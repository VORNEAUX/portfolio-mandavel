# Note sull'ottimizzazione (Portfolio + Pacchetti)

## Bug risolti
- **Flash bianchi (Portfolio)**: scaricando un'anteprima (`src="about:blank"`) l'evento `load` riaccendeva l'iframe bianco. Ora ogni anteprima ha un token di caricamento, resta invisibile finché il contenuto non è dipinto (font + 2 frame) e non viene mai riattivata dopo lo scarico. Stesso trattamento per il viewer a schermo intero.
- **Testi che sparivano/tagliati**: causa = tile di raster mancanti. Il pavimento 3D era un elemento CSS da 5000×16000 px (~80 Mpx) che saturava la memoria GPU su mobile. Ora è disegnato su un canvas grande quanto lo schermo, con la stessa geometria, ridisegnato solo quando la camera si muove.
- **Pulsanti non cliccabili (Portfolio e Pacchetti)**: i contenitori 3D (`#ring`, `#tilt`, …) intercettavano i tocchi davanti ai pulsanti. Ora solo i pulsanti e gli schermi ricevono i tocchi; il trascinamento continua a funzionare ovunque.
- **Sovrapposizioni in Pacchetti**: layout mobile a colonna dentro ogni muro (illustrazione flessibile + testo), con fattore di scala automatico (mai sotto 0,72) per telefoni piccoli; layout dedicato per landscape; su desktop basso il testo si riduce se supera il muro.
- Orbita di «Impresa Completa»: le etichette uscivano fino a 200 px dal muro; il raggio ora dipende dalla dimensione dell'illustrazione.
- Header su schermi <400 px più compatto; textarea a 16 px e niente focus automatico su touch (evita zoom/tastiera che ridimensiona la scena).

## Prestazioni
- Pavimento su canvas (vedi sopra); `:hover` sticky dei tocchi disattivato; blur dei pannelli disattivato sui touch (sfondo già al 92%); shimmer del pulsante in pausa sui pannelli non attivi.
- Pacchetti: il cambio colore non anima più una custom property (ridipingeva lo schermo a ogni frame) ma due livelli in dissolvenza (solo opacity).
- Anteprime dal vivo (`progetti/*.html?pv=1`): pixel ratio 1, animazioni/rAF in pausa durante i movimenti di camera, 30 fps su touch. Le pagine aperte normalmente non cambiano.

## Descrizioni dei servizi nei pacchetti
- Ogni scheda ha ora una breve descrizione sotto il titolo (campo `d:` di ciascun pacchetto nell'array `K` di `pacchetti.html`), nel colore «muted» della sala, senza elenchi né box aggiuntivi.
- Il pannello «Come conviene» ha una sezione «Cosa include»: un servizio per riga (numero in mono + nome + una frase), testi nel dizionario `SD`.
- I testi si basano sui nomi dei servizi e sui concept; non contengono numeri, tempi o garanzie inventati. Vanno riletti e, se serve, adattati ai servizi reali.
- Su desktop il contenuto di ogni sala si adatta con una scala individuale (`--ks`) solo quando serve; sulla sala 05 il limite tiene conto dello schema del sito. Su mobile `--am` riserva lo spazio minimo all'illustrazione.

## Tempi di consegna e 7° pacchetto
- **Tempi di consegna**: riga discreta «Consegna indicativa · 3–5 giorni» sotto i pulsanti di ogni scheda; nel pannello «Come conviene» il blocco «Tempi di consegna» (stima orientativa, non garantita; anche prima, anche oltre i 5 giorni; dipende da richieste/progetti e complessità); una riga anche nel modulo di richiesta. Testi in `pl()`, `sheet()` e `#dtm` in `pacchetti.html`.
- **Negozio Aperto (07)**: E-commerce + Landing page + Profilo Google + Presentazione. Valore €4119, prezzo €2890, −30%, risparmio €1229. Prezzi di riferimento dei servizi ricavati dai pacchetti esistenti: Profilo Google €249, Landing page €890, Presentazione €490 (Sito 5 pagine €1490, Registro preventivi €490); **E-commerce €2490 è una stima da confermare** (in `K[6]`: se cambia il listino, aggiorna `val`, `pr`, `sc`, `ris`).
- L'anello è ora generico a N sale (`N=K.length`): per aggiungerne altre basta un elemento in `K`, uno in `ART`, un colore in `C` e il CSS della sala.
