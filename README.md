# TFState Explorer (Single-Page, HTML+JS)

Uno strumento **client-side** per esplorare, cercare, fare diff e generare comandi/bLocchi Terraform a partire da uno o due file `.tfstate`.

## Funzionalità
- **Caricamento** di uno state corrente (`.tfstate`) e opzionale **state base** per il diff.
- Vista **albero** per moduli ➜ risorse ➜ istanze.
- Vista **tabellare** filtrabile per **Modulo / Tipo / Provider** + ricerca full-text (opzionale negli attributi).
- **Diff** evidenziato: `added`, `removed`, `changed`, `same` (anche filtro per tipo di diff).
- **Selezione** righe dall’albero o dalla tabella (sincronizzate).
- **Preview rinomine** (from→to) con avvisi (target esistente / duplicati / fuori prefisso).
- Generazione:
    - `terraform state mv` (CLI)
    - blocchi `moved {}` (HCL)
    - **`terraform import` (CLI)**
    - **blocchi `import {}` (HCL)**  
      con autodetect dell’ID (`id`, `ocid`, `resource_id`, oppure prima stringa che somiglia a `ocid1.*`) o campo ID personalizzato.
- **Export CSV** delle righe filtrate.
- **Copy/Download** dei comandi/blocchi generati.
- **Drag & Drop** del `.tfstate`.

> Tutto gira **localmente nel browser**: nessun upload, nessun backend.

---

## Avvio veloce

### Opzione A) Apri il file direttamente
1. Salva il file `index.html` in una cartella.
2. Aprilo con Chrome/Edge/Firefox.
   > Nota: alcuni browser limitano le API file su `file://`. Se vedi comportamenti strani, usa l’Opzione B.

### Opzione B) Mini server statico (consigliata)
Servi la cartella con un server locale:

- Con Python:
  ```bash
  python -m http.server 5173