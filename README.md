<p align="center">
  <img src="https://github.com/user-attachments/assets/6d383e82-8221-438b-9d6d-a19e998fcc59" alt="icon" width="80" style="vertical-align: middle;">
</p>

<h1 align="center">
  Div Acer Manager Max
</h1>

**Div Acer Manager Max** è un'utility Linux ricca di funzionalità per laptop Acer, basata sugli incredibili driver [Linuwu Sense](https://github.com/0x7375646F/Linuwu-Sense). Replica e amplia le funzionalità di NitroSense e PredatorSense di Acer su Linux con controllo completo delle ventole, modalità prestazioni, ottimizzazione batteria, impostazioni retroilluminazione e altro — il tutto in una moderna interfaccia basata su Avalonia.

> [!CAUTION]
> Il progetto è in sviluppo passivo.

![Title Image](https://github.com/user-attachments/assets/a60898a6-a2b8-432e-b5a2-8d0a45c63484)

<h4 align="center">
⭐ Metti una stella a questa repository per mostrare supporto. Mi motiva a migliorare il progetto per tutti
</h4>  

## ✨ Funzionalità

### ✅ Completamente implementate

* 🔋 **Profili prestazioni / termici**
  Eco, Silenzioso, Bilanciato, Prestazioni, Turbo — regolati automaticamente in base allo stato alimentazione/batteria
  (es. Turbo nascosto quando su batteria o non supportato)

* 🌡 **Controllo ventole**
  Modalità velocità manuale e automatica
  Manuale disabilitata automaticamente nel profilo Silenzioso

* 💡 **Override LCD**
  Controllo diretto del comportamento energetico LCD

* 🎨 **Timeout retroilluminazione tastiera**
  Personalizza il timeout della retroilluminazione tastiera

* 🔊 **Animazione e suono di avvio**
  Abilita/disabilita le animazioni e i suoni di avvio Acer

* 💻 **Informazioni sistema in tempo reale**
  Mostra profilo prestazioni, impostazioni ventole, stato calibrazione e altro in tempo reale

* 🧠 **Daemon intelligente (basso consumo risorse)**

  * Rileva automaticamente le funzionalità supportate per dispositivo
  * Comunica con la GUI in tempo reale
  * Leggero: usa ~10MB di RAM
  * Può funzionare **indipendentemente** dalla GUI
  * Riavvio ricorsivo per risolvere problemi software simili a quelli su Windows

* 🖥️ **GUI moderna**

  * Basata su Avalonia, pulita e reattiva
  * Monitoraggio in tempo reale con Dashboard e letture temperature accurate
  * L'interfaccia nasconde dinamicamente le funzionalità non supportate
  * Feedback in tempo reale dal daemon

## 🧭 Compatibilità

Controlla la compatibilità del tuo dispositivo qui: [Lista compatibilità](Compatibility.md)

> Anche se non presente nella lista, DAMX funzionerà sulla maggior parte dei dispositivi. Apri un issue sulla pagina di Linuwu-Sense (qui verrà ignorato)

## 🖥️ Guida all'installazione di DAMX

Puoi installare DAMX usando uno dei seguenti metodi:

### 🔗 Installazione remota

1. Apri una finestra del terminale.

2. Esegui il seguente comando:

   ```bash
   curl -fsSL https://raw.githubusercontent.com/PXDiv/Div-Acer-Manager-Max/refs/heads/main/scripts/remoteSetup.sh -o /tmp/setup.sh && sudo bash /tmp/setup.sh
   ```

3. Segui le istruzioni a schermo.

4. Fatto!

### 📦 Installazione locale (metodo alternativo)

Se l'installazione remota fallisce o sei offline, segui questi passaggi:

1. Scarica l'ultima release dalla sezione **Releases**.

2. Estrai il pacchetto scaricato.

3. Rendi eseguibile lo script `setup.sh`:

   ```bash
   chmod +x setup.sh
   ```

4. Esegui lo script:

   * Fai clic destro sul file setup e scegli **"Esegui nel terminale"**,
     oppure apri un terminale nella cartella ed esegui:

     ```bash
     ./setup.sh
     ```

5. Quando richiesto, scegli un'opzione dal menu:

   * `1` → Installa
   * `2` → Installa senza driver
   * `3` → Disinstalla
   * `4` → Reinstalla/Aggiorna

6. Riavvia il sistema dopo il completamento dell'installazione.

✅ Tutto qui — sei pronto!

## 🖥️ Risoluzione problemi

Puoi controllare i log in /var/log/DAMX_Daemon_Log.log

Se ottieni UNKNOWN come tipo di laptop, prova a riavviare (succede a volte).
Se continua a succedere, potrebbe significare che l'installazione dei driver è fallita. Assicurati di avere gli header del kernel appropriati per compilare i driver.

Consulta anche la [pagina FAQ](FAQ.md) prima di aprire qualsiasi issue.

Apri una nuova issue o discussione e includi i log per ottenere supporto e aiutare il progetto a crescere se hai bisogno di informazioni, vuoi segnalare un bug o semplicemente dare idee per le versioni future di DAMX.

## Screenshot

![image](https://github.com/user-attachments/assets/10d44e8c-14e4-4441-b60c-538af1840cf6)
![image](https://github.com/user-attachments/assets/89217b26-b94c-4c78-8fe8-3de2b22a7095)
![image](https://github.com/user-attachments/assets/72a7b944-5efc-4520-83b6-88069fc05723)
![image](https://github.com/user-attachments/assets/f9a9d663-70c6-482e-a0c4-15a4ea08a8d2)

## ❤️ Powered by Linuwu

I driver personalizzati per questo progetto [Div-Linuwu Sense](https://github.com/PXDiv/Div-Linuwu-Sense) sono costruiti interamente sopra i driver [Linuwu Sense](https://github.com/0x7375646F/Linuwu-Sense) — un enorme ringraziamento ai loro sviluppatori per aver reso possibile l'accesso hardware sui laptop Acer.

## 🤝 Contribuire

* Segnala bug o richiedi funzionalità tramite GitHub Issues
* Invia pull request per migliorare il codice o l'interfaccia
* Aiuta a testare su diversi modelli di laptop Acer

## 📄 Licenza

Questo progetto è rilasciato sotto la **GNU General Public License v3.0**.  
Vedi il file [LICENSE](LICENSE) per i dettagli.
