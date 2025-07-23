---
layout: default
title: Estrazione aree mediche
header_title: "Estrazione aree mediche"
header_type: hero #base, post, hero,image, splash
header_img: assets/images/dict.png
---

Per attribuire una disciplina medica a ciascun articolo del dataset, abbiamo sfruttato le potenzialità di un sistema AI generativo specializzato in testo medico, pubblicato da Google a maggio 2025, MedGemma 4B (https://medgemma.org/). MedGemma 4B è un modello di linguaggio di grandi dimensioni (LLM, 4 miliardi di parametri) ottimizzato per il dominio biomedico e scientifico, capace di astrazione semantica e classificazione contestuale. La sua forza principale consiste nel non limitarsi all’analisi di singole parole chiave, ma di cogliere il contesto dell’intero abstract, restituendo una classificazione coerente con il contenuto reale del testo.

# Dettagli sul modello
Dimensione: 4 miliardi di parametri, addestrati su un ampio corpus di testi biomedici e scientifici.
Architettura: transformer, con supporto nativo per prompt “chat” e comprensione contestuale avanzata.
Funzionalità: classificazione di discipline, estrazione di concetti medici, question answering, robustezza su testi misti.
Efficienza: la versione 4B consente inferenza rapida anche su GPU con memoria limitata, grazie alla quantizzazione a 4-bit.

# Step operativi della pipeline

<strong> Pre-processing </strong>:
Per ciascun articolo, sono stati aggregati titolo, abstract, keywords e journal in un unico testo, seguendo una priorità predefinita.

<strong> Batch inference </strong>:
Gli articoli sono stati processati in batch ottimizzati per la memoria GPU, sfruttando la quantizzazione per ridurre l’utilizzo di risorse.

<strong> Prompting </strong>:
Il modello riceve, per ciascun testo, un prompt specifico che lo istruisce a rispondere esclusivamente con il nome della disciplina medica principale.

<strong> Gestione checkpoint </strong>:
È stato implementato un sistema di checkpoint automatici per gestire dataset di grandi dimensioni e consentire la ripresa dell’elaborazione in caso di interruzioni.

<strong> Salvataggio validazione </strong>:
I risultati vengono salvati progressivamente in file temporanei e, al termine, nel file finale che associa a ciascun articolo la disciplina estratta. 

Questo approccio ha permesso di estrarre in modo efficiente e scalabile la disciplina medica caratterizzante di ciascun articolo, abilitando analisi aggregate sulle aree di ricerca prevalenti e sulle correlazioni con altre variabili del dataset.
