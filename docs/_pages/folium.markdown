---
layout: default
title:  "Grafo e Community"
subtitle: ""
header_type: hero #base, post, hero,image, splash
header_img: assets/images/body_graph.jpg
header_title: "Grafo e Community"
vega: false
---

Per quanto riguarda il grafo, abbiamo scaricato tramite l’API di PubMed tutti gli articoli che citavano una pubblicazione del nostro dataset e li  abbiamo filtrati per ottenere solo quelli già presenti nel dataset europeo.

Tramite la libreria Networkx abbiamo costruito il grafo diretto ponendo come nodi gli articoli e come archi le citazioni. Più precisamente abbiamo orientato gli archi dal documento citato verso quello citante, così che un arco rappresenti la trasmissione dell’informazione. Con questa convenzione, l’out-degree rappresenta il numero di citazioni ricevute da un articolo.

Successivamente ci siamo limitati a studiare la componente gigante del grafo che comprende circa il 98% dei nodi.
Statistiche sulla GC: 

<ul>
  <li>Sulla componente gigante abbiamo calcolato l’assortativity nella versione ‘out’ ‘out’ 
per capire se articoli con degree alto (quindi molto citati) tendono ad essere citati da altri articoli anch’essi molto citati. Come forse era prevedibile l’assortativity è risultata essere dello 0.0063 circa, cioè articoli molto citati non si citano tra loro in modo sistematico, ma nemmeno sono citati solo da articoli poco citati (misto di citazioni incrociate tra articoli molto e poco citati).</li>
  <li>calcolato l’assortativity nella versione ‘in’-’in’ per capire se articoli che citano molto tendono a citare altri articoli che a loro volta citano molto, questa assortativity è risultata essere dello 0.18 , cioè è presente una tendenza omofila, quindi articoli che citano molto tendono a citare altri articoli che a loro volta citano molto. In altre parole, i paper “ricchi di riferimenti” tendono a citare altri paper altrettanto ricchi di riferimenti.</li>
  <li>Abbiamo anche calcolato i coefficienti di clustering locale e globale che sono risultati essere dello 0.054 e 0.0068 rispettivamente che implica che le citazioni non si concentrano in gruppi chiusi, ma si distribuiscono in maniera più radiale o aciclica.</li>
</ul>

Lo studio del grafo è stato sfruttato per estrarre dai dati delle comunità corrispondenti ad articoli su un argomento specifico. Inizialmente abbiamo provato ad applicare l’algoritmo di Girvan Neuman, ma tale approccio è risultato infattibile a causa della grande dimensione del grafo. Abbiamo quindi scelto l’algoritmo di Leiden in quanto massimizza la modularità per trovare insiemi densamente connessi internamente, che corrispondono bene a gruppi di articoli affini. Inoltre Leiden è più veloce e accurato del suo predecessore Louvain su grafi grandi e sparsi. 

<strong>Problemi di Leiden</strong>: Leiden utilizza la modularità e dunque può ignorare piccole comunità se queste non migliorano abbastanza la metrica (Risoluzione limitata) e dunque rischia di fondere comunità diverse in una più grande. Inoltre Leiden include elementi di randomizzazione: è possibile ottenere risultati leggermente diversi a ogni esecuzione, a meno di fissare un seed.

Una volta ottenute così 135 comunità ci siamo soffermati sulle più popolate (>100 articoli) e abbiamo calcolato per ciascuna la percentuale di articoli finanziati, decidendo poi di analizzare le comunità in cui almeno un quinto degli articoli è stato finanziato. 

Per queste 6 comunità abbiamo ‘estratto’ gli specifici ambiti medici/ malattie tramite dei wordcloud e le aziende più frequenti per analizzare come le aziende e le rispettive aree di influenza si distribuiscono tra le comunità. I risultati di questa analisi sono visibili nei grafici sankey.

Dal grafo abbiamo visto che gli articoli con finanziamenti hanno in media 2 citazioni in più rispetto a quelli senza
media cit. per art senza=3.649699434891231
media cit. per art con= 5.7747452520396765
