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

In a world that is growing continuously and exponentially—such as that of medical research—gaining an overarching view of certain aspects can be a daunting, if not impossible, task. Among these is the phenomenon of corporate involvement in research, which often hides behind the declaration of a <strong>Conflict of Interest (COI)</strong> associated with a publication.
We analyzed over one and a half million scientific articles and found that the share of publications with a declared COI statement rose <strong>from 20% to over 70% between 2017 and 2024</strong>, showing how its use is becoming increasingly common and (seemingly) transparent.

<strong>Does the rise in the number of articles correspond to an increased interest from companies?</strong>

<div style="height: 400px; width: 100%;">
  <iframe 
    src="/g2-2025-website/assets/charts/perc_empty_tagged.html"
    width="100%"
    height="100%"
    frameborder="0"
    style="border: none;"
    title="Percentuale_COI">
  </iframe>
</div>

<div style="height: 400px; width: 600px;">
  <iframe 
    src="/g2-2025-website/assets/charts/areas_empty_vs_tagged.html"
    width="100%"
    height="100%"
    frameborder="0"
    style="border: none;"
    title="Aree COI vuoto/non vuoto">
  </iframe>
</div>


Based on the data collected, the answer appears to be no. But if companies are so “selective,” in which fields are they more actively involved?
In this article, we aim to reconstruct the relationship between public and private entities on one side, and research on the other, through the analysis of public conflict of interest declarations associated with scientific articles (hereafter referred to as <em>COI statements</em>).

---

<h1 class="text-center">What's up, COI?</h1>

As illustrated by Enrico Granieri, Professor Emeritus of Neurology at the University of Ferrara, since the late 1980s medical research has paid increasing attention to the need for disclosing conflicts of interest when publishing scientific work. This requirement is driven primarily by publishers themselves, but also by ethics committees, which play a central role in overseeing matters related to medical practice and research.
<strong>How has one of the world’s largest open-access bibliographic databases—PubMed—adapted to these evolving needs?</strong>

Since 2017, the platform has allowed researchers to include a COI statement directly on the article’s page. This inclusion marks an important step in the direction highlighted by Prof. Granieri, as it provides a key new tool for the preliminary evaluation of a study—whether in research settings or clinical decision-making. However, it is not yet included in all articles. Our goal is to <strong>explore to what extent this publicly available data can help reconstruct the relationships between companies and research institutions—relationships</strong> that, by their nature, are often subject to political manipulation.

Clearly, the aim of our project is not to denounce a conflict of interest which, as mentioned above, is openly accessible to anyone visiting the PubMed website. Rather, our goal is to offer a perspective on the vast body of recent scientific literature—one that may inspire new research trajectories and help users navigate the overwhelming sea of publications.

---

<h1 class="text-center">Oh COI, where art thou?</h1>

<p> In an initial phase, we queried the PubMed database to retrieve all articles relevant to our investigation. The first obstacle we encountered was the actual possibility of isolating articles originating from the EU, including the United Kingdom and Switzerland.
On the other hand—especially when considering biomedical literature, which includes a large number of multicenter studies—one might expect research groups to exhibit moderate (if not high) geographical heterogeneity. In reality, as the chart shows, the situation appears to be quite different.</p>

<!-- Chart container with proper spacing -->
<div style="width: 600px; height: 500px; margin: 20px auto; overflow: hidden;">
  <vegachart 
    schema-url="/g2-2025-website/assets/charts/geo_distribution_chart.json"
    style="width: 100%; height: 100%; display: block;">
  </vegachart>
</div>

<p style="clear: both; margin-top: 20px;">We observed that around 65% of the articles show a high level of affiliation homogeneity, with all affiliations linked to a single European country. Another 20% include affiliations that are ambiguous at the national level—but can still be considered entirely European. Over 10% reflect ambiguity that goes beyond European borders, while less than 5% include at least one European author but are heavily skewed toward non-European affiliations. 

We therefore decided to assess the actual completion of the COI field; in this respect, the results appear to align with what one might expect.</p>


<div style="width: 1000px; height: 500px; margin: 10px auto; overflow: hidden;">
  <vegachart 
    schema-url="/g2-2025-website/assets/charts/COI_year.json"
    style="width: 100%; height: 100%; display: block;">
  </vegachart>
</div>

The overall increase in scientific output is accompanied by a marked rise in the number of articles with a declared COI statement, and a corresponding decline in the volume of articles where the COI field is left blank.

A similar trend can also be observed when looking at articles by country, considering only the ten most productive nations.


<div style="width: 1000px; height: 500px; margin: 10px auto; overflow: hidden;">
  <vegachart 
    schema-url="/g2-2025-website/assets/charts/trend_disclosure_eu_chart.json"
    style="width: 100%; height: 100%; display: block;">
  </vegachart>
</div>

Poland’s scientific output, in this regard, shows a percentage increase significantly above average. Notably, a high number of declared COIs can be observed across much of Eastern Europe (as well as Norway), as illustrated in the map below.

inserire mappa

From this perspective, Romania holds the record for the highest proportion of articles with a declared COI relative to its total scientific output published on PubMed—with over 65% of articles featuring a publicly available conflict of interest statement.

<div style="width: 900px; height: 500px; margin: 10px auto; overflow: hidden;">
  <vegachart 
    schema-url="/g2-2025-website/assets/charts/top10_disclosure_eu_chart.json"
    style="width: 100%; height: 100%; display: block;">
  </vegachart>
</div>

---

<h1 class="text-center">What did you major in, COI?</h1>

Once we obtained our dataset, the challenge was to classify the articles by medical discipline.
Within a timeframe of no more than ten years, hundreds of new diseases (think, for example, of COVID) have emerged, requiring innovative therapeutic approaches that do not fit into previous classifications. Another issue that cannot be overlooked is the lack of standardization in medical terminology.

However, our goal was not simply to reach the ‘leaves of the tree’, but rather to identify the ‘main branches’.

In a context where the redundancy of specific terms can be misleading, it is necessary to have a system capable of performing high-level abstraction. For this purpose, we leveraged the capabilities of MedGemma, an LLM developed by Google and specialized in medical texts.

Here are our initial results.

<div class="flourish-embed flourish-bar-chart-race" data-src="visualisation/24243729"><script src="https://public.flourish.studio/resources/embed.js"></script><noscript><img src="https://public.flourish.studio/visualisation/24243729/thumbnail" width="100%" alt="bar-chart-race visualization" /></noscript></div>
 
The chart dynamically displays the number of articles for the 10 most frequent medical areas. In this 'publication race', the rapid rise of the 'Infectious Disease' category can be observed, alongside 'Immunology', coinciding with 2020-2021. Nevertheless, scientific research on a topic of enduring interest remains predominant: oncology.
The surge in publications related to 'Immunology' and 'Infectious Disease' is even more evident in the following line plot. The chart shows, for each medical category, the year-over-year difference in the number of publications.


<div style="width: 1000px; height: 600px; margin: 10px auto; overflow: hidden;">
  <vegachart 
    schema-url="/g2-2025-website/assets/charts/increment_chart.json"
    style="width: 100%; height: 100%; display: block;">
  </vegachart>
</div>

In 2020, the number of publications concerning infectious diseases increased by almost 98%, and it is interesting to note that in the same year, the number of articles in the psychiatric field also nearly doubled (+84%). This data should also be interpreted as a possible effect of COVID-19 and the subsequent restrictions.

---

<h1 class="text-center">You don't know where your interest lies, COI...</h1>

But how can companies be linked to specific articles based on the COI statement? By applying a text processing model, we identified 121 companies and organizations with a significant presence in the publications under analysis.

immg

We were able to distinguish two classes of articles: on one side, those whose COI statement did not mention any company; on the other, those that did include one or more companies.

As shown in the chart below, the number of the latter—articles that explicitly mention a company in their COI—has grown steadily over the observed period, rising from about 10,000 in 2017 to nearly 35,000 in 2024. This increase may reflect the gradual adoption of this new PubMed feature.

<div style="height: 400px; width: 100%;">
  <iframe 
    src="/g2-2025-website/assets/charts/nb_tagged_articles_year.html"
    width="100%"
    height="100%"
    frameborder="0"
    style="border: none;"
    title="Aziende cit line">
  </iframe>
</div>


This trend appears to be proportional to the overall rise in publications containing a COI statement, which themselves increased rapidly over the period we analyzed—again pointing to the progressive integration of this feature into the PubMed platform.
However, the proportion between the two types of articles has remained relatively stable over the years: on average, only one out of ten COI statements actually mentions a company, while the remaining nine have “nothing to declare.”

But how are the 121 identified companies distributed across these articles?

As shown in the chart below, a small number of companies appear in the majority of articles, while many others are mentioned only occasionally.
In particular, the top five companies stand out for the sheer volume of articles they are cited in, whereas the frequency drops off quickly for the others: most companies appear in fewer than 5,000 articles, roughly one-tenth the number of the top five (5).

<div style="width: 100%; text-align: center;">
  <div style="display: inline-block; height: 400px; width: 100%; max-width: [your-desired-width]px;">
    <iframe 
      src="/g2-2025-website/assets/charts/company_freq_distrib_scatter.html"
      width="100%"
      height="100%"
      frameborder="0"
      style="border: none;"
      title="Aziende cit line">
    </iframe>
  </div>
</div>

In the chart below, we show the top companies by frequency. Notably, the top five companies each appear in nearly 25% of the articles in the dataset (with the leading company reaching 28% on its own). In fact, as the chart illustrates, more than 50% of the articles mention at least one of these top five companies.

<div style="width: 1000px; height: 600px; margin: 20px 100px 20px -100px ; overflow: hidden;">
  <vegachart 
    schema-url="/g2-2025-website/assets/charts/visualization.vl.json"
    style="width: 100%; height: 100%;">
  </vegachart>
</div>


<div style="width: 1000px; height: 350px; margin: 20px -100px 5px 100px ; overflow: hidden;">
  <vegachart 
    schema-url="/g2-2025-website/assets/charts/donut.json"
    style="width: 100%; height: 100%;">
  </vegachart>
</div>

---

<h1 class="text-center">That COI really tied the room together...</h1>

Once we identified the top companies mentioned in the processed COI statements, we conducted an initial analysis comparing their frequency with their revenue over the past 12 months.

<div style="width: 600px; height: 350px; margin: 10px auto; overflow: hidden;">
  <vegachart 
    schema-url="/g2-2025-website/assets/charts/scatter_tags_vs_revenues.json"
    style="width: 100%; height: 100%; display: block;">
  </vegachart>
</div>

Looking at the data for 51 of the companies considered, we can observe that the two variables appear to go relatively hand in hand: greater financial resources seem to correlate positively with greater involvement in research.

But how is corporate influence distributed across different medical fields as a whole?

{% include plotly-graph.html id="grafico2" file="sankey_azi_aree" height="600px" %}

In this chart, we can observe an almost perfect balance of interest in oncology, while neurology shows a clear dominance by Roche and Novartis.

---

<h1 class="text-center">And now… COInnect the nodes!</h1>


To more meaningfully capture the relationship between companies and research groups, we decided to also consider the citation network underlying the vast collection of articles at our disposal.

We built a graph designed to describe, as accurately as possible, the relationships between articles. Analyzing the structure of this graph naturally led to the identification of the most relevant research communities. Each community was labeled using a vector of five medical disciplines.

A clear example is the SARS-CoV community, represented by the vector
[‘Infectious Disease’, ‘Immunology’, ‘Pulmonology’, ‘Epidemiology’, ‘Virology’],
with over 71,000 articles (with declared COI), and a peak of more than 17,000 articles in 2021 (dropping to around 8,600 in 2024).

To assess corporate interest in more specific medical areas, we analyzed the percentage of occurrence of one or more companies within the COI statements associated with each community.


<div style="width: 1200px; height: 350px; margin: 10px auto; overflow: hidden;">
  <vegachart 
    schema-url="/g2-2025-website/assets/charts/perc_articoli_finan_comm.json"
    style="width: 100%; height: 100%; display: block;">
  </vegachart>
</div>

As shown in the chart, six communities exceed the threshold of 20% of articles that mention at least one company in their COI statement.

Here too, as we did for the medical fields, we decided to examine the influence of the companies most actively involved in these specific communities.


{% include plotly-graph.html id="grafico3" file="sankey_comm_az.html" height="600px" %}

Here again, the ubiquitous Novartis and AstraZeneca make an appearance, but there is also room for relatively smaller companies such as the Italian Chiesi Pharmaceuticals, which—as shown in the chart—supports a considerable number of influential articles within Community 17.

However, as we observed in the previous Sankey diagram (which mapped companies to medical fields), the contribution of companies within research communities appears fairly balanced, despite some notable and interesting differences. 

It seems reasonable to assume that companies do not favor one medical area over another, but rather distribute their involvement quite evenly across the entire research landscape.
So how can we interpret the relationship we’ve analyzed so far in a more meaningful way?
The key insight comes directly from the definition of the communities themselves. These communities do not simply represent a more granular and concrete modeling of the medical taxonomy introduced earlier.
By aggregating the information contained in the titles of the most heavily supported communities, and visualizing it through carefully refined word clouds, something very interesting begins to emerge.

In conclusion, it appears that research communities do not emerge simply from the proximity between medical fields, but rather align with established research traditions focused on specific groups of diseases or disorders.
Likewise, corporate interest in these communities should be understood in this light: there is a clear preference for chronic conditions that require ongoing treatment and care.

<ul>
  <li>Community 8: Heart failure / Diabetes</li>
  <li>Community 17: Cystic fibrosis / Chronic obstructive pulmonary disease</li>
  <li>Community 19: Fatty liver disease / Hepatitis / Hepatocellular carcinoma</li>
  <li>Community 22: Rheumatoid arthritis / Atopic dermatitis / Spondyloarthritis</li>
  <li>Community 32: Sleep apnea / Migraine / Botulinum toxin / Bruxism</li>
  <li>Community 33 : Rare genetic diseases (Fabry, Von Willebrand)</li>
</ul>


We discussed these findings with Dr. Carmen Barbato (Neurology, Santa Maria Annunziata Hospital, Florence), Dr. Alessandro Sodero (Neurologist and researcher at the IRCCS in Florence), and Prof. Enrico Granieri.

In discussing the composition of diseases within the various communities, it emerged that—for at least some of them—a physiopathological rationale can be identified.

Community 32, in particular, brings together articles that cover medical categories which, at first glance, may seem quite distant from one another (Neurology, Dentistry, Coronary Disease).
However, a possible common thread among these conditions is Obstructive Sleep Apnea Syndrome (OSAS)—a disorder characterized by snoring and nighttime apneas, which can lead to bruxism (the involuntary grinding of teeth, a dental issue sometimes treated with botulinum toxin injections), as well as hypertension, coronary problems, and most notably, migraine and headache.

We believe that the discovery of such clearly defined and distinct communities deserves further exploration and input from experts within each respective domain.

What seems evident is that these communities tend to form around groups of diseases characterized primarily by multi-dimensional complexity, and by the need for collaboration between research teams across different medical fields. 

---

This study has shown that the adoption of COI statements is a steadily growing phenomenon.
We identified a consistent upward trend, and it is reasonable to expect that in the near future, their use will become ubiquitous.

We analyzed the frequency with which the main companies appear in COI declarations and found that, especially for the largest corporations, their presence tends to be evenly distributed across different medical disciplines.

Moreover, it appears that the percentage of articles with private sector support has not increased over the years.

After analyzing variations within specific medical categories, we can say that exogenous shocks—such as COVID—have a significant impact on the rate of scientific production.
In this context, we observed that using the number of scientific publications as a proxy for research quality can be misleading, especially given the ever-growing volume of articles.

This study highlights that, within the PubMed network, there exist communities of articles—and therefore of research institutions, scientists, and scholars—that are highly interconnected around pathologies characterized by multi-dimensional complexity or multimorbidity, whose nature still requires further characterization.













