# Resoconto dell'uso dell'AI — Segnale Festival

## Sessione 1
* **Cosa è stato chiesto all'AI:** 
  * Supporto per strutturare i file JSON (`sedi.json` e `eventi.json`) e creazione del file di descrizione dei dati con schema relazionale in Mermaid (`dati/SCHEMA.md`).
  * Scrittura del codice JavaScript asincrono con `fetch` per `programma.html`, integrando la gestione degli stati di caricamento, array vuoto, errori di lettura e fallback per sedi inesistenti («Sede da definire»).
  * Implementazione del widget meteo in `info.html` tramite l'API pubblica di Open-Meteo, con attribuzione della licenza CC BY 4.0 e gestione degli errori locali.
  * Personalizzazione grafica del carosello di `info.html` (rimozione delle frecce di default, ingrandimento delle immagini a piena larghezza, aggiunta di pulsanti personalizzati «Precedente» e «Successivo» rossi allineati ai lati con i pallini di paginazione ridotti e colorati in mezzo) e ottimizzazione della responsività dell'header nel CSS.

* **Cosa è stato utilizzato, modificato o scartato:** 
  * Sono stati integrati integralmente i file JSON proposti e la logica di fetching asincrono per il programma e per il meteo.
  * È stato adottato lo schema di navigazione personalizzato per i luoghi del festival, allineando i pulsanti e la paginazione secondo le preferenze di design.
  * Non è stato scartato nulla di rilevante, in quanto le soluzioni proposte rispettavano rigorosamente i vincoli tecnici e stilistici della consegna.

* **Come è stato verificato:** 
  * Il codice è stato testato in locale tramite **Live Preview** su VS Code.
  * Sono state eseguite tutte le prove di verifica richieste: modifica del nome di una sede, svuotamento dell'array eventi (`[]`), simulazione di errore sui file di dati e sui parametri dell'API meteo, e test di visualizzazione su differenti dimensioni di schermo.

* **Quali problemi ci sono stati e come sono stati risolti:** 
  * *Problema:* Gestire correttamente la visualizzazione degli eventi con `sede_id` non valido senza bloccare la generazione delle altre schede.
  * *Soluzione:* L'utilizzo di un operatore di fallback (`|| 'Sede da definire'`) all'interno del ciclo di generazione delle card ha risolto il problema in modo pulito ed efficiente.
  * *Problema:* Allineare correttamente i nuovi pulsanti e i pallini di paginazione sotto le immagini dei luoghi in `info.html`.
  * *Soluzione:* L'utilizzo di un contenitore flessibile (`display: flex` con `justify-content: space-between` e `align-items: center`) ha permesso di posizionare i pulsanti ai lati e i pallini ridotti esattamente al centro.