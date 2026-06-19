# Lista Compatibilità DAMX:
Se il tuo dispositivo non è presente nella tabella — niente paura! Puoi comunque scaricare e provare DAMX. Se il tuo laptop è compatibile, potrebbe funzionare direttamente. In caso contrario, puoi aggiungere il supporto creando una configurazione personalizzata per il tuo sistema.

DAMX è progettato principalmente per laptop Acer moderni (2022 e successivi) che utilizzano protocolli WMI.

✅ Distribuzioni testate ufficialmente: Ubuntu 25+ e Kubuntu 25+
✅ Versione minima del kernel: Linux 6.13+

> Nota: questa lista riflette semplicemente i dispositivi su cui DAMX è stato confermato funzionante.
>
> Se il tuo laptop Acer non è elencato ma funziona correttamente o parzialmente con DAMX, aiuta a migliorare il progetto aprendo un issue con i dettagli del tuo modello — così anche gli altri potranno beneficiarne.
>

Consulta anche la [pagina FAQ](FAQ.md) per sapere come far funzionare il tuo modello anche se non supportato, e puoi aiutare gli altri creando una configurazione quirk per il tuo modello e inviando una merge request.




| Modello             | Stato                  | Note                                                             |
| ------------------- | ---------------------- | ---------------------------------------------------------------- |
| **ANV15-51**        | ✅ Pienamente supportato | **Testato e verificato ufficialmente.**                          |
| ANV15-41            | ✅ Supportato           | Stabile con tutte le funzionalità.                               |
| AN16-41             | ✅ Supportato           | Pienamente funzionante su kernel supportati.                     |
| AN16-43             | ✅ Supportato           | Pienamente funzionante su kernel supportati.                     |
| **PHN16-71**        | ✅ Supportato           | L'illuminazione per-tasto potrebbe non funzionare correttamente. |
| PHN16-72            | ✅ Supportato           | Usa lo stesso profilo quirk del PHN16-71 senza problemi noti.    |
| PH16-71             | ✅ Supportato           | Usa quirk universale Predator V4.                                |
| PH18-71             | ✅ Supportato           | Usa quirk universale Predator V4.                                |
| PH315-53            | ✅ Supportato           | Stabile, usa quirk dedicato.                                     |
| AN515-44            | ✅ Supportato <br> (Vedi note) | Necessario forzare parametri <br> tramite Gestione Avanzata (`nitro_v4`) |
| AN515-47            | ✅ Supportato <br> (Vedi note) | Necessario forzare parametri <br> tramite Gestione Avanzata (`nitro_v4`) |
| AN515-58            | ✅ Supportato <br> (Vedi note) | Supporto integrato, <br> per LCD Override usare parametro `nitro_v4` |
| AN517-54            | ✅ Supportato <br> (Vedi note) | Necessario forzare parametri <br> tramite Gestione Avanzata (`nitro_v4`) |
| AN517-55            | ⚪ Non ancora verificato | Nessuna segnalazione — supporto hardware non confermato.         |
| Aspire 1360         | ✅ Supportato           | Modello legacy — usa quirk Aspire 1520.                          |
| Aspire 1520         | ✅ Supportato           | Modello legacy — usa quirk Aspire 1520.                          |
| Aspire 3100         | ✅ Supportato           | Usa quirk TravelMate 2490.                                       |
| Aspire 3610         | ✅ Supportato           | Usa quirk TravelMate 2490.                                       |
| Aspire 5100         | ✅ Supportato           | Usa quirk TravelMate 2490.                                       |
| Aspire 5610         | ✅ Supportato           | Usa quirk TravelMate 2490.                                       |
| Aspire 5630         | ✅ Supportato           | Usa quirk TravelMate 2490.                                       |
| Aspire 5650         | ✅ Supportato           | Usa quirk TravelMate 2490.                                       |
| Aspire 5680         | ✅ Supportato           | Usa quirk TravelMate 2490.                                       |
| Aspire 9110         | ✅ Supportato           | Usa quirk TravelMate 2490.                                       |
| TravelMate 2490     | ✅ Supportato           | Supporto nativo.                                                 |
| TravelMate 4200     | ✅ Supportato           | Usa quirk TravelMate 2490.                                       |
| Switch 10 E SW3-016 | ✅ Supportato           | Supporto dock tastiera tramite force caps.                       |
| Switch 10 SW5-012   | ✅ Supportato           | Supporto dock tastiera tramite force caps.                       |
| Switch V 10 SW5-017 | ✅ Supportato           | Supporto dock tastiera tramite force caps.                       |
| One 10 (S1003)      | ✅ Supportato           | Supporto dock tastiera tramite force caps.                       |
