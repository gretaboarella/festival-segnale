# Schema dei dati — Segnale Festival

## 1. Entità
Il sistema si basa su due entità principali: **Evento** e **Sede**.

## 2. Campi di ciascuna entità

### Evento (`eventi.json`)
* `id`: Numero intero (es. `1`) — Chiave primaria.
* `titolo`: Stringa (es. `"Lettere in movimento"`).
* `tipo`: Stringa, categoria dell'appuntamento (es. `"Incontro"`, `"Laboratorio"`, `"Mostra"`).
* `data`: Stringa, giorno di svolgimento (es. `"Venerdì 12 giugno"`).
* `ora`: Stringa, orario di inizio (es. `"10:00"`).
* `descrizione`: Stringa, testo descrittivo dell'attività.
* `immagine`: Stringa, percorso del file grafico (es. `"assets/lettere-in-movimento.svg"`).
* `alt_immagine`: Stringa, descrizione testuale alternativa dell'immagine.
* `sede_id`: Stringa, identificativo della sede ospitante (es. `"sede-1"`).

### Sede (`sedi.json`)
* `id`: Stringa o numero (es. `"sede-1"`) — Chiave primaria.
* `nome`: Stringa, nome ufficiale della sede (es. `"Officina Nord"`).
* `indirizzo`: Stringa, via e numero civico (es. `"Corso Duca degli Abruzzi 24"`).

## 3. Chiave primaria
* **Evento**: Il campo `id` è numerico, univoco all'interno dell'entità e stabile.
* **Sede**: Il campo `id` è univoco, stabile e funge da identificativo testuale.

## 4. Relazione
La relazione tra le due entità è di **uno a molti (1:N)**:
* Una sede può ospitare più eventi.
* Ogni evento si svolge in una sola sede.
* Il campo `Evento.sede_id` fa riferimento a `Sede.id` creando il collegamento logico.

## 5. Quantità
* **Eventi**: 6 record.
* **Sedi**: 3 record.

## 6. Aggiornamento dei dati
I dati vengono aggiornati modificando direttamente i file JSON all'interno della cartella `dati/` nella repository del progetto e pubblicando le modifiche tramite GitHub Pages. Non è richiesto l'uso di database dinamici o pannelli di controllo.

## 7. Cosa mostra la pagina
La pagina `programma.html` legge in modo dinamico i file JSON tramite `fetch` e genera le schede degli eventi a schermo, inserendo per ciascun evento le informazioni di dettaglio, l'immagine e il nome della sede associata recuperato da `sedi.json`.

---

## Schema Entità-Relazione (Mermaid)

```mermaid
erDiagram
    SEDE {
        string id PK
        string nome
        string indirizzo
    }
    EVENTO {
        int id PK
        string titolo
        string tipo
        string data
        string ora
        string descrizione
        string immagine
        string alt_immagine
        string sede_id FK
    }
    SEDE ||--o{ EVENTO : "ospita"