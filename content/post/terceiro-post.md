---
title: "3° Visualização: algo que não lembro 2 "
date: 2017-11-22T09:07:49-03:00
draft: false
---

<!--more-->


<div id="vis" width=300></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/vega/3.0.7/vega.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-lite/2.0.1/vega-lite.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/3.0.0-rc7/vega-embed.js"></script>
<script>
    const spec = {
    "$schema": "https://vega.github.io/schema/vega-lite/v2.json",
  "data": {
    "url": "https://api.insa.gov.br/reservatorios/12172/monitoramento",
    "format": {
      "type": "json",
      "property": "volumes"
    }
  },
  "mark": "bar",
  "encoding": {
    "x": {
      "timeUnit": "yearmonth",
      "field": "DataInformacao",
      "type": "temporal",
      "axis": {
        "title": "Mês/Ano"
      }
    },
    "y": {
      "aggregate": "mean",
      "field": "VolumePercentual",
      "type": "quantitative",
      "axis": {
        "title": "Volume Percentual (%)"
      }
    }
  }

     };
  	vegaEmbed('#vis', spec).catch(console.warn);
</script>




