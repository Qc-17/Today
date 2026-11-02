# Today – versione web

Sito/PWA mobile-first ispirato al prototipo Today. Non richiede backend per conservare le foto: usa IndexedDB e localStorage del browser.

## Avvio

Serve un hosting HTTPS (ad esempio GitHub Pages) oppure un server locale. Aprire `index.html` direttamente come `file://` può impedire fotocamera, notifiche e service worker.

## Funzionalità

- Fascia oraria giornaliera personalizzabile.
- Orario casuale scelto all'interno della fascia.
- Finestra di 10 minuti.
- Scatto tramite fotocamera live del browser (`getUserMedia`), senza selezione dalla galleria.
- Un solo scatto al giorno.
- Foto conservate in IndexedDB e cancellate al superamento della scadenza.
- Galleria limitata al diario attuale, senza archivio dei cicli precedenti.
- PWA installabile e shell offline.

## Limiti inevitabili del web statico

1. Il browser non garantisce notifiche programmate quando il sito è chiuso. In questa versione la notifica viene mostrata quando la pagina è aperta/attiva; al ritorno sul sito viene verificato lo stato e applicata un'eventuale scadenza. Per notifiche affidabili a sito chiuso serve un backend con Web Push oppure un'app nativa.
2. La condivisione foto dal browser usa il menu di condivisione del sistema quando supportato. Il web non può invocare in modo affidabile il composer Instagram Stories come fa un Intent Android nativo, né verificare universalmente se Instagram è installato.
3. Le foto sono locali al browser/dispositivo e possono essere rimosse se l'utente cancella i dati del sito o il browser libera lo spazio.
4. Per usare fotocamera e notifiche, il sito deve essere servito via HTTPS (o localhost).

## Pubblicazione su GitHub Pages

Carica tutti i file della cartella nella root della repository e abilita GitHub Pages dalle impostazioni del repository. Non serve una build React: è una PWA statica.
