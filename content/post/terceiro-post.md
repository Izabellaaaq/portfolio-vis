---
title: "Maior queda de percentual do Açude de Boqueirão"
date: 2017-11-22T09:07:49-03:00
draft: false
---

De acordo com os dados analisados, percebe-se que a maior queda de percentual do açude de Boqueirão foi entre 2011 até os dias atuais. Onde, o mesmo tinha 90% de sua capacidade em 2011 e foi caindo aos poucos, chegando a cerca de 8% de volume médio. Lembrando que nos últimos dois anos, tivemos racionamento e em 2017 a chegada das águas do Rio São Francisco por meio da transposição. 


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
  "mark": "area",
  "width": 600,
  "height": 400,
 "transform": [
    {
      "filter": {
        "timeUnit": "year",
        "field": "DataInformacao",
        "range": [
          2010,
          2017
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



