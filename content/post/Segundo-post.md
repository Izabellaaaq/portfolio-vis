---
title: "Mínimo de volume do Açude de Boqueirão entre os anos de 1990 e 1999."
date: 2017-11-22T09:07:49-03:00
draft: false
---

<!--more-->

No intervalo de 1990  a 1999, a mínimo de volume foi no ano 1998, caiu de pouco mais de 80% em 1997 para cerca de 30% em 1998. Uma queda considerável de sua capacidade.


<div id="vis" width=300></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vega/3.0.7/vega.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-lite/2.0.1/vega-lite.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/3.0.0-rc7/vega-embed.js"></script>
<script>
    const spec = {
    "$schema": "https://vega.github.io/schema/vega-lite/v2.json",
  "data": {
      "url":"https://api.insa.gov.br/reservatorios/12172/monitoramento",
      "format": {
          "type": "json",
          "property": "volumes",
          "parse": {"DataInformacao": "utc:'%d/%m/%Y'"}
      }
  },
  "mark": "line",
  "width": 600,
 "transform": [
    {
      "filter": {
        "timeUnit": "year",
        "field": "DataInformacao",
        "range": [
          1990,
          1999
        ]
      }
    },
    {
      "filter": {
        "timeUnit": "month",
        "field": "DataInformacao",
        "range": [
          6,
          7
        ]
      }
    }
  ],
  
"encoding": {
  "x": {
    "timeUnit": "year",
    "field": "DataInformacao",
    "type": "temporal",
    "axis": {"title": "Anos"}
  },
  "y": {
    "aggregate": "mean",
    "field": "VolumePercentual",
    "type": "quantitative",
    "axis": {"title": "Média do volume (%)"}
  }
}

     };
  	vegaEmbed('#vis', spec).catch(console.warn);
</script>




