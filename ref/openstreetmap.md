# OpenStreetMap

```sparql
SELECT DISTINCT ?item ?itemLabel WHERE {
  ?item p:P31/ps:P31/wdt:P279* wd:Q56695738 .
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}

```

[Run it on Wikidata](https://query.wikidata.org/#SELECT%20DISTINCT%20%3Fitem%20%3FitemLabel%20%3Fcoord%20%3FcountryLabel%20%3FshortCountry%20%3Fcity%20%20WHERE%20%7B%0A%20%20%3Fitem%20p%3AP31%2Fps%3AP31%2Fwdt%3AP279%2a%20wd%3AQ56695738%20.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0A)
