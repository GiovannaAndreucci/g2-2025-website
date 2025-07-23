---
layout: default
title: "Home"
show_sidetoc: true
header_type: hero
header_img:  assets/images/vesalio2.jpeg
header_title: "You don't need to be coy, COI!"
subtitle: ""
vega: true
plotly: true
---

<div class="full-width-wrapper">
    <img src="{{ site.baseurl }}/assets/images/header copy.svg" alt="sbd-pattern" class="full-width-image">
</div>

La ricerca scientifica è cambiata enormemente negli ultimi anni. Il numero di pubblicazioni è aumentato esponenzialmente, determinando una nuova e complessa stratificazione della produzione scientifica. 
In quest’ottica riteniamo che l’avvento delle più recenti tecniche di Big Data Analysis e i modelli di Artificial Intelligence possano essere in grado di aiutare a gettare nuova luce su questo settore, fornendo strumenti che orientino la ricerca e la arricchiscano di nuovi significati.

Il nostro lavoro si propone di investigare il settore dell’healthcare, uno degli ambiti più complessi, da un lato per via del gran numero di investimenti, dall’altro per la granularità delle diverse specializzazioni. In particolare, cercheremo di ricostruire il rapporto fra enti pubblici e privati da un lato e ricerca dall’altro, tramite l’analisi delle dichiarazioni di conflitto d’interesse (d’ora in poi abbreviato in COI statements), associate agli articoli e pubblicamente consultabili.

Abbiamo deciso di concentrarci sulla produzione dei ricercatori europei dal 2017 al 2024, arrivando a considerare oltre tre milioni di articoli. La nostra principale fonte di dati è l’archivio ad accesso libero online PubMed. Da qui, attraverso tecniche di web scraping è stato possibile recuperare le informazioni necessarie relative a ogni articolo di nostro interesse, come titolo, paese di provenienza dell’articolo, numero di volte che l’articolo è stato citato e, ovviamente, il COI statement. 

Una volta ottenuti questi dati, abbiamo utilizzato il modello MedGemma 4B, specializzato nell’analisi di testi medici, per categorizzare ogni articolo secondo la sua principale area medica di appartenenza. Inoltre, tramite  una versione del modello DistilBERT specializzato in Named-Entity-Recognition, siamo stati in grado di individuare le aziende citate all’interno del COI statement di ciascun articolo. Abbiamo poi impiegato quanto così ricavato per analizzare il rapporto tra articoli e aziende associate a ciascuno di essi, distinguendoli per aree mediche.
Infine, collegando ogni articolo a quelli che lo citano e tenendo conto del numero di citazioni, abbiamo costruito un grafo, in modo da poter osservare relazioni e comunità tra gli articoli del nostro dataset.

---

<h1 class="text-center">What's up, COI?</h1>

Come illustrato da Enrico Granieri, professore ordinario di Neurologia presso l’Università di Ferrara, dalla fine degli anni Ottanta nella ricerca medica si pone una crescente attenzione alla necessità di esplicitare i conflitti d’interesse nella pubblicazione di lavori scientifici, sotto la supervisione in primis delle stesse case editrici, ma anche dei comitati etici, centrali per la gestione di questioni legate alla pratica medica e alla ricerca. Come si è adeguato il più grande archivio bibliografico online ad accesso libero al mondo, ossia PubMed, a queste nuove necessità?

Nato nel 1949 come archivio cartaceo presso la National Library of Medicine (NLM) a Bethesda, Maryland (USA), la prima versione online di PubMed risale a gennaio 1996. Meno di quindici anni dopo, nel 2010, erano oltre 17 milioni gli articoli reperibili tramite abstract, mentre gli articoli disponibili in formato integrale erano oltre 3,1 milioni. Ad oggi si stima che il numero degli articoli provenienti dalla sola letteratura biomedica (Medline) sia di circa 38 milioni. Questo archivio è inoltre dotato di un motore di ricerca che permette di filtrare gli articoli per autore, rivista, o testo libero.

Nel 2016 un gruppo di senatori del Congresso USA, su richiesta di diversi scienziati e organizzazioni statunitensi, ha chiesto alla NLM di aggiungere il COI statement degli autori alle informazioni indicizzate per gli articoli sul loro motore di ricerca. Tale inclusione, implementata a partire dall’8 marzo 2017, è stata un passo importante nella direzione citata dal prof. Granieri, dal momento che costituisce un nuovo strumento fondamentale per la valutazione preliminare di uno studio in sede di ricerca o di decisioni cliniche, sebbene non sia incluso in tutti gli articoli.

Il nostro obiettivo è proprio studiare questo nuovo elemento dell’archivio PubMed negli articoli europei dal suo inserimento nel 2017 fino al 2024, analizzandone la distribuzione rispetto alle discipline mediche. Inoltre vogliamo scoprire in che misura questo dato pubblico permetta di ricostruire i rapporti tra aziende e sedi della ricerca, rapporti per loro natura facile oggetto di strumentalizzazioni politiche. Queste operazioni sono rese possibili da tecniche di Big Data Analysis, che automatizzano il reperimento e l’analisi dell'enorme mole di dati necessari.

Chiaramente, lo scopo del nostro progetto non è denunciare un conflitto di interessi che, come detto sopra, è pubblicamente accessibile a chiunque acceda al sito di PubMed. Il nostro scopo è quello di presentare una prospettiva inedita sulla vasta produzione scientifica recente, che possa stimolare lo sviluppo di nuove traiettorie di ricerca e aiutare gli utenti a orientarsi nel mare magnum delle pubblicazioni.

---

<h1 class="text-center">Oh COI, where art thou?</h1>

Attraverso l’API di Entrez (il motore di ricerca adottato dalle più importanti banche dati di letteratura biomedica) è stato possibile interrogare il database di PubMed per recuperare tutti gli articoli rilevanti per la nostra indagine. Il primo ostacolo ha riguardato l’effettiva possibilità di isolare gli articoli con provenienza UE, con l’aggiunta di Regno Unito e Svizzera: in quale prospettiva è possibile infatti considerare un articolo europeo a partire dalle sole affiliazioni degli autori? D’altra parte, specie se si considera la letteratura biomedica (che conta un gran numero di studi multicentrici), si potrebbe pensare che i gruppi di ricerca presentino una moderata (se non addirittura elevata) eterogeneità geografica. In una situazione di questo tipo, sarebbe stato quantomai azzardato tentare di costituire un labelling geografico. In realtà, a partire da una semplice query capace di considerare tutti gli articoli con almeno un autore con affiliazione europea, i dati risultano piuttosto eloquenti.

<div style="height: 400px">
  <vegachart schema-url="/g2-2025-website/assets/charts/geo_distribution_chart.json" style="width: 50%; height: 50%"></vegachart>
</div>

Escludendo dall’analisi i dati mancanti sulle affiliazioni e considerando la scala nazionale, notiamo come il 65% circa degli articoli presentino un’elevata omogeneità a livello di affiliazioni (queste ultime sono tutte riferibili a un unico stato europeo). Un altro 20% consta di affiliazioni ambigue su scala nazionale (ma comunque da considerarsi tutte europee).
Più del 10% riflettono un’ambiguità che esula dai confini europei, mentre meno del 5% presenta almeno un autore europeo, risultando però fortemente sbilanciato verso affiliazioni non europee. Una volta circoscritti gli articoli rilevanti per la nostra analisi, abbiamo deciso di quantificare l’effettiva compilazione del campo COI; su questo frangente i risultati sembrano essere in linea con quanto osservato da alcuni studi precedenti.

inserire grafico COI barre

Al generale incremento della produzione scientifica è associato un deciso aumento di articoli con COI statement dichiarato e una speculare diminuzione del volume di articoli con il campo COI non compilato. 
È inoltre possibile apprezzare un trend simile negli articoli per nazione, considerando solo i dieci paesi più produttivi.

<div style="height: 400px">
  <vegachart schema-url="/g2-2025-website/assets/charts/trend_disclosure_eu_chart.json" style="width: 100%; height: 100%"></vegachart>
</div>

La produzione scientifica polacca in questo senso mostra un incremento percentuale decisamente superiore alla media. A tal proposito è possibile riscontrare un elevato numero di COI dichiarato in buona parte dei paesi dell’Est Europa (oltre alla Norvegia), come osservabile nella mappa sottostante.

inserire mappa

La Romania da questo punto di vista detiene il record di articoli con COI dichiarato rispetto all’intera produzione scientifica pubblicata su PubMed, con oltre il 65% di articoli con un conflitto di interesse disponibile pubblicamente.

<div style="height: 400px">
  <vegachart schema-url="/g2-2025-website/assets/charts/top_countries_chart.json" style="width: 100%; height: 100%"></vegachart>
</div>


<h1 class="text-center">What did you major in, COI?</h1>

<div class="flourish-embed flourish-bar-chart-race" data-src="visualisation/24243729"><script src="https://public.flourish.studio/resources/embed.js"></script><noscript><img src="https://public.flourish.studio/visualisation/24243729/thumbnail" width="100%" alt="bar-chart-race visualization" /></noscript></div>
 

<div style="height: 400px">
  <vegachart schema-url="/g2-2025-website/assets/charts/percentage_barchart.json" style="width: 100%; height: 100%"></vegachart>
</div>


<div style="height: 400px">
  <vegachart schema-url="{{site.baseurl}}/assets/charts/increment_chart.json" style="width: 100%; height: 100%"></vegachart>
</div>





<h1 class="text-center">You don't know where your interest lies, COI...</h1>

Una volta isolati gli articoli in cui la sezione del COI statement fosse presente, è stato chiaramente essenziale per poter procedere con le analisi, processare il testo di tali statements. Per questo compito ci siamo affidati in prima battuta alla NER (Named Entity Recognition), una tecnica di elaborazione del linguaggio naturale (NLP) che identifica elementi specifici (entità) all'interno di un testo e li classifica in categorie predefinite come persone, luoghi, organizzazioni, date, ecc.

Il fatto che la forma degli statements non è standardizzata, ma espressa in linguaggio naturale, ha costituito un ostacolo per il processo: le aziende compaiono spesso con nomi e grafie diverse, il modello, su una tale quantità di dati, commette un numero considerevole di errori, i modelli NER non nascono specificatamente per riconoscere nomi di aziende healthcare.

Il modello che abbiamo scelto è distilbert-NER, versione specializzata per il NER di distilBERT, a sua volta una variante compressa del modello BERT. Applicandolo ai testi dei COI statement e selezionando tra le entità rilevate quelle categorizzate come “organizzazioni”, abbiamo ottenuto una lista di potenziali enti e aziende con cui gli autori di ciascun articolo avevano un rapporto di qualche tipo.

immagine coi

Abbiamo sottoposto questa lista preliminare ad un post-processing semi-automatico, con due obiettivi principali. Il primo, quello di uniformare i nomi delle aziende, soggetti a comuni errori e variazioni di grafia, riportandoli ad una sola forma standard. Per farlo, abbiamo creato dei pattern ad hoc per le aziende farmaceutiche, a partire dalle top 40 di un dataset contenente i nomi delle più grandi, e aggiungendo successivamente quelle che emergevano da una verifica manuale, fino ad arrivare ad un totale di 121 pattern. 

Il secondo obiettivo è stato quello di eliminare ciò che, per sua natura, sapevamo potesse verosimilmente costituire un errore nell’estrazione: ad esempio, parole con pochi caratteri (fino a due), o termini poco frequenti nel nostro corpus. Anche termini molto frequenti come “University” o “Pharma”, ma isolati erroneamente da espressioni più complesse, sono stati rimossi manualmente.  

Giunti a questo punto, gli articoli erano divisi in due categorie: da un lato, quelli senza alcun tag associato, ossia senza alcun conflitto di interessi risultante dalla nostra analisi; dall’altro, quelli con associati tag di aziende e/o enti pubblici, con cui uno o più autori hanno dichiarato di avere rapporti che possono costituire in qualche modo un conflitto d’interesse.

Come mostrato dal grafico qui sotto, gli articoli del secondo tipo, con conflitti esplicitati, sono cresciuti costantemente nel periodo osservato, passando da circa 10.000 nel 2017 a quasi 35.000 nel 2024. Questo aumento potrebbe riflettere il progressivo adeguamento a questa nuova funzione di PubMed.

retta numero articoli


Questa tendenza sembra essere proporzionale all’aumento generale delle pubblicazioni con COI statement presente, a loro volta aumentate molto rapidamente durante il periodo di nostro interesse, mostrando di nuovo una progressiva adeguazione a questa integrazione del sito. Si mantiene, però, pressoché costante negli anni l’incidenza dei due tipi di articoli sul totale.


grafici


Concentrandosi sulle 121 aziende individuate attraverso distibert-NER, vediamo che le prime cinque in particolare si distaccano dalle altre per il gran numero di articoli in cui sono presenti, mentre per le successive la frequenza cala rapidamente, arrivando ad avere la maggior parte delle aziende a una frequenza sotto 5.000.

grafico

Concentrandosi sulle 121 aziende individuate attraverso distibert-NER, vediamo che le prime cinque in particolare si distaccano dalle altre per il gran numero di articoli in cui sono presenti, mentre per le successive la frequenza cala rapidamente, arrivando ad avere la maggior parte delle aziende a una frequenza sotto 5.000.

grafici




<h1 class="text-center">That COI really tied the room together...</h1>


<h1 class="text-center">And now… COInnect the nodes!</h1>

# Sankey diagram

{% include plotly-graph.html id="grafico1" file="grafico1.html" height="600px" %}


e il secondo grafico sankey con i colori giusti

{% include plotly-graph.html id="grafico2" file="sankey_azi_aree.html" height="600px" %}








