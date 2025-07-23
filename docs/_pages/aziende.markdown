---
layout: default
title: Estrazione aziende
header_title: "Estrazione aziende"
header_type: hero #base, post, hero,image, splash
header_img: assets/images/hippocut2.png
---

In primis abbiamo provato ad utilizzare SpaCy. Tuttavia, i risultati apparivano molto poco precisi con un gran numero di match errati (nomi di autori o altri sostantivi irrilevanti) che sarebbero dovuti essere eliminati successivamente; per questo motivo abbiamo scartato questo metodo.
Test distilbert-NER
In assenza di modelli non LLM specializzati nel NER per riconoscere aziende, abbiamo deciso di testare il modello distilBERT-NER (https://huggingface.co/dslim/distilbert-NER), una versione fine-tuned per NER di distilBERT. distilBERT è una versione compressa di BERT, con risultati paragonabili, ma meno parametri, il che lo rende più leggero, rapido e efficiente.
Questo modello identifica 4 tipi di entità: location (LOC), organizations (ORG), person (PER), and Miscellaneous (MISC). Di queste, ci concentriamo su ORG in quanto le aziende dovrebbero corrispondere a questa categoria. Il suo fine-tuning è stato svolto sulla versione inglese del dataset CoNLL-2003 Named Entity Recognition dataset (https://www.aclweb.org/anthology/W03-0419.pdf), riconosciuto per la sua diversificata gamma di tipologie di entità.

I risultati sono stati migliori, soprattutto perché distilBERT sembrava in grado di riconoscere tutte le aziende all’interno dei COI statement, aggiungendo al limite tag aggiuntivi irrilevanti. Decidiamo quindi, dopo il test preliminare, di applicare distilbert-NER a tutto il nostro dataset di COI statements.

I risultati di tale estrazione sono dei file in formato json, in cui il PMID (numero identificativo dell’articolo) è la key, cui si associa un set contenente le entità di tipo ORG estratte dal COI statement dell’articolo corrispondente.

---

# Post-processing delle entità estratte

Alla fine dell’estrazione, i dati devono essere aggregati. In particolare sono necessarie due operazioni.
La prima dipende dalla forma dei testi dei COI statement, dal momento che autori diversi possono usare formulazioni diverse per riferirsi alla stessa azienda o ente. Per questo è necessario uniformare tali formulazioni.

La seconda dipende dalla performance del modello, siccome alcune estrazioni risultano scorrette e contengono dati rumorosi. Tali estrazioni evidentemente scorrette includono principalmente parole di pochi caratteri (forse sigle indicanti gli autori) e sostantivi che da soli non indicano specifiche aziende (come “Institute” o “Conflict”).
In base ai problemi evidenziati sopra, abbiamo svolto alcune operazioni di post-processing per eliminare il rumore dai nostri dati.

Per unificare i nomi delle organizations estratte, abbiamo per prima cosa rintracciato un dataset contenente le maggiori aziende farmaceutiche e il loro fatturato nei 30 giorni precedenti l’estrazione dei dati (https://companiesmarketcap.com/pharmaceuticals/largest-pharmaceutical-companies-by-market-cap/ estratto l’ultima volta il 18 luglio 2025).
Ipotizzando che molte tra le aziende presenti nei nostri NER match saranno presenti in questo dataset, usiamo questo set come riferimento. Per ognuna delle prime n aziende del companies marketcap dataset creiamo una regular expression che rintracci le possibili riformulazioni del nome. Applichiamo queste RegEx ai nostri match, per uniformare tutte le grafie di ogni azienda al nome ufficiale dell’azienda. Ad esempio, associamo all’azienda “Bristol-Myers Squibb” tutti i match corrispondenti alla RegEx '(bristol)? ?[-–]? ?myers?|squibb|bms'.

Escludendo i tag già associati alle aziende di cui sopra, applichiamo un ulteriore filtraggio dei tag restanti. In particolare, eliminiamo: (1) tutti i tag con un numero di caratteri minore o uguale a 2; (2) tutti i match che contengano un numero minore o uguale a 2 di caratteri alfabetici (ignorando i caratteri non alfabetici); (3) i tag con frequenza complessiva minore o uguale a 1000.


Dopo aver svolto il cleaning descritto nella sezione precedente, aggiungiamo manualmente delle RegEx per le aziende che sono presenti in questo nuovo elenco di tag e che non erano incluse nel dataset delle aziende farmaceutiche, inclusi alcuni enti pubblici. Inoltre modifichiamo il nostro metodo in modo che, quando un’azienda ne abbia acquisita un’altra entro il 2024, associamo ad essa tutti i tag dell’azienda acquisita. 
Il risultato di questo post-processing ai NER match ottenuti inizialmente vengono salvati in un dataframe che includa il PMID di ogni articolo associato a un set delle aziende.
