# emergency-management

> Work in progress. Ignore for now (Rocha, 2022-10-22)

<!--
- https://www.wikidata.org/wiki/Q10427676
- https://wiki.openstreetmap.org/wiki/User:EmericusPetro/sandbox
- https://pandoc.org/try/
-->


<!-- TOC depthfrom:2 -->

- [related general concepts](#related-general-concepts)
- [Wikidata SPARQL for organizations](#wikidata-sparql-for-organizations)
    - [Option 1](#option-1)
    - [Option 2](#option-2)
- [Wikidata, conventions for tagging properties](#wikidata-conventions-for-tagging-properties)
    - [Wikidata, items that do not fit these conventions](#wikidata-items-that-do-not-fit-these-conventions)
- [Starting points to find more organizations](#starting-points-to-find-more-organizations)
- [TODO](#todo)

<!-- /TOC -->

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

# https://www.wikidata.org/wiki/Q7079212
- conceptum: /office of emergency management/@eng-Latn
  wikidata: Q7079212
```

## Wikidata SPARQL for organizations

### Option 1
```sparql
# organizations: field of work = emergency management (Q1460420) or office of emergency management (Q7079212)
# FIXME: still not finding Q7258782
SELECT ?item ?label ?country WHERE {
  ?item wdt:P101 wd:Q1460420.
  SERVICE wikibase:label {
    bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,es,pt,de".
    ?item rdfs:label ?label.
  }
  OPTIONAL { ?item wdt:P17 ?country. }
  # OPTIONAL { ?item wdt:P1448 ?official_name. }
}
LIMIT 1000
```

[Try it on Wikidata Query Service](https://query.wikidata.org/#%23%20organizations%3A%20field%20of%20work%20%3D%20emergency%20management%20%28Q1460420%29%20or%20office%20of%20emergency%20management%20%28Q7079212%29%0A%23%20FIXME%3A%20still%20not%20finding%20Q7258782%0ASELECT%20%3Fitem%20%3Flabel%20%3Fcountry%20WHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP101%20wd%3AQ1460420.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%0A%20%20%20%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%2Ces%2Cpt%2Cde%22.%0A%20%20%20%20%3Fitem%20rdfs%3Alabel%20%3Flabel.%0A%20%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP17%20%3Fcountry.%20%7D%0A%20%20%23%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP1448%20%3Fofficial_name.%20%7D%0A%7D%0ALIMIT%201000)

### Option 2

```sparql
# organizations: field of work = emergency management (Q1460420)
SELECT DISTINCT ?item ?label ?country ?operating_area (GROUP_CONCAT(DISTINCT ?official_website; SEPARATOR = "|") AS ?official_websites) WHERE {
  ?item wdt:P101 wd:Q1460420;
    (p:P31/ps:P31/(wdt:P279*)) wd:Q327333.
  SERVICE wikibase:label {
    bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en,es,pt,de".
    ?item rdfs:label ?label.
  }
  OPTIONAL { ?item wdt:P17 ?country. }
  OPTIONAL { ?item wdt:P2541 ?operating_area. }
  OPTIONAL { ?item wdt:P856 ?official_website. }
}
GROUP BY ?item ?label ?country ?operating_area
ORDER BY (?country) (?operating_area)
LIMIT 1000
```

[Try it on Wikidata Query Service](https://query.wikidata.org/#%23%20organizations%3A%20field%20of%20work%20%3D%20emergency%20management%20%28Q1460420%29%0ASELECT%20DISTINCT%20%3Fitem%20%3Flabel%20%3Fcountry%20%3Foperating_area%20%28GROUP_CONCAT%28DISTINCT%20%3Fofficial_website%3B%20SEPARATOR%20%3D%20%22%7C%22%29%20AS%20%3Fofficial_websites%29%20WHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP101%20wd%3AQ1460420%3B%0A%20%20%20%20%28p%3AP31%2Fps%3AP31%2F%28wdt%3AP279%2a%29%29%20wd%3AQ327333.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%0A%20%20%20%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%2Ces%2Cpt%2Cde%22.%0A%20%20%20%20%3Fitem%20rdfs%3Alabel%20%3Flabel.%0A%20%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP17%20%3Fcountry.%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP2541%20%3Foperating_area.%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP856%20%3Fofficial_website.%20%7D%0A%7D%0AGROUP%20BY%20%3Fitem%20%3Flabel%20%3Fcountry%20%3Foperating_area%0AORDER%20BY%20%28%3Fcountry%29%20%28%3Foperating_area%29%0ALIMIT%201000)

## Wikidata, conventions for tagging properties

- property: **instance of (P31)**
  - Values: **government agency (Q327333)**
  - Note: It can be a subtype
- property: **field of work (P101)**
  - Values: **emergency management (Q1460420)**
- property: **operating area (P2541)**
  - Values: the region, in special if already not the "country")
  - Examples:
    - https://www.wikidata.org/wiki/Q7258782
    - https://www.wikidata.org/wiki/Q107464177

### Wikidata, items that do not fit these conventions

Note: this list is not comprehensive. They are mostly here to show examples of Wikidata items that would be missed on the conventions. These, however, could be candidates for additional lists in other SPARQL queries.

- **UN System**
  - United Nations Office for the Coordination of Humanitarian Affairs (Q1065854)
    - part of United Nations System
  - United Nations High Commissioner for Refugees (Q132551)
    - (...)
- **IFRC related**
  - CADRIM (Q105264524) - Caribbean Disaster Risk Management Resource Center
    - instance of organization 
    - part of International Federation of Red Cross and Red Crescent Societies 
- **International organizations (except UN system and IFRC)**
  - Caribbean Disaster Emergency Management Agency (Q5039374) - Caribbean Disaster Emergency Response Agency CDEMA
    - instance of international organization (Q484652)
- **Foreign aid (not focused on own country; not already UN system; not charitable organization)**
  - Office of Foreign Disaster Assistance (Q3347537)
    - parent organization United States Agency for International Development (Q217072)
- **Related to military**
  - U.S. Air Force Emergency Management (Q19878356)
    - part of United States Air Force (Q11223)
  - Plan DN-III-E (Q253066) - Mexican Secretariat of National Defense aid operation
    - instance of military unit (Q176799)
- **Other reasons**
  - EURETS (Q1276285) - European Emergency Temporary Shelter
  - Cabinet Office Briefing Room (Q1790966) - UK emergency committee
    - instance of committee
  - MapAction (Q6753712) - UK charitable organization
    - instance of non-governmental organization
  - Bundesministerium des Innern. Schutzkommission (Q17354068) - Germany (West)
    - instance of panel
  - Disaster Management Bureau (Q48725793)
    - instance of government organization (Q2659904)
  - Scientific Advisory Group for Emergencies (Q88096332) - UK government advisory body
    - instance of advisory board (Q4686866)
  - University of Washington Population Health Initiative (Q104732823) - Population Health Initiative, University of Washington
    - instance of university research group (Q28863779)

## Starting points to find more organizations
- https://en.wikipedia.org/wiki/Office_of_emergency_management
- https://www.wikidata.org/wiki/Q5039374
  - See participant section

## TODO
- As 2022-10-22, several governmental organizations are still not labeled as field of work = emergency management. We need to improve this topic
- The SPARQL query still returning people (however it would be necessary fix all items to be governmental organizations before "fix" it)
- Add more agencies from here https://en.wikipedia.org/wiki/Office_of_emergency_management