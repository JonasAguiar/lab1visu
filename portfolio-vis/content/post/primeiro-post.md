---
title: "No racionamento"
date: 2017-11-14T14:44:11-03:00
draft: false
---

<div id="vis" width=200></div>

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
    "property": "volumes",
    "parse": {
        "DataInformacao": "utc:'%d/%m/%Y'"
            }
        }
    },

"width": 1000,
"height": 500,
"layer": [{
  "data": {
    "url": "https://api.insa.gov.br/reservatorios/12172/monitoramento",
    "format": {
    "type": "json",
    "property": "volumes",
    "parse": {
        "DataInformacao": "utc:'%d/%m/%Y'"
            }
        }
    },

"mark": {
    "type": "area",
    "interpolate": "monotone",
    "color": "#81DAF5"
},
"selection": {
  "brush": {"type": "interval", "encodings": ["x"]}
},
"encoding": {
  "x": {
    "timeUnit" : "daymonthyear",
    "field": "DataInformacao",
    "type": "temporal",
    "axis": {"format": "%B/%Y", "title" : "Volume percentual em decorrer dos anos"}
   },
  "y": {
    "field": "VolumePercentual",
    "type": "quantitative",
    "axis": {"tickCount": 30, "grid": false, "title": "Volume percentual"}
     }
   }, "transform" : [{"filter": {"field": "DataInformacao", "range": [{"year": 2014, "month": "dec", "date": 6}, {"year": 2017, "month": "aug", "date": 26}] }}]



},{
"data": {
  "values": [
    {"y" : 8.2}

]

},

"mark": "rule",
"encoding": {
  "y": {
    "field": "y",
    "type": "quantitative"
},
"color": {"value": "red"},
"size": {"value": 3}
            }
        }
    ]
};
  	vegaEmbed('#vis', spec).catch(console.warn);
</script>
