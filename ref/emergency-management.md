# emergency-management

> Work in progress. Ignore for now (Rocha, 2022-10-22)

<!--
- https://www.wikidata.org/wiki/Q10427676
- https://wiki.openstreetmap.org/wiki/User:EmericusPetro/sandbox
- https://pandoc.org/try/
-->


<!-- TOC depthfrom:2 -->

- [emergency management](#emergency-management)
- [related general concepts](#related-general-concepts)
- [organizations](#organizations)
- [TODO](#todo)

<!-- /TOC -->

## emergency management

## related general concepts

```yaml

# https://www.wikidata.org/wiki/Q852008
- conceptum: /civil protection/@eng-Latn
  nomen:
    eng-Latn: civil protection
  wikidata: Q852008
  comprehendit:

    # https://www.wikidata.org/wiki/Q10427676
    - conceptum: /civil defense/@eng-Latn
      wikidata: Q10427676
      nomen:
        eng-Latn: civil defense
        spa-Latn: defensa civil
        por-Latn: defesa civil

    # https://www.wikidata.org/wiki/Q1460420
    - conceptum: /emergency management/@eng-Latn
      wikidata: Q1460420
      nomen:
        eng-Latn: emergency management
        spa-Latn: administración de desastres
        por-Latn: gestão de emergências
```

## organizations 

```sparql
# organizations: field of work = emergency management
SELECT ?item ?label ?country ?_image WHERE {
  ?item wdt:P101 wd:Q1460420.
  SERVICE wikibase:label {
    bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,es,pt,de".
    ?item rdfs:label ?label.
  }
  OPTIONAL { ?item wdt:P18 ?_image. }
  OPTIONAL { ?item wdt:P17 ?country. }
  # OPTIONAL { ?item wdt:P1448 ?official_name. }
}
LIMIT 1000
```

[Try it on Wikidata Query Service](https://query.wikidata.org/#%23%20organizations%3A%20field%20of%20work%20%3D%20emergency%20management%0ASELECT%20%3Fitem%20%3Flabel%20%3Fcountry%20%3F_image%20WHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP101%20wd%3AQ1460420.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%0A%20%20%20%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%2Ces%2Cpt%2Cde%22.%0A%20%20%20%20%3Fitem%20rdfs%3Alabel%20%3Flabel.%0A%20%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3F_image.%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP17%20%3Fcountry.%20%7D%0A%20%20%23%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP1448%20%3Fofficial_name.%20%7D%0A%7D%0ALIMIT%201000)


## TODO
- As 2022-10-22, several governmental organizations are still not labeled as field of work = emergency management. We need to improve this topic
- The SPARQL query still returning people (however it would be necessary fix all items to be governmental organizations before "fix" it)