---
layout: default
title: Dashboard Analisi Dati
graph_file: grafico1.html
plotly: true
---

<!-- 
  Uso: {% include plotly-graph.html id="grafico1" file="grafico1.html" height="500px" %}
  
  Parametri:
  - id: ID del div contenitore (obbligatorio)
  - file: nome del file HTML con il grafico (obbligatorio)
  - path: percorso personalizzato (default: /assets/charts/plotly/)
  - height: altezza del grafico (default: 500px)
  - width: larghezza del grafico (default: 100%)
  - class: classi CSS aggiuntive (opzionale)
-->


# Dashboard Analisi Dati

{% include plotly-graph.html id="grafico1" file="grafico1.html" height="600px" %}