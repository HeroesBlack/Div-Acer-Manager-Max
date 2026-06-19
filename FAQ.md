# ❓ Domande Frequenti (FAQ)

### 🔧 L'installazione dei driver fallisce

Ci sono diverse cause comuni per problemi di installazione dei driver:

1. **Versione del kernel incompatibile**
   I driver Linuwu Sense richiedono **Linux kernel 6.13 o successivo**. Se stai usando un kernel più vecchio, l'installazione fallirà. Aggiorna il kernel prima di procedere.

2. **Secure Boot abilitato**
   Secure Boot impedisce il caricamento di moduli kernel non firmati. Questo può causare errori come:

   ```
   modprobe: ERROR: could not insert 'linuwu_sense': Key was rejected by service
   make: Error 1
   ```

   **Soluzione**: Disabilita Secure Boot nelle impostazioni BIOS/UEFI e riprova l'installazione.

3. **Il percorso di installazione contiene spazi**
   Se la directory di installazione contiene spazi (es. `DAMX-0.8.8 (1)/setup.sh`), lo script potrebbe fallire.
   **Soluzione**: Sposta o rinomina la directory in modo che **non ci siano spazi nel percorso**.

---

### 🧩 La GUI è vuota o mostra "Unknown Model" (anche se il tuo modello è supportato)

Di solito è causato da problemi di rilevamento del modello:

* **Problemi firmware Acer**: Alcuni dispositivi Acer si comportano in modo inconsistente durante il rilevamento hardware.
  **Prova a riavviare il laptop** o **reinstallare i driver**.

* **Problemi di compatibilità con la distribuzione**:
  Il progetto DAMX è ufficialmente testato e supportato solo su **Ubuntu**. Altre distribuzioni Linux potrebbero introdurre incompatibilità di kernel o librerie, causando funzionalità mancanti nella GUI.

---

### 🛑 Mostra "Unknown Model" e il mio modello non è nella lista compatibilità

Nessun problema! Il tuo dispositivo potrebbe essere comunque supportato in modo non ufficiale.

**Passaggi da provare:**

1. Apri la **Gestione Avanzata** nella GUI.
2. Avvia i driver con uno dei seguenti parametri:

   * `nitro_v4` o `predator_v4`
   * Opzionale: Aggiungi `enable_all` per sbloccare tutte le funzionalità (controllo RGB, LCD override, ecc.)
3. Se funziona, puoi **rendere il parametro permanente** usando la Gestione Avanzata.

Vuoi il supporto nativo?

* Vai al progetto Div-Linuwu Sense e **invia la configurazione quirk del tuo dispositivo nel driver stesso** per aiutare gli altri nella community.

---

### 🛠️ Voglio aggiungere il supporto per il mio modello — Come?

Hai due opzioni:

1. **Fork e modifica il progetto originale**

   * Clona il repository originale [linuwu-sense](#)
   * Aggiungi i quirk/configurazione specifici del tuo modello
   * Compila e testa

1. **Usa il fork Div-Linuwu Sense (consigliato)**

   * È un fork più stabile e community-friendly, pensato per l'**integrazione con DAMX**
   * Invia la tua configurazione tramite pull request
   * Attivo e aggiornato regolarmente, a differenza del progetto upstream

- Lo sviluppatore originale sembra essere occupato e ha pochissimo tempo per revisionare o aggiornare il codice, figuriamoci accettare pull request. Per questo ho forkato il progetto per assicurare che aggiornamenti e pull request vengano gestiti velocemente.

---

### 🛠️ Come scrivo la configurazione quirk nel driver per ottenere il supporto nativo?
Ecco un processo user-friendly per aggiungere il supporto per un nuovo modello di laptop Acer al driver `linuwu_sense.c`:

### Guida passo-passo per aggiungere un nuovo quirk modello

1. **Identifica il modello del tuo laptop**
   - Esegui `sudo dmidecode -s system-product-name` nel terminale per ottenere il nome esatto del modello
   - Annota eventuali funzionalità speciali del tuo modello (tastiera RGB, sistema di raffreddamento speciale, ecc.)

2. **Controlla i quirk esistenti**
   - Cerca le voci quirk esistenti nel file (cerca `quirk_acer_` per trovarle)
   - Trova quella che corrisponde meglio alle capacità del tuo laptop

3. **Crea la tua voce quirk**
   - Aggiungi una nuova voce nella sezione quirk seguendo questo formato:
     ```c
     static struct quirk_entry quirk_acer_TUO_MODELLO = {
        .predator_v4 = 1,             // Se usa Predator Sense v4
        .nitro_v4 = 1,                // Se usa Nitro Sense v4
        .nitro_sense = 1,             // Se non supporta LCD Override e Boot Animation Sound usa nitro_sense
        .four_zone_kb = 1             // Se ha tastiera RGB a 4 zone
     
        //quirk speciali (aggiungi solo se sai cosa stai facendo e il tuo hardware li supporta)
        .wireless = 1,                // Se ha gestione wireless speciale
        .brightness = -1,              // Se ha controllo luminosità
        .turbo = 1,                   // Se ha modalità turbo (la modalità turbo viene rilevata automaticamente dal driver, non serve abilitarla esplicitamente, è necessaria solo in scenari e modelli specifici)
        .cpu_fans = 1,                // Numero di ventole CPU
        .gpu_fans = 1,                // Numero di ventole GPU
     };
     ```

4. **Aggiungi la voce DMI Match**
   - Aggiungi il tuo modello all'array `acer_quirks`:
     ```c
     {
         .callback = dmi_matched,
         .ident = "Acer Nome Tuo Modello",
         .matches = {
             DMI_MATCH(DMI_SYS_VENDOR, "Acer"),
             DMI_MATCH(DMI_PRODUCT_NAME, "NOME ESATTO MODELLO"),
         },
         .driver_data = &quirk_acer_TUO_MODELLO,
     },
     ```

5. **Testa le modifiche**
   - Salva il driver e le modifiche nella directory Linuwu Sense di DAMX

   - Reinstalla DAMX (reinstallerà automaticamente il driver):

   - Controlla dmesg per errori:
     ```bash
     dmesg
     ```
   - Controlla DAMX per tutte le funzionalità desiderate:
     

6. **Invia le modifiche**
   - Forka il repository GitHub
   - Crea un branch per le tue modifiche
   - Committa le modifiche con un messaggio descrittivo
   - Crea una pull request verso il repository originale

### Esempio per un nuovo modello

*Se il tuo modello non richiede molta configurazione e non ha funzionalità speciali come la tastiera RGB a quattro zone puoi semplicemente aggiungere:*
```c
/* Aggiungi all'array acer_quirks (circa riga 570): */

   {
         .callback = dmi_matched,
         .ident = "Acer Nitro ANV15-51",
         .matches = {
             DMI_MATCH(DMI_SYS_VENDOR, "Acer"),
             DMI_MATCH(DMI_PRODUCT_NAME, "Nitro ANV15-51"),
         },
            .driver_data = &quirk_acer_nitro, //Questa riga indica quale lista quirk (struct) usare, dato che vogliamo il quirk nitro_sense predefinito, si inizializzerà con la configurazione default
     },
```
Questo abiliterà semplicemente il quirk base con i default di nitro_sense

Ecco le struct predefinite:
- Per predator_v4 usa `.driver_data =  &quirk_acer_predator_v4` // Abilita il Predator_v4 base, usare nei modelli predator. <br>
- Per nitro_v4 usa `.driver_data =  &quirk_acer_nitro_v4` // Abilita il Nitro_v4 base, usare nei modelli nitro. <br>
- Per nitro_sense usa `.driver_data = &quirk_acer_nitro` // Usato nei modelli nitro senza funzionalità speciali come LCD override e boot sound (come ANV15-51). <br>


*Per un "Acer Predator AN515-58" con tutte le funzionalità:*

```c
 static struct quirk_entry quirk_acer_nitro_an515_58 = {
    .nitro_v4 = 1,
    .four_zone_kb = 1,
 };

/* Poi aggiungi all'array acer_quirks: */
   {
        .callback = dmi_matched,
        .ident = "Acer Nitro AN515-58",
        .matches = {
            DMI_MATCH(DMI_SYS_VENDOR, "Acer"),
            DMI_MATCH(DMI_PRODUCT_NAME, "Nitro AN515-58"),
        },
        .driver_data = &quirk_acer_nitro_an515_58,
    },
```

*Per un "Acer Predator PHN16-73" con tutte le funzionalità speciali:*

```c
static struct quirk_entry quirk_acer_predator_phn16_73 = {
    .turbo = 1,
    .cpu_fans = 1,
    .gpu_fans = 1,
    .predator_v4 = 1,
    .four_zone_kb = 1
};

/* Poi aggiungi all'array acer_quirks: */
{
    .callback = dmi_matched,
    .ident = "Acer Predator PHN16-73",
    .matches = {
        DMI_MATCH(DMI_SYS_VENDOR, "Acer"),
        DMI_MATCH(DMI_PRODUCT_NAME, "Predator PHN16-73"),
    },
    .driver_data = &quirk_acer_predator_phn16_73,
},
```

### Suggerimenti per la risoluzione problemi

1. Se le funzionalità non funzionano:
   - Prova ad abilitare il parametro `enable_all=1` quando carichi il modulo per testare tutte le capacità
   - Controlla i log del kernel con `dmesg` per indizi

2. Se il tuo modello non viene rilevato:
   - Ricontrolla il nome esatto del prodotto nel DMI
   - Prova con wildcard se il nome varia leggermente tra le regioni

3. Per problemi con la tastiera RGB:
   - Assicurati che `four_zone_kb = 1` sia impostato
   - Verifica se la tua tastiera risponde ai controlli RGB esistenti

Ricorda di fare sempre un backup del kernel/driver funzionante prima di apportare modifiche!

---

Hai altre domande o hai bisogno di aiuto?
👉 Apri un [issue](#issues) o unisciti alle discussioni.
