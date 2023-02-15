# Defesa Civil no Brasil

## Wikidata:WikiProject Civil Defense
* https://www.wikidata.org/wiki/Wikidata:WikiProject_Civil_Defense


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

### firefighting
```sparql
# firefighting (Q897825)
SELECT DISTINCT ?item ?itemLabel ?countryLabel ?operating_areaLabel ?official_website WHERE {
  VALUES ?fow {
    wd:Q897825
  }
  ?item wdt:P101 ?fow.
  MINUS { ?item wdt:P31 wd:Q5. }
  OPTIONAL { ?item wdt:P17 ?country. }
  OPTIONAL { ?item wdt:P2541 ?operating_area. }
  OPTIONAL { ?item wdt:P856 ?official_website. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,de,fr,ru,es,ja,zh,ar". }
}
LIMIT 2000
```

### firefighting v2

```sparql
# fields_of_work=firefighting (Q897825) OR instance_of=fire department (Q6498663) NOT  human (Q5)
SELECT DISTINCT ?item ?itemLabel ?countryLabel ?operating_areaLabel ?official_website WHERE {
  VALUES ?instances_of {
    wd:Q6498663
  }
  VALUES ?fields_of_work {
    wd:Q897825
  }
  { ?item wdt:P101 ?fields_of_work. }
  UNION
  { ?item (p:P31/ps:P31/(wdt:P279*)) ?instances_of. }
  MINUS { ?item wdt:P31 wd:Q5. }
  OPTIONAL { ?item wdt:P17 ?country. }
  OPTIONAL { ?item wdt:P2541 ?operating_area. }
  OPTIONAL { ?item wdt:P856 ?official_website. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,de,fr,ru,es,ja,zh,ar". }
}
ORDER BY (?countryLabel) (?operating_areaLabel)
LIMIT 5000
```

### emergency medical services

```sparql
# instances_of=emergency medical services OR fields_of_work=emergency medicine (Q2861470) NOT  human (Q5)
SELECT DISTINCT ?item ?itemLabel ?countryLabel ?operating_areaLabel ?official_website WHERE {
  VALUES ?instances_of {
    wd:Q860447
  }
  VALUES ?fields_of_work {
    wd:Q2861470
  }
  { ?item wdt:P101 ?fields_of_work. }
  UNION
  { ?item (p:P31/ps:P31/(wdt:P279*)) ?instances_of. }
  MINUS { ?item wdt:P31 wd:Q5. }
  OPTIONAL { ?item wdt:P17 ?country. }
  OPTIONAL { ?item wdt:P2541 ?operating_area. }
  OPTIONAL { ?item wdt:P856 ?official_website. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,de,fr,ru,es,ja,zh,ar". }
}
ORDER BY (?countryLabel) (?operating_areaLabel)
LIMIT 5000
```

### [empty results] rescue
- rescue (Q1341429)
- <s>search and rescue (Q741964)</s>

```sparql
# rescue (Q1341429) NOT human (Q5)
SELECT DISTINCT ?item ?itemLabel ?countryLabel ?operating_areaLabel ?official_website WHERE {
  VALUES ?instances_of {
    wd:Q1341429
  }
  VALUES ?fields_of_work {
    wd:Q1341429
  }
  { ?item wdt:P101 ?fields_of_work. }
  UNION
  { ?item (p:P31/ps:P31/(wdt:P279*)) ?instances_of. }
  MINUS { ?item wdt:P31 wd:Q5. }
  OPTIONAL { ?item wdt:P17 ?country. }
  OPTIONAL { ?item wdt:P2541 ?operating_area. }
  OPTIONAL { ?item wdt:P856 ?official_website. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,de,fr,ru,es,ja,zh,ar". }
}
ORDER BY (?countryLabel) (?operating_areaLabel)
LIMIT 5000
```




- https://pt.wikipedia.org/wiki/Categoria:Empresas_de_energia_el%C3%A9trica_do_Brasil
- https://pt.wikipedia.org/wiki/Categoria:Empresas_de_saneamento_do_Brasil
- https://pt.wikipedia.org/wiki/Categoria:Cemit%C3%A9rios

### Hospitals
- https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples#Map_of_hospitals
```sparql
#added 2017-08
#defaultView:Map
SELECT DISTINCT * WHERE {
  ?item wdt:P31/wdt:P279* wd:Q16917;
        wdt:P625 ?geo .
}
```

### Nuclear power plant (draft)
Note: _installations containing dangerous forces_

```sparql
# nuclear power plant (Q134447)
SELECT DISTINCT ?item ?itemLabel ?countryLabel ?service_entry ?service_retirement ?official_website WHERE {
  VALUES ?instances_of {
    wd:Q134447
  }
  ?item (p:P31/ps:P31) ?instances_of.
  OPTIONAL { ?item wdt:P17 ?country. }
  OPTIONAL { ?item wdt:P729 ?service_entry. }
  OPTIONAL { ?item wdt:P730 ?service_retirement. }
  OPTIONAL { ?item wdt:P856 ?official_website. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,de,fr,ru,es,ja,zh,ar". }
}
ORDER BY (?countryLabel) (?service_entry) (?service_retirement)
```

### levee (Q105190) / flood defense
Note: _installations containing dangerous forces_

```sparql
# levee (Q105190) / flood defense
SELECT DISTINCT ?item ?itemLabel ?countryLabel ?located_in_admLabel ?coordinate_location WHERE {
  VALUES ?instances_of {
    wd:Q105190
  }
  ?item (p:P31/ps:P31) ?instances_of.
  OPTIONAL { ?item wdt:P17 ?country. }
  OPTIONAL { ?item wdt:P131 ?located_in_adm. }
  OPTIONAL { ?item wdt:P625 ?coordinate_location. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,de,fr,ru,es,ja,zh,ar". }
}
ORDER BY (?countryLabel) (?located_in_adm) (?coordinate_location)
```
[Try it on Wikidata Query Service](https://w.wiki/5wPK)


## Tips

### Querying property without value with SPARQL in WikiData
- https://stackoverflow.com/questions/59675996/how-to-find-items-with-no-value-for-a-property
```
FILTER NOT EXISTS { ?item wdt:P17 ?val }
```

## Organize WikiProjects
- https://www.mediawiki.org/wiki/Help:Subpages
  - `{{Special:PrefixIndex/Wikidata:WikiProject_Civil_Defense/}}`