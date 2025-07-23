---
layout: default
title: Installation
header_title: "Scraping e Geolocalizzazione"
header_type: hero #base, post, hero,image, splash
header_img: assets/images/geocut.png
---

# Scraping



# Definizione geografica

All’interno del progetto questa sezione si inserisce come componente per analizzare gli articoli presi in esame su PubMed dal 2017 al 2024. Lo scopo è identificare pattern in relazioni a tre dimensioni prese in esame: affiliazione geografica, disclosure COI e presenza di aziende esplicitamente dichiarate. 

La prima parte della pipeline è dedicata alla creazione di un dataset geografico aggregando gli articoli scientifici e attribuendo le nazionalità partendo dalle informazioni contenute nelle affiliazioni. 

E’ stato utilizzato un approccio ibrido per l’inferenza del paese con una prima parte riguardante:

<ul>
  <li>Matching testuale diretto sul nome delle nazioni </li>
  <li>Dizionari euristici per città ed istituzioni ricorrenti</li>
  <li>Normalizzazione dei paesi</li>
</ul>


Questo ha portato ad una prima classificazione in 4 categorie: 

<strong>Eu</strong>: articoli  a singola nazione europea

<strong>Non Eu</strong>: articoli  a singola nazione non europea

<strong>Ambigous</strong>: articoli con più di una nazione

<strong>Unknown</strong>: articoli non coperti dalla classificazione

Per i casi ambiguous sono si è effettuata un’ulteriore divisione in europei, non europei e nazionalità miste, parallelamente per i casi non classificati è stato applicato un modello Spacy per estrarre unità geografiche, GPE, ed aggiornare i dizionari per l’assegnazione.

Questo ha permesso la seguente classificazione

eu  2144703
ambiguous_all_eu   672667
ambiguous_mixed   380531
non-eu    54942
unknown    21652
ambiguous_all_non_eu     2117

Successivamente si è proceduto ad un’analisi e pulizia ulteriore del dataset globale, dalla rimozione dei duplicati raggiungendo le seguenti percentuali nelle classi

Si è effettuato un filtraggio dei solo papers europei ed alla loro rappresentazione creazioni grafica  partendo da una cartina geografica tramite ploty della percentuale di articoli con COI, la classifica dei paesi per numeri di pubblicazioni scientifiche, la classifica dei paesi con maggior numero di paper in percentuale presentati con COI ed il trend delle disclosure dei singoli paesi nei diversi anni. 

Il passo successivo è stato unire il dataset geografico così creato con il dataset semantico contenente i tag semantici delle aziende e le estrazioni delle diverse discipline mediche tramite medGEMMA. Il merge è stato effettuato grazie al codice PMID unico identificativo dell’articolo. Questo ha permesso di concatenare l’ultima porzione della pipeline.

In quest’ultima sezione si intende verificare se esistano concentrazioni geografiche statisticamente significative tra specifiche aziende e specifiche nazioni. 

La procedure è avvenuta nel seguente modo:

<strong>Selezione delle aziende di interesse</strong>:
È stato selezionato il sottoinsieme di aziende che, sommate, costituiscono il 95% della presenza aziendale complessiva nel dataset. Questa soglia serve a escludere outlier a bassa frequenza e ridurre il rumore statistico nella matrice finale. Il risultato ha portato ad analizzare un subset che rappresenta il 10.24% rispetto al totale degli articoli con COI 


<strong>Costruzione della tabella di contingenza</strong>
Si è costruita una matrice azienda  per paese , in cui ogni cella rappresenta il numero di articoli in cui quella specifica azienda è associata a quella specifica nazione.


<strong>Test di indipendenza e analisi dei residui</strong>
È stato applicato un test del chi-quadro per valutare l’ipotesi nulla di indipendenza tra azienda e paese. Successivamente, sono stati calcolati i residui standardizzati per ogni cella, al fine di identificare le combinazioni con maggiore scostamento rispetto alla frequenza attesa.



<strong>Ulteriori analisi</strong>
Il test del chi-quadro ha confermato una forte dipendenza tra aziende e paesi (Chi2 = 12115.787, dof = 266, p-value < 1e-300).
Successivamente, sono stati calcolati i residui standardizzati per ciascuna cella della matrice, Per valutare la significatività puntuale, è stato applicato un filtro basato sulla soglia |r| > 1.96, corrispondente a un livello di confidenza del 95% (p < 0.05) sotto l’assunzione di distribuzione normale standard. Questo permette di evidenziare quali combinazioni specifiche mostrano scostamenti significativamente superiori (o inferiori) alla frequenza attesa producendo la seguente tabella dei primi 10 risultati:

Novo Nordisk – Denmark → 65.17


GlaxoSmithKline – United Kingdom → 33.74


Novo Nordisk – United Kingdom / Denmark → 19.88


Bayer – Germany → 18.31


Medtronic – Netherlands → 18.22


AstraZeneca – Sweden → 14.41


AstraZeneca – United Kingdom → 13.08


Takeda Pharmaceutical – United Kingdom → 12.21


Novo Nordisk – Sweden → 10.39


Boehringer Ingelheim – Denmark → 9.45

I valori elencati indicano una presenza molto più elevata rispetto a quanto atteso in base alla distribuzione marginale delle frequenze, confermando pattern di concentrazione editoriale coerenti con la sede geografica dell’azienda o la sua area strategica di influenza. Sebbene i residui standardizzati correggano per le dimensioni marginali (ossia tengano conto del volume totale di articoli per azienda e per paese), l’assunzione di indipendenza resta teoricamente forte, e potrebbe non cogliere appieno dinamiche sottostanti più complesse come accordi editoriali, strategie multinazionali o effetti storici e istituzionali.