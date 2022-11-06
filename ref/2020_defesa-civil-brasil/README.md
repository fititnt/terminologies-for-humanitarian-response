# Defesa Civil no Brasil

## Wikidata:WikiProject Civil Defense
* https://www.wikidata.org/wiki/Wikidata:WikiProject_Civil_Defense


## Wikipédia Lusófona
- https://pt.wikipedia.org/wiki/Categoria:Defesa_civil
- https://pt.wikipedia.org/wiki/Defesa_civil_no_Brasil
- https://pt.wikipedia.org/wiki/Centro_Nacional_de_Gerenciamento_de_Riscos_e_Desastres
- Historia:
  -  https://pt.wikipedia.org/w/index.php?title=Defesa_civil_no_Brasil&type=revision&diff=63566864&oldid=63566838&diffmode=source


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