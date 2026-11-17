# House Prices — traccia del progetto

Obiettivo: prevedere il prezzo di vendita (`SalePrice`) delle case del test set.
La competizione valuta l'RMSE tra i logaritmi dei prezzi previsti e reali:
[valutazione Kaggle](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/overview/description).

Questa è la traccia da seguire. Il codice, i grafici e le osservazioni vanno in
`file.ipynb`, usando le stesse sezioni nell'ordine indicato.

## Ordine di lavoro

- [ ] **1. Caricare e controllare i dati**
  Leggere `train.csv` e `test.csv` dalla cartella
  `data/house-prices-advanced-regression-techniques/`. Controllare prime righe,
  dimensioni, tipi delle colonne, duplicati e valori mancanti. Consultare
  `data_description.txt` per capire il significato delle variabili.

- [ ] **2. Impostare la validazione**
  Separare `SalePrice` dalle caratteristiche. Escludere `Id` dagli input del
  modello e conservarlo per la submission. Dividere il training set in una parte
  per addestrare e una per valutare, fissando un seme casuale. `test.csv` va
  conservato per le previsioni finali: non contiene i prezzi reali. In seguito,
  rendere il confronto più robusto con una cross-validation a 5 parti.

- [ ] **3. Esplorare i dati di addestramento**
  Studiare la distribuzione di `SalePrice`, anche in scala logaritmica, e le
  relazioni con superficie, qualità, quartiere e anno di costruzione. Esaminare
  valori mancanti e outlier, annotando le osservazioni prima di modificare i dati.

- [ ] **4. Preparare le variabili**
  Distinguere i dati mancanti dalle assenze reali: per esempio, alcuni `NA`
  indicano che una casa non ha piscina o garage. Trattare i codici categorici,
  come `MSSubClass`, come categorie. Gestire valori mancanti, codifica delle
  categorie e standardizzazione quando utile al modello tramite una pipeline.
  Imparare mediane, categorie e parametri solo sui dati di addestramento di
  ciascuna suddivisione, poi applicarli ai dati di validazione.

- [ ] **5. Costruire una prima baseline**
  Valutare una previsione costante come riferimento minimo, poi una regressione
  Ridge sul logaritmo di `SalePrice`. Registrare l'RMSE sui logaritmi dei prezzi
  usando i dati di validazione.

- [ ] **6. Confrontare e migliorare i modelli**
  Provare modelli ad alberi e gradient boosting. Sperimentare variabili come
  superficie totale ed età della casa alla vendita, poi ottimizzare i parametri
  più utili. Confrontare gli esperimenti sulle stesse suddivisioni e annotare
  modello, modifiche e punteggio.

- [ ] **7. Creare la submission**
  Riaddestrare la pipeline scelta su tutto `train.csv`, prevedere i prezzi di
  `test.csv` e riportarli alla scala originale se è stato usato il logaritmo.
  Creare `submission.csv` seguendo `sample_submission.csv`: 1.459 righe di dati,
  colonne `Id,SalePrice`, nessun indice aggiuntivo, prezzi positivi e nessun
  valore mancante.

Primo traguardo: completare una pipeline semplice e ottenere una prima
submission valida, poi migliorarla confrontando i risultati in validazione.
