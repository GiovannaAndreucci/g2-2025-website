---
layout: default
title: Medical area extraction
header_title: "Medical area extraction"
header_type: hero #base, post, hero,image, splash
header_img: assets/images/dict.png
---

To assign a medical discipline to each article in the dataset, we leveraged the capabilities of a generative AI system specialized in medical text, published by Google in May 2025, MedGemma 4B (<a href="https://medgemma.org/" style="color:#222; text-decoration:underline;">https://medgemma.org/</a>). MedGemma 4B is a large language model (LLM, 4 billion parameters) optimized for biomedical and scientific domains, capable of semantic abstraction and contextual classification. Its main strength lies in going beyond the analysis of individual keywords, capturing the context of the entire abstract and providing a classification consistent with the actual content of the text.

# Model details
Size: 4 billion parameters, trained on a large corpus of biomedical and scientific texts.
Architecture: transformer, with native support for “chat” prompts and advanced contextual understanding.
Features: discipline classification, extraction of medical concepts, question answering, robustness on mixed texts.
Efficiency: the 4B version allows fast inference even on GPUs with limited memory, thanks to 4-bit quantization.

# Operational steps of the pipeline

<strong>Pre-processing</strong>:  
For each article, title, abstract, keywords, and journal were aggregated into a single text, following a predefined priority.

<strong>Batch inference</strong>:  
Articles were processed in batches optimized for GPU memory, leveraging quantization to reduce resource usage.

<strong>Prompting</strong>:  
For each text, the model receives a specific prompt instructing it to reply exclusively with the name of the main medical discipline.

<strong>Checkpoint management</strong>:  
An automatic checkpoint system was implemented to handle large datasets and enable resumption in case of interruptions.

<strong>Validation saving</strong>:  
Results are progressively saved in temporary files and, at the end, in the final file that associates each article with the extracted discipline.

This approach enabled efficient and scalable extraction of the main medical discipline characterizing each article, allowing for aggregate analyses of predominant research areas and correlations with other dataset variables.
