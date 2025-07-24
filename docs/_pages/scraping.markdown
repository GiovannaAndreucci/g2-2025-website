---
layout: default
title: Scraping e Geolocalization
header_title: "Scraping e Geolocation"
header_type: hero #base, post, hero,image, splash
header_img: assets/images/geocut.png
---

# Scraping

Through the Entrez API (the search engine used by the most important biomedical literature databases), it was possible to query the PubMed database to retrieve all articles relevant to our investigation (namely, those with at least one European affiliation in the list of affiliations). The first challenge concerned the actual possibility of isolating articles originating from the EU, with the addition of the United Kingdom and Switzerland: from what perspective can an article be considered European based solely on the authors’ affiliations?


# Geographical Definition

Within the project, this section serves as a component for analyzing articles examined on PubMed from 2017 to 2024. The aim is to identify patterns in relation to three dimensions under consideration: geographical affiliation, COI disclosure, and the presence of explicitly declared companies.

The first part of the pipeline is dedicated to creating a geographical dataset by aggregating scientific articles and assigning nationalities based on information contained in the affiliations.

A hybrid approach was used for country inference, consisting of:

<ul>
  <li>Direct textual matching on country names</li>
  <li>Heuristic dictionaries for recurring cities and institutions</li>
  <li>Country normalization</li>
</ul>

This led to an initial classification into 4 categories:

<strong>Eu</strong>: articles from a single European nation

<strong>Non Eu</strong>: articles from a single non-European nation

<strong>Ambiguous</strong>: articles with more than one nation

<strong>Unknown</strong>: articles not covered by the classification

For ambiguous cases, a further subdivision was made into European, non-European, and mixed nationalities; in parallel, for unclassified cases, a Spacy model was applied to extract geographical units (GPE) and update dictionaries for assignment.

This enabled the following classification:

eu  2144703
ambiguous_all_eu   672667
ambiguous_mixed   380531
non-eu    54942
unknown    21652
ambiguous_all_non_eu     2117

Subsequently, further analysis and cleaning of the global dataset were performed, from removing duplicates to filtering only European papers and their graphical representation. Starting from the creation of the geographic map using plotly, the percentage of articles with COI, the ranking of countries by number of scientific publications, the ranking of countries with the highest percentage of papers presented with COI, and the trend of disclosures of individual countries over the years.

The next step was to merge the geographical dataset thus created with the semantic dataset containing the semantic tags of companies and the extraction of various medical disciplines using MedGemma. The merge was performed using the unique PMID identifier of the article. This enabled concatenation of the last portion of the pipeline.

<strong>Further Analysis</strong>
In this final section, we aim to verify whether statistically significant geographical concentrations exist between specific companies and specific countries.

The procedure was carried out as follows:

<strong>Selection of companies of interest</strong>:  
The subset of companies that together constitute 95% of the overall corporate presence in the dataset was selected. This threshold serves to exclude low-frequency outliers and reduce statistical noise in the final matrix. The result led to analyzing a subset representing 10.24% of the total articles with COI.

<strong>Construction of the contingency table</strong>:  
A company-by-country matrix was constructed, in which each cell represents the number of articles in which that specific company is associated with that specific nation.

<strong>Independence test and residual analysis</strong>:  
A chi-square test was applied to assess the null hypothesis of independence between company and country. Subsequently, standardized residuals for each cell were calculated to identify combinations with the greatest deviation from the expected frequency.

The chi-square test confirmed a strong dependence between companies and countries (Chi2 = 12115.787, dof = 266, p-value < 1e-300).  
Subsequently, standardized residuals were calculated for each cell in the matrix. To assess point significance, a filter based on the threshold |r| > 1.96 was applied, corresponding to a 95% confidence level (p < 0.05) under the assumption of a standard normal distribution. This highlights which specific combinations show deviations significantly above (or below) the expected frequency, producing the following table of the top 10 results:

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

The listed values indicate a much higher presence than expected based on the marginal distribution of frequencies, confirming editorial concentration patterns consistent with the geographical location of the company or its strategic area of influence. Although the standardized residuals correct for marginal sizes (i.e., they account for the total volume of articles per company and per country), the assumption of independence remains theoretically strong and may not fully capture more complex underlying dynamics such as editorial agreements, multinational strategies, or historical and institutional effects.