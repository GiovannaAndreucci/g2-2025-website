---
layout: default
title: Company Extraction
header_title: "Company Extraction"
header_type: hero #base, post, hero,image, splash
header_img: assets/images/hippocut2.png
---

In order to analyze the companies in the COI statements, we had to extract them using NER techniques.

First, we tried using SpaCy. However, the results appeared very imprecise, with a large number of incorrect matches. For this reason, we discarded this method.

In the absence of non-LLM models specialized in NER for recognizing companies, we decided to test the distilBERT-NER model (https://huggingface.co/dslim/distilbert-NER). This is a NER fine-tuned version of distilBERT. which is a compressed version of BERT, with comparable results but fewer parameters, making it lighter, faster, and more efficient.

This model identifies 4 types of entities: location (LOC), organizations (ORG), person (PER), and Miscellaneous (MISC). Among these, we focus on ORG, as companies should fall under this category. The model’s fine-tuning was performed on the English version of the CoNLL-2003 Named Entity Recognition dataset (https://www.aclweb.org/anthology/W03-0419.pdf), known for its diverse range of entity types. The results were better, mainly because distilBERT appeared capable of recognizing all the companies within the COI statements, at most adding some irrelevant extra tags. Therefore, after preliminary testing, we decided to apply distilBERT-NER to our entire dataset of COI statements.

The output of this extraction consists of a JSON file, where the PMIDs (article identifier number) are the keys, associated with a set containing the extracted ORG-type entities from the corresponding article's COI statement as values.


---

# Post-processing of the extracted entities

After the extraction of the companies, two main operations were needed.

The first depends on the structure of the COI statement texts, as different authors may use varying formulations to refer to the same company or entity. Therefore, it is necessary to standardize these formulations. The second depends on the model's performance, as some extractions are incorrect and contain noisy data. These erroneous extractions mainly include very short words (possibly acronyms indicating authors) and nouns that do not refer to specific companies (such as "Institute" or "Conflict").

Based on the issues highlighted above, we performed some post-processing operations to clean the noise from our data.

To standardize the names of the extracted organizations, we first identified a dataset containing the largest pharmaceutical companies and their marketcap in the 30 days preceding data extraction (https://companiesmarketcap.com/pharmaceuticals/largest-pharmaceutical-companies-by-market-cap/ , last retrieved on July 18, 2025). 

Assuming that many of the companies in our NER matches would also appear in this dataset, we used it as a reference. For each of the top 40 companies in the Companies MarketCap dataset, we created a regular expression to capture possible variations of their names. We then applied these RegEx patterns to our matches to standardize all spellings of each company to its official name. For example, we assigned all matches corresponding to the RegEx r“(bristol)? ?[-–]? ?myers?|squibb|bms” to the company "Bristol-Myers Squibb". This approach ensured consistent naming across different formulations of the same organization in the COI statements.

For the remaining tags not associated with the pharmaceutical reference set, we implemented additional filtering criteria:

* we removed all tags containing ≤2 characters,
* we eliminated matches with ≤2 alphabetical characters (non-alphabetical characters disregarded), and
* we excluded tags appearing ≤1000 times in total.

Following this automated cleaning process, we manually supplemented our standardization approach. To do this, first we added custom regex patterns for significant entities (including public institutions) that appeared in our filtered results but weren't in the pharmaceutical reference set; then we implemented acquisition-aware mapping, where all mentions of companies acquired by 2024 were automatically associated with their parent organizations.
The final output of this post-processing pipeline was structured as a dataframe where each row had a PMID column and a column with the set of standardized company names associated with that article's COI statement.

By using the same RegEx patterns defined during the post-processing, we were able to identify 51 matches in 3 different datasets and retrieve the revenues ttm of those companies (https://companiesmarketcap.com/pharmaceuticals/largest-pharmaceutical-companies-by-revenue/, https://companiesmarketcap.com/healthcare/largest-healthcare-companies-by-revenue/, https://bullfincher.io/ranking/top-medical-device-companies-in-the-world-by-revenue, last downloaded on July 21, 2025). We calculated the Pearson correlation coefficient between the frequency of the companies tags and their revenues, obtaining a value of 0.83, associated with a p-value of 2.8e-14. 

