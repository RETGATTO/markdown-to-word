# Markdown → Word — GitHub Pages (versione con immagini)

Questa versione della mini web app converte un file Markdown `.md` in un file Word `.docx` ed è in grado di incorporare nel Word le immagini referenziate nel Markdown.

## Novità principali

- supporto immagini locali referenziate nel Markdown, per esempio:
  - `![Logo](images/logo.png)`
  - `![Schema](../img/schema.jpg)`
- supporto immagini remote via URL HTTP/HTTPS, se il sito sorgente consente il download dal browser
- mantenimento del comportamento "solo file `.md`" per documenti senza immagini locali

## Punto importante: come funzionano le immagini locali

Una pagina web pubblicata su GitHub Pages **non può leggere automaticamente i file locali del computer** indicati nel Markdown, a meno che l'utente non dia accesso a quei file.

Per questo motivo la pagina offre due modalità:

### Modalità 1 — Seleziona file `.md`
Usala se:
- il documento non contiene immagini locali
- oppure usa immagini remote via URL

### Modalità 2 — Seleziona cartella
Usala se il Markdown contiene immagini locali.

L'utente deve selezionare **la cartella che contiene il file `.md` e le immagini**. In questo modo la pagina può leggere i file immagine e incorporarli nel Word.

## Esempio di struttura consigliata

```text
manuale-progetto/
├── manuale.md
└── images/
    ├── copertina.png
    └── schema.jpg
```

Nel file `manuale.md`:

```md
# Manuale

![Copertina](images/copertina.png)

Testo del manuale.
```

Procedura utente:
1. aprire la pagina
2. cliccare **Seleziona cartella**
3. scegliere `manuale-progetto`
4. se richiesto, scegliere `manuale.md`
5. cliccare **Converti in Word**

## Formati immagine supportati

La pagina prova a incorporare:
- PNG
- JPG / JPEG
- GIF
- BMP
- WEBP

Per ottenere la massima compatibilità con Word, è consigliabile usare soprattutto:
- PNG
- JPG / JPEG

## Casi in cui l'immagine può non essere incorporata

Il documento Word viene comunque creato, ma la pagina mostrerà un avviso se:
- il percorso immagine nel Markdown è sbagliato
- il file immagine non è presente nella cartella selezionata
- il formato immagine non è supportato
- l'immagine è remota ma il sito sorgente non consente il download dal browser
- il browser non riesce a leggere correttamente il file immagine

## Pubblicazione con GitHub Pages

### 1. Crea un repository

Su GitHub crea un repository, per esempio:

`markdown-to-word`

Se vuoi che il convertitore sia apribile da tutti tramite link, usa un repository pubblico.

### 2. Carica i file

Carica nella root del repository almeno:
- `index.html`
- `.nojekyll`

Puoi caricare anche questo `README.md` e i file di esempio.

### 3. Attiva GitHub Pages

Nel repository:
1. apri **Settings**
2. apri **Pages**
3. in **Build and deployment**, scegli **Deploy from a branch**
4. seleziona branch `main`
5. seleziona cartella `/(root)`
6. premi **Save**

Dopo qualche minuto l'indirizzo del sito sarà normalmente simile a:

`https://NOMEUTENTE.github.io/markdown-to-word/`

## Test rapido

Nel pacchetto trovi una piccola cartella di esempio con immagini locali. Provala prima di distribuire il link ai colleghi.

## Privacy

La conversione viene eseguita nel browser dell'utente. Il repository GitHub Pages ospita soltanto la pagina HTML/JavaScript del convertitore.

Nota: la pagina carica librerie JavaScript da jsDelivr, quindi serve connettività Internet.
