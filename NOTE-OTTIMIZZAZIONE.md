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
