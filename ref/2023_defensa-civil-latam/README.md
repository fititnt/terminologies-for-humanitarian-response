# Defensa civil en LATAM

> - WikiProject Civil Defense https://www.wikidata.org/wiki/Wikidata:WikiProject_Civil_Defense
> - See <https://www.wikidata.org/wiki/Wikidata:WikiProject_Civil_Defense/List_of_emergency_management_governmental_agencies/LATAM>

## Wikidata SPARQL

### Defensa civil en LATAM + Caribe

```sparql
# Defensa civil en LATAM + Caribe
# https://w.wiki/6LmU
SELECT DISTINCT ?item ?itemLabel ?country ?countryLabel ?operating_areaLabel ?official_website WHERE {
  VALUES ?in_latam {
    wd:Q77
    wd:Q96
    wd:Q155
    wd:Q241
    wd:Q298
    wd:Q414
    wd:Q419
    wd:Q717
    wd:Q733
    wd:Q736
    wd:Q739
    wd:Q750
    wd:Q774
    wd:Q783
    wd:Q786
    wd:Q790
    wd:Q792
    wd:Q800
    wd:Q804
    wd:Q811
    wd:Q1183
    wd:Q25228
    wd:Q781
    wd:Q244
    wd:Q242
    wd:Q25305
    wd:Q784
    wd:Q769
    wd:Q766
    wd:Q13353
    wd:Q13353
    wd:Q763
    wd:Q760
    wd:Q757
    wd:Q730
    wd:Q778
    wd:Q754
    wd:Q18221
  }
  ?item wdt:P101 wd:Q1460420;
    (p:P31/ps:P31/(wdt:P279*)) wd:Q327333;
    wdt:P17 ?in_latam.
  OPTIONAL { ?item wdt:P17 ?country. }
  OPTIONAL { ?item wdt:P2541 ?operating_area. }
  OPTIONAL { ?item wdt:P856 ?official_website. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,de,fr,ru,es,ja,zh,ar". }
}
ORDER BY (?countryLabel) (?operating_areaLabel)
```

<!--
## Notas temporárias


### Wikidata SPARQL (TODO remove)

#### Defesa civil no Brasil
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
#### LATAM
- Latin America (Q12585) https://www.wikidata.org/wiki/Q12585
  - https://www.worldometers.info/geography/how-many-countries-in-latin-america/
  - https://www.britannica.com/topic/list-of-countries-in-Latin-America-2061416
- Latin America and the Caribbean (Q72829598) https://www.wikidata.org/wiki/Q72829598

```sparql
SELECT ?country_in_latam ?country_in_latamLabel WHERE {
  wd:Q12585 wdt:P527 ?country_in_latam.
  
  # FIXME: this is returning South America and other regions
  # wd:Q12585 wdt:P527 ?country_in_latam ;
  #           wdt:P31 wd:Q6256 .
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}
ORDER BY ?country_in_latamLabel
}
```

# Referências

## Referências genéricas 
- Wikipedia en español
  - https://es.wikipedia.org/wiki/Protecci%C3%B3n_civil

- Wikipédia Lusófona
  - https://pt.wikipedia.org/wiki/Categoria:Defesa_civil
  - https://pt.wikipedia.org/wiki/Defesa_civil_no_Brasil
  - https://pt.wikipedia.org/wiki/Centro_Nacional_de_Gerenciamento_de_Riscos_e_Desastres
  - Historia:
    -  https://pt.wikipedia.org/w/index.php?title=Defesa_civil_no_Brasil&type=revision&diff=63566864&oldid=63566838&diffmode=source

## Pesquisa por país


- Argentina
- Bolivia
- Brazil
- Chile
- Colombia
  - http://www.defensacivil.gov.co/
- Costa Rica
- Cuba
- Dominican Republic
- Ecuador
  - https://www.gestionderiesgos.gob.ec/
- El Salvador
  - https://www.proteccioncivil.gob.sv/
- Guatemala
- Haiti
- Honduras
- Mexico
  - https://es.wikipedia.org/wiki/Protecci%C3%B3n_civil#M%C3%A9xico_2
- Nicaragua
- Panama
- Paraguay
- Peru
  - https://es.wikipedia.org/wiki/Instituto_Nacional_de_Defensa_Civil
    - https://www.wikidata.org/wiki/Q5917500
- Puerto Rico
- Uruguay
- Venezuela
  - https://www.pcivil.gob.ve/

-->