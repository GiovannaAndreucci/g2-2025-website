---
layout: default
title:  "Grafo e Community"
subtitle: ""
header_type: hero #base, post, hero,image, splash
header_img: assets/images/body_graph.jpg
header_title: "Grafo e Community"
vega: false
---
Regarding the graph, we used the PubMed API to download all articles citing a publication from our dataset. We then filtered these to retain only those already present in the European dataset.

Using the NetworkX library, we built a directed graph where nodes represent articles and edges represent citations. More specifically, we oriented edges from the cited document to the citing one, so that an edge represents the flow of information. With this convention, *the out-degree of a node corresponds to the number of citations received by an article.*


We then focused on the giant component (GC) of the graph, which comprises about 98% of the nodes. 

<ul>
  <li> On the GC we calculated the out–out assortativity to assess whether highly cited articles tend to be cited by other highly cited ones. As might be expected, the result was approximately 0.0063, suggesting that highly cited articles do not systematically cite each other, but neither are they cited exclusively by low-citation articles — there is a mix of cross-citation between highly and lowly cited papers.
</li>
  <li>We also calculated the in–in assortativity to see whether articles that cite many others tend to cite other articles that themselves cite a lot. This value turned out to be 0.18, indicating a homophilic tendency — in other words, papers that cite many references tend to cite others that are similarly rich in references.
</li>
  <li>We computed both the local and global clustering coefficients, which were 0.054 and 0.0068 respectively. These low values suggest that citations do not concentrate in closed, tightly-knit groups but rather are spread in a more radial or acyclic manner.
</li>
</ul>

We then used the graph structure to extract communities, corresponding to clusters of articles on specific topics. Initially, we attempted to apply the Girvan–Newman algorithm, but this approach was infeasible due to the graph’s large size. We therefore chose the *Leiden algorithm*, which maximizes modularity to find densely connected clusters, typically corresponding well to groups of related articles. Additionally, Leiden is both faster and more accurate than its predecessor, Louvain, especially on large, sparse graphs.
 
<strong>Limitations of Leiden:</strong>
 Leiden relies on modularity, and thus may overlook small communities if they do not significantly improve the modularity score (resolution limit), potentially merging distinct communities into one larger group. Moreover, Leiden includes randomization, meaning slightly different results may occur with each run unless a random seed is fixed.
After running Leiden, we obtained 135 communities, and focused on the most populated ones (with >100 articles). For each, we calculated the percentage of funded articles, and selected for further analysis the communities where at least 20% of articles received funding.
For these 6 communities, we extracted the specific medical domains or diseases via word clouds, and identified the most frequent companies, in order to analyze how companies and their areas of influence are distributed across communities. The results of this analysis are shown in the Sankey diagrams.

<strong>Further analysis:<strong>
From the graph, we observed that funded articles receive, on average, 2 more citations than those without funding:
<ul> <li> Average citations per article (unfunded): 3.65</li>
<li>Average citations per article (funded): 5.77</li>



