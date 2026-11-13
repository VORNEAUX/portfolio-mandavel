# MANDAVEL Portfolio — sito indipendente

Sito statico autonomo (nessuna build, nessun server): `index.html` + cartella `progetti/` con 6 concept dimostrativi originali (01, 03–07), copiati senza modifiche, e il progetto reale 02 (ELDOVANT Official Website).
Il portfolio è un percorso 3D (CSS 3D + canvas, nessuna libreria): si naviga con scroll, trascinamento, frecce o dall'indice (tasto I). Non contiene alcun collegamento al sito principale MANDAVEL.

## Pubblicazione (GitHub Pages)
1. Crea un repository dedicato, es. `mandavel-portfolio`.
2. Carica il contenuto di questa cartella nella radice del repository.
3. Settings → Pages → Branch `main` / cartella `/ (root)`.

## Note tecniche
- I concept 01 e 07 caricano Three.js da cdnjs; il progetto 02 carica solo Google Fonts e usa immagini locali (`assets/eldovant/`); tutti tranne 03 caricano Google Fonts: serve connessione a internet.
- I concept 03, 04 e 07 salvano dati dimostrativi nel localStorage del browser (chiavi proprie, separate dal portfolio).
- Ogni concept si apre nel visualizzatore del portfolio, a schermo intero in una nuova scheda, oppure si passa ai pacchetti dal pulsante «Scopri i pacchetti».
- Per aggiungere un concept: copia il file in `progetti/` e aggiungi un oggetto all'array `P` in `index.html`. Campi facoltativi usati dal progetto 02: `real` (etichetta «Progetto reale» nel visualizzatore), `cta` (testo del pulsante), `ext` (link esterno nella scheda e nel pannello), `cred` (riga «Crediti»).

## Logo e tema
- Logo ufficiali in `assets/` (derivati dai file forniti: sfondo reso trasparente e margini ritagliati); `favicon.png` è ricavata dal simbolo del logo.
- Favicon: `favicon.ico` nella radice (16, 32, 48, 64, 128, 256 px, emblema «M» ricavato dal logo su sfondo scuro, margine minimo, nessuna deformazione) richiamata da `index.html` e `pacchetti.html` con PNG di supporto e `apple-touch-icon` in `assets/`. `assets/favicon.png` resta usata come immagine nella sala 06 di `pacchetti.html`. Dopo una modifica incrementa il parametro `?v=` nei tag `link` per aggirare la cache dei browser.
- Tema chiaro/scuro dal pulsante in alto a destra: la scelta viene ricordata nel browser. La transizione 3D usa le View Transitions (Chrome/Edge/Safari recenti); altrove il cambio è immediato.

## Modifiche ai concept originali
I concept in `progetti/` (esclusi il 02) sono invariati, tranne una regola CSS aggiunta in coda a `03-tassello.html` (controlli di rotazione del modello): evita un artefatto grafico di composizione (un quadrato) riscontrato nel visualizzatore.

## Pagina Pacchetti
`pacchetti.html` presenta i sette pacchetti come una piccola esposizione (una «sala» per pacchetto). Per collegare le richieste a un recapito reale imposta `CONTATTO.email` e/o `CONTATTO.url` in cima allo script di `pacchetti.html`: finché sono vuoti, il modulo di richiesta permette di copiare il riepilogo negli appunti (nessun link morto, nessun invio simulato).

## Indirizzo ufficiale ed email
- Indirizzo del portfolio: **https://gallery.mandavel.it** (file `CNAME` incluso). GitHub Pages → Settings → Pages → Custom domain: `gallery.mandavel.it`, poi «Enforce HTTPS». Nel DNS di `mandavel.it` crea un record **CNAME**: nome `gallery`, valore `vorneaux.github.io`.
- Email: `hello@mandavel.it` (domande generali), `projects@mandavel.it` (richieste commerciali: è il destinatario del pulsante «Richiedi informazioni»), `clients@mandavel.it` (clienti con un incarico).

## P2 — ELDOVANT Official Website
- Il precedente P2 (Calce Studio, concept dimostrativo) è stato sostituito da `progetti/02-eldovant-website.html`: caso studio del sito ufficiale https://www.eldovant.com, progettato e realizzato da MANDAVEL per ELDOVANT.
- Il sito **non è incorporato in iframe**: la pagina mostra schermate desktop e mobile (`assets/eldovant/*.jpg`) e rimanda a eldovant.com in una nuova scheda. Le schermate sono state generate dal pacchetto sorgente del sito (non dal dominio live, non raggiungibile dall'ambiente di lavoro) a 1440×900 (desktop) e 390×844 @2x (mobile): se il sito cambia, vanno rigenerate.
- Palette, caratteri e funzioni descritti nella pagina provengono dal codice del sito. Titoli, date e stati dei film sono quelli del sito al momento delle schermate.
- Il visualizzatore ha il flag `allow-popups-to-escape-sandbox` così il link a eldovant.com si apre fuori dalla sandbox dell'iframe.
- Frasi del portfolio aggiornate per distinguere i sei concept con dati fittizi dal progetto reale: introduzione (pannello 00), nota in basso a sinistra, sottotitolo del visualizzatore (dinamico), meta description. In `pacchetti.html` il link «Sito aziendale» ora si chiama «Sito web ufficiale · ELDOVANT» («Guarda un progetto reale»).
