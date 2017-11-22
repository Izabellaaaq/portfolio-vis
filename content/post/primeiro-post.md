---
title: "Qual o máximo de volume que o açude de Boqueirão atingiu nos anos de 1990 a 1999? "
date: 2017-11-22T09:07:49-03:00
draft: false
---
 
Percebe-se que a maior média de volume atingido pelo Açude de Boqueirão foi no ano de 1992, com pouco mais de 90% de sua capacidade. No ano de 1990, o açude estava próximo dessa capacidade, porém em 1991 houve uma queda para quase 90%.

<!--more-->


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
  "mark": "bar",
  "width": 180,
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




