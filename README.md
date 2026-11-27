# PlanMaker

Web app per disegnare la pianta di una casa e arredarla, pensata per PC e tablet.
È un'unica pagina HTML: non serve installare niente, non c'è un server e non ci sono dipendenze da compilare.

## Cosa fa

- **Costruzione**: muri e tramezzi con aggancio *interno / centro / esterno*, lunghezza e angolo digitati, porte (battente, doppia, scorrevole a scomparsa ed esterna, soffietto) e finestre (1–3 ante, portafinestra, scorrevole, vasistas) che si agganciano ai muri, stanze con superficie, quote e testi.
- **Arredi parametrici**: circa 50 blocchi in Camera, Soggiorno, Pranzo, Cucina, Bagno, Studio e Varie (letto con misure standard, divano con posti e penisola, tavolo con sedie, cucina lineare con moduli, armadio, doccia, scala…). I mobili si appoggiano da soli ai muri, anche inclinati, e negli angoli. Si possono scegliere i colori di riempimento e delle linee e salvare i propri arredi preferiti.
- **Griglia e snap**: griglia attivabile con il passo regolabile, aggancio a estremi, punti medi e muri, modo ortogonale.
- **Layer** da accendere, spegnere e bloccare: muri, tramezzi, porte, finestre, arredi, stanze, quote, testi, linee, sfondo.
- **Import**: DXF (linee, polilinee, archi, cerchi, blocchi), PDF e immagini come sfondo, con calibrazione della scala.
- **Export**: PDF vettoriale in scala, DXF per AutoCAD (in cm, con layer), PNG, JSON del progetto.
- **Layout di stampa**: foglio da A4 ad A0, scala, nord, scalimetro, legenda ambienti, cartiglio.
- Tema chiaro e scuro, comandi touch (pizzico per lo zoom, pulsanti "Fine", "Ruota", "Elimina").

## Struttura

```
index.html             l'app completa (HTML + CSS + JavaScript)
manifest.webmanifest   per installarla come app su tablet e telefono
sw.js                  service worker: funzionamento offline
icons/                 icone dell'app
```

## Pubblicarla su GitHub Pages

1. Crea un nuovo repository su GitHub, per esempio `planimetria`.
2. Carica il contenuto di questa cartella: con **Add file → Upload files** trascina tutti i file e la cartella `icons`, oppure usa GitHub Desktop.
3. Vai in **Settings → Pages**, in *Source* scegli **Deploy from a branch**, branch `main`, cartella `/ (root)`, e salva.
4. Dopo circa un minuto l'app è online su `https://TUO-UTENTE.github.io/planimetria/`.

## Installarla sul tablet

Apri l'indirizzo di GitHub Pages sul tablet:

- **iPad (Safari)**: Condividi → *Aggiungi alla schermata Home*.
- **Android (Chrome)**: menu ⋮ → *Installa app*.

Dopo il primo avvio funziona anche offline.

## Aggiornare l'app

Sostituisci `index.html` nel repository con la nuova versione. Nel file `sw.js` cambia `VERSION` (per esempio `planimetria-v2`), così i dispositivi scaricano la versione nuova.

## Dove vengono salvati i progetti

In questa versione autonoma il progetto si salva **nel browser del dispositivo** (localStorage). Per spostare un progetto tra PC e tablet usa **⇩ Esporta → Progetto JSON** e poi *Carica dal testo* sull'altro dispositivo.

Lo sfondo importato (DXF, PDF, immagine) resta solo sul dispositivo dove l'hai importato.

La sincronizzazione automatica tra dispositivi funziona solo nella versione ospitata in Claude, perché usa l'archivio di Claude.

## Note

- **DWG**: è un formato chiuso e non si può leggere né scrivere in modo affidabile in una pagina web. Esporta il **DXF** e in AutoCAD fai *Salva con nome → DWG*. Per importare, salva prima il DWG come DXF (in AutoCAD o con il convertitore gratuito ODA File Converter).
- L'import dei **PDF** usa la libreria pdf.js caricata da cdnjs: serve la connessione la prima volta che importi un PDF.
- Unità di misura interne: centimetri.
