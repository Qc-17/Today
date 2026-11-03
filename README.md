# Today – versione web

Sito/PWA mobile-first ispirato al prototipo Today. Non richiede backend per conservare le foto: usa IndexedDB e localStorage del browser.

## Avvio

Serve un hosting HTTPS (ad esempio GitHub Pages) oppure un server locale. Aprire `index.html` direttamente come `file://` può impedire fotocamera, notifiche e service worker.

## Funzionalità

- Fascia oraria giornaliera personalizzabile.
- Orario casuale scelto all'interno della fascia.
- Finestra di 10 minuti.
- Scatto tramite fotocamera live (posteriore o anteriore, a scelta) del browser (`getUserMedia`), senza selezione dalla galleria.
- Un solo scatto al giorno.
- Dopo lo scatto: nota facoltativa (max 140 caratteri) e cuore per i «bei momenti».
- Ricordi: circa ogni 3-4 giorni, a un orario casuale nella fascia, una vecchia foto (più probabile se col cuore) sostituisce la foto principale per 10 minuti, sempre più sbiadita con l'età. In quei 10 minuti la galleria è chiusa e non viene richiesto nessuno scatto.
- Foto conservate in IndexedDB. Se il momento viene saltato non vengono cancellate: si nascondono e non compaiono più in galleria né nei ricordi.
- Ripristino: dopo sette giorni di fila senza saltare il momento, una foto nascosta a caso torna visibile e il conteggio riparte da zero. Saltare il momento azzera il conteggio.
- PWA installabile e shell offline.

## Limiti inevitabili del web statico

1. Il browser non garantisce notifiche programmate quando il sito è chiuso (vale anche per i ricordi). In questa versione la notifica viene mostrata quando la pagina è aperta/attiva; al ritorno sul sito viene verificato lo stato e applicata un'eventuale scadenza. Per notifiche affidabili a sito chiuso serve un backend con Web Push oppure un'app nativa.
2. Le foto non hanno pulsanti di condivisione o download e l'interfaccia blocca salvataggio con pressione lunga, tasto destro e trascinamento. Nessun sito web può però impedire screenshot, registrazione dello schermo o l'uso degli strumenti per sviluppatori del browser.
3. Le foto sono locali al browser/dispositivo e possono essere rimosse se l'utente cancella i dati del sito o il browser libera lo spazio.
4. Per usare fotocamera e notifiche, il sito deve essere servito via HTTPS (o localhost).
