# Defensa civil en LATAM

## Wikidata:WikiProject Civil Defense
* https://www.wikidata.org/wiki/Wikidata:WikiProject_Civil_Defense

## LATAM
- Latin America (Q12585) https://www.wikidata.org/wiki/Q12585

```sparql
SELECT ?country_in_latam ?country_in_latamLabel WHERE {
  wd:Q12585 wdt:P527 ?country_in_latam.
  
  # FIXME: this is returning South America and other regions
  # wd:Q12585 wdt:P527 ?country_in_latam ;
  #           wdt:P31 wd:Q6256 .
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}
```

## wikipedia en español
- https://es.wikipedia.org/wiki/Protecci%C3%B3n_civil

## Wikipédia Lusófona
- https://pt.wikipedia.org/wiki/Categoria:Defesa_civil
- https://pt.wikipedia.org/wiki/Defesa_civil_no_Brasil
- https://pt.wikipedia.org/wiki/Centro_Nacional_de_Gerenciamento_de_Riscos_e_Desastres
- Historia:
  -  https://pt.wikipedia.org/w/index.php?title=Defesa_civil_no_Brasil&type=revision&diff=63566864&oldid=63566838&diffmode=source


## Wikidata

### Defesa civil no Brasil
```sparql
# https://w.wiki/5v2d
# emergency management (Q1460420) + government agency (Q327333) + Brasil (Q155)
SELECT DISTINCT ?item ?itemLabel ?operating_areaLabel ?official_website WHERE {
  ?item wdt:P101 wd:Q1460420;
    (p:P31/ps:P31/(wdt:P279*)) wd:Q327333;
    wdt:P17 wd:Q155.
  OPTIONAL { ?item wdt:P2541 ?operating_area. }
  OPTIONAL { ?item wdt:P856 ?official_website. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,de,fr,ru,es,ja,zh,ar". }
}
ORDER BY ?operating_areaLabel
```

## TODO/FIXME
- Colombia
  - http://www.defensacivil.gov.co/
- Equador
  - https://www.gestionderiesgos.gob.ec/
- El Salvador
  - https://www.proteccioncivil.gob.sv/
- Mexico
  - https://es.wikipedia.org/wiki/Protecci%C3%B3n_civil#M%C3%A9xico_2
- Peru
  - https://es.wikipedia.org/wiki/Instituto_Nacional_de_Defensa_Civil
    - https://www.wikidata.org/wiki/Q5917500
- Venezuela
  - https://www.pcivil.gob.ve/

## TODO / REMOVE

### Wikidata Continents, countries, regions and capitals

```sparql
# @see https://linkedwiki.com/query/wikidata_Continents,_countries,_regions_and_capitals?lang=EN
PREFIX bd: <http://www.bigdata.com/rdf#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wikibase: <http://wikiba.se/ontology#>

#defaultView:Tree
SELECT ?continent ?continentFlag ?continentLabel ?country ?countryLabel ?countryFlag ?region ?regionLabel ?regionFlag ?city ?cityLabel ?cityImage ?property ?propertyLabel ?value ?valueLabel WHERE {
  {
    SELECT * WHERE {
      ?continent wdt:P31 wd:Q5107.
      ?country wdt:P30 ?continent.
      ?country wdt:P31 wd:Q6256.
      ?country wdt:P150 ?region.
      OPTIONAL {
        ?continent wdt:P242 ?continentFlag.
        ?country wdt:P41 ?countryFlag.
        ?region wdt:P41 ?regionFlag.
      }
      OPTIONAL {
        ?region wdt:P36 ?city.
        ?city wdt:P31 wd:Q515.
        ?city wdt:P18 ?cityImage.
        OPTIONAL {
          VALUES (?prop) {
            (wdt:P1082)
            (wdt:P6)
            (wdt:P190)
            (wdt:P31)
            (wdt:P571)
            (wdt:P150)
            (wdt:P206)
            (wdt:P527)
          }
          ?city ?prop ?value.
          ?property ?ref ?prop.
          ?property rdf:type wikibase:Property.
        }
      }
    }
  }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```