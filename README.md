# Strade Provinciali — Provincia di Cosenza

App mobile (PWA installabile su Android) per consultare i tracciati delle strade provinciali, i cippi chilometrici, i limiti di competenza e le segnalazioni di manutenzione, con foto e vista Street View di ogni punto. Pensata per cantonieri, capocantonieri e ditte.

Fase attuale: prova su un gruppo di strade della zona di Cassano allo Ionio (Servizio 3, Gruppi 15-18).

## Come si aggiornano i dati

I dati vengono dai file KML esportati da Google Earth (uno per strada), che si trovano in `STRADE PER APP/` (cartella a fianco di questa, fuori da questo repository).

```
python genera_app.py
```

Lo script legge tutti i KML, unisce segnaposto + vista Street View + foto di ogni punto, estrae le foto in `foto/` e riscrive i dati dentro `index.html` (tra `/*DATA_START*/` e `/*DATA_END*/`). Poi:

```
git add -A && git commit -m "aggiornamento dati" && git push
```

## Note

- Le foto sono in gran parte schermate di Google Street View (© Google): la fonte è indicata nell'app.
- Lo stato delle segnalazioni (da fare / assegnato / fatto) è salvato solo sul dispositivo di chi lo imposta.
