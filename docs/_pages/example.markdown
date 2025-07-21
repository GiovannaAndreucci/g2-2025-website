---
layout: default
title: "Home"
show_sidetoc: true
header_type: hero
header_img: assets/images/folium_map.webp
header_title: "You don't need to be coy, COI!"
subtitle: "Medical (European) Disclosure Survey"
vega: true
---

<div class="full-width-wrapper">
    <img src="{{ site.baseurl }}/assets/images/header.svg" alt="sbd-pattern" class="full-width-image">
</div>

La ricerca scientifica è cambiata enormemente negli ultimi anni. Il numero di pubblicazioni si è infatti rivelato in esponenziale aumento, determinando così una nuova e complessa stratificazione della produzione scientifica. In quest’ottica riteniamo che l’avvento delle più recenti tecniche di Artificial Intelligence e Big Data Analysis possano essere in grado di aiutare i ricercatori, nonché gli enti pubblici e privati, a gettare nuova luce sul loro settore di studio, ad orientare la loro ricerca e a trovare nuove connessioni e nuovi significati.
Il presente lavoro si propone di investigare il settore dell’healthcare, uno degli ambiti più ‘spinosi’ e compositi (per via del gran numero di investimenti e per la granularità delle diverse specializzazioni) e nello specifico si propone di ricostruire il rapporto fra aziende e ricerca tramite l’analisi delle dichiarazioni di conflitto d’interesse pubblicamente consultabili (COI statements).

I dati a nostra disposizione sono stati ottenuti principalmente dall’archivio ad accesso libero PubMed. Attraverso le tecniche di web scraping è stato possibile recuperare: PMID, titolo, abstract, autori, affiliazioni degli autori, nome della rivista, citazioni ricevute e COI statement dichiarato (o non dichiarato) dagli autori. La ricerca è stata condotta estraendo l’intera produzione dei ricercatori europei dal 2017 al 2024, arrivando a considerare oltre tre milioni di articoli. Grazie all’impiego di MedGemma 4B (un LLM specializzato nell’analisi di testi medici) è stato possibile ricavare l’area medica principale di ogni lavoro e, ove disponibile, tramite la Name-Entity-Recognition operata da DistilBERT, si è proceduto ad ‘aggregare’ le informazioni contenute nel COI statement individuando le aziende coinvolte.
Siamo poi passati ad analizzare il rapporto tra le suddette aziende, il numero di articoli ‘interessati’ associati a ciascuna azienda e le aree mediche negli anni di riferimento. Infine, investigando il numero ed il tipo di citazioni, abbiamo costruito un grafo con cui studiare la composizione di speciali comunità all’interno dei nostri dati.

---

![](https://placehold.co/800x200/png)

<div class="didascalie"> questa è una didascalia </div>


# What's up, COI?

PubMed è oggi il più grande archivio bibliografico online ad accesso libero al mondo. Il suo germe nacque (in forma cartacea) nel 1949 presso la National Library of Medicine (NLM) Bethesda, Maryland (USA) e la sua prima versione online risale a gennaio 1996. Al 27 novembre 2010, erano oltre 17 milioni gli articoli reperibili tramite abstract, mentre gli articoli disponibili in formato integrale erano oltre 3,1 milioni. Presso il motore di ricerca online è possibile ricercare per autore, rivista, o testo libero, le pubblicazioni scientifiche dal 1949 ad oggi e su diversi dataset scientifici internazionali.
Come illustrato da Enrico Granieri, professore ordinario di Neurologia presso l’Università di Ferrara, dalla fine degli anni Ottanta si è fatta largo una crescente attenzione verso la dichiarazione dei conflitti d’interesse in sede di pubblicazione dei lavori scientifici, supervisionata in primis dalla stessa casa editrice, e poi dall’apporto fondamentale dei comitati etici nella gestione di questioni legate alla pratica medica e alla ricerca. E Pubmed? Come si è orientato il più grande archivio ad accesso libero rispetto a questa tematica?
Nel 2016 un gruppo di senatori del Congresso USA, su richiesta di diversi scienziati e organizzazioni statunitensi, ha chiesto alla NLM di elencare i conflitti di interesse (COI) degli autori in una dichiarazione standardizzata (in una specifica sezione della pagina web) come parte degli abstract indicizzati su PubMed. L'inclusione di un COI statement pubblico nella pagina web di PubMed, dove è presente anche l’abstract dell’articolo, è sicuramente un passo importante (e auspicabile) nella direzione che indicava il prof. Granieri. Considerando che i lettori potrebbero non avere accesso all'articolo completo (dove dovrebbe essere presente una dichiarazione di conflitto d’interesse), un COI pubblico risulta uno strumento fondamentale (unitamente all’abstract di un articolo) per valutare preliminarmente uno studio e/o per orientare le decisioni cliniche. Tali modifiche sono state implementate l'8 marzo 2017.
L’obiettivo di questo progetto è quello di ‘catalogare’ le pubblicazioni scientifiche, edite da ricercatori europei, presso l’archivio PubMed dal 2017 al 2024 prestando particolare attenzione al nuovo campo COI, introdotto da PubMed in tempi relativamente recenti. Ci proponiamo di analizzare quali sono le aree mediche maggiormente rappresentate, e se esistono delle correlazioni tra alcune di esse. Inoltre, siamo interessati a indagare i rapporti fra aziende private e ricerca biomedica e le modalità in cui questi rapporti si sviluppano. Si tratterà quindi di valutare la possibilità di ricostruire questi rapporti (per loro natura scomodi e facile oggetto di strumentalizzazioni politiche) a partire da un dato essenzialmente pubblico, a cui teoricamente tutti possono avere accesso. Il vantaggio nell’impiego dei Big Data (e delle tecniche capaci di elaborarli) risiede nella possibilità di automatizzare il reperimento di questo dato pubblico e di contribuire in maniera fondamentale all’analisi dei dati stessi.
Ci teniamo a sottolineare che lo scopo del nostro progetto non è arrivare a ‘denunciare’ un conflitto di interessi che, lo ripetiamo, è già reso pubblico a monte. Il nostro scopo è quello di presentare un'altra prospettiva sulla produzione scientifica, capace di stimolare lo sviluppo di nuove traiettorie di ricerca per gli esperti del settore e aiutare gli utenti a orientarsi nel mare magnum delle pubblicazioni.

# Oh COI, where art thou?

# What did you major in, COI?

<div class="flourish-embed flourish-bar-chart-race" data-src="visualisation/24243729"><script src="https://public.flourish.studio/resources/embed.js"></script><noscript><img src="https://public.flourish.studio/visualisation/24243729/thumbnail" width="100%" alt="bar-chart-race visualization" /></noscript></div>
 

<div style="height: 400px">
  <vegachart schema-url="/g2-2025-website/assets/charts/percentage_barchart.json" style="width: 100%; height: 100%"></vegachart>
</div>

# CIAO


<div style="height: 200px">
  <vegachart schema-url="{{site.baseurl}}/assets/charts/increment_chart.json" style="width: 50%; height: 50%"></vegachart>
</div>





# You don’t know where your interest lies, COI…






# And now… COInnect the nodes!













