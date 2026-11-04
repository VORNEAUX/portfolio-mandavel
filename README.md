# MANDAVEL Portfolio — sito indipendente

Sito statico autonomo (nessuna build, nessun server): `index.html` + cartella `progetti/` con i 7 concept dimostrativi originali, copiati senza modifiche.
Il portfolio è un percorso 3D (CSS 3D + canvas, nessuna libreria): si naviga con scroll, trascinamento, frecce o dall'indice (tasto I). Non contiene alcun collegamento al sito principale MANDAVEL.

## Pubblicazione (GitHub Pages)
1. Crea un repository dedicato, es. `mandavel-portfolio`.
2. Carica il contenuto di questa cartella nella radice del repository.
3. Settings → Pages → Branch `main` / cartella `/ (root)`.

## Note tecniche
- I concept 01 e 07 caricano Three.js da cdnjs; tutti tranne 03 caricano Google Fonts: serve connessione a internet.
- I concept 03, 04 e 07 salvano dati dimostrativi nel localStorage del browser (chiavi proprie, separate dal portfolio).
- Ogni concept si apre nel visualizzatore del portfolio, a schermo intero in una nuova scheda, oppure si passa ai pacchetti dal pulsante «Scopri i pacchetti».
- Per aggiungere un concept: copia il file in `progetti/` e aggiungi un oggetto all'array `P` in `index.html`.

## Logo e tema
- Logo ufficiali in `assets/` (derivati dai file forniti: sfondo reso trasparente e margini ritagliati); `favicon.png` è ricavata dal simbolo del logo.
- Tema chiaro/scuro dal pulsante in alto a destra: la scelta viene ricordata nel browser. La transizione 3D usa le View Transitions (Chrome/Edge/Safari recenti); altrove il cambio è immediato.

## Modifiche ai concept originali
I concept in `progetti/` sono invariati, tranne una regola CSS aggiunta in coda a `03-tassello.html` (controlli di rotazione del modello): evita un artefatto grafico di composizione (un quadrato) riscontrato nel visualizzatore.

## Pagina Pacchetti
`pacchetti.html` presenta i sei pacchetti come una piccola esposizione (una «sala» per pacchetto). Per collegare le richieste a un recapito reale imposta `CONTATTO.email` e/o `CONTATTO.url` in cima allo script di `pacchetti.html`: finché sono vuoti, il modulo di richiesta permette di copiare il riepilogo negli appunti (nessun link morto, nessun invio simulato).
