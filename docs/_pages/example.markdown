---
layout: default
title: "Home"
show_sidetoc: true
header_type: hero
header_img: assets/images/folium_map.webp
header_title: "You don't need to be coy, COI!"
subtitle: "Medical (European) Disclosure Survey"
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


# Introduction to the Project

You can use headings, paragraphs, and lists to structure the content effectively. This can be done using Markdown
syntax, which allows for easy formatting of text. For example, you can use **bold** or *italic* text to emphasize key
points, and you can create lists to organize information clearly.

This is an example of how to format the text in a way that is visually appealing and easy to read.
In this paragraph we use a `.lead` class to highlight the main points of the project.
{: .lead}

<p class="green"> 
    You can complete the entire page using only markdown syntax, but you can also use HTML tags to add more complex elements. In this example, we use a paragraph with a class of "green" to highlight the text in green color.
</p>

<p class="mt-3"><strong>The structure of the work is organised around key thematic areas:</strong></p>

<p>
The project framework is designed to offer an <strong>interdisciplinary approach</strong>, combining technical methodologies such as <strong>data analysis, machine learning, and artificial intelligence</strong> with broader considerations. The content is structured to alternate between <strong>theoretical guidance</strong> and <strong>practical exploration</strong>, encouraging users to apply concepts through hands-on development of a data-driven application or story.
</p>

<hr>

<p>
Throughout the development, you will engage with <strong>real-world datasets</strong>, explore <strong>data-driven narratives</strong>, and reflect on the <strong>ethical and social implications</strong> of your choices. The structure is designed to be modular, allowing flexibility while maintaining a coherent narrative flow.
</p>

<div class="full-width-wrapper">
<div class="where">
    <div class="container">
        <div class="row pt-2 ">
            <div class="col-md-6 col-sm-12">
               <img src="{{ site.baseurl }}/assets/images/Dr_Jekyll.jpg" alt="Project Visual">
            </div>
        <div class="col-md-6 col-sm-12">
            <h3>CONTEXT</h3>
            <p class="lead">This template is designed to be hosted on GitHub Pages and supports the development of project websites that combine technical insights with visual storytelling. You can adapt it to showcase datasets, code, visualizations, and final insights.
            </p>
            <h3>Getting Started</h3>
            <p>Use the provided structure to start editing your content using Markdown or HTML.</p>
            <p><strong>Refer to the documentation for details on how to customize layout, navigation, and visual elements.</strong></p>
        </div>
        </div>
    </div>
</div>
</div>

<div class="aim mt-5">
    <div class="container">
        <div class="row pt-2 ">
        <div class="col-md-6 col-sm-12">
            <h3>AIM OF THE TEMPLATE</h3>
                <p>
                The template is designed to support the development of data-intensive web projects, particularly those focused on <strong>research, education, or communication</strong>. Its goal is to provide a flexible, lightweight, and customizable framework that allows you to build a compelling narrative around your data.
                </p>
                <p>
                Whether you're documenting a case study, presenting findings from an analysis, or guiding users through an interactive application, this template encourages a balance between <strong>technical accuracy</strong> and <strong>accessible communication</strong>. You can customize each section to align with the structure of your project while maintaining consistency across pages.
                </p>
            </div>
            <div class="col-md-6 col-sm-12">
                <div class="project lead px-3 py-1">
                   <h3>Topics</h3>
                    <ul>
                        <li>Data Science</li>
                        <li>Artificial Intelligence</li>
                        <li>Machine Learning</li>
                        <li>Social Network Analysis</li>
                        <li>Data Governance</li>
                        <li>Disinformation</li>
                        <li>Information Dynamics</li>
                        <li>Social Dynamics</li>
                        <li>Political Dynamics</li>
                        <li>Large Language Models</li>
                        <li>Sustainable Development</li>
                        <li>Open Science</li>
                        <li>Data Altruism</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</div>

<br>

---

# How we support our ideas?

Using data visualizations is a powerful way to support your ideas and findings. In this template, you can easily
integrate visualizations created with Vega-Lite, a high-level grammar for interactive graphics.

<br>
