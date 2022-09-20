# yet-another-ontology-for-humanitarian-emergency-assistance
**Yet Another Ontology for Humanitarian Emergency Assistance contexts...**
**_but_ also engineered with the Basic Formal Ontology (ISO/IEC 21838-2:2021 version)**.
Why BFO? It is the most used top level ontology (i.e. best interoperability on scientific research),
but also means philosophy ([mereology](https://en.wikipedia.org/wiki/Mereology)) becomes a requisite to a point [RDF](https://en.wikipedia.org/wiki/Resource_Description_Framework) feels easy. So. Much. Fun!

> > **Disclaimer**: this repository is mostly for validate implementations with OWL semantics not already automated/implemented in other projects.
Feel free to explore how it works, or even copy parts you need, but as of 2022-09-19,
but the URIs are not granted to be permanent.

## Current drafts

> _"An ontology is a formal, explicit specification of a shared conceptualization."_
> -- https://iaoa.org/isc2012/docs/Guarino2009_What_is_an_Ontology.pdf

### `xcod.owl`

- At the moment, the [xcod.owl](xcod.owl) is a rudimentar mapping from Wikidata,
OpenStreetMap and [Common Operational Datasets](https://en.wikipedia.org/wiki/Common_Operational_Datasets).
  - However, as BFO explicitly enforces as good practice the need to encode _the classes_ as [universals](https://www.wikidata.org/wiki/Q3551307), this makes things not trivial.
    - Actually, the harder concept is which universal is represented on _Humanitarian Profile_. The idea of common operational datasets (note the lower case) still exists (at least in military contexts).
- The good news is: do exist data collections which are (while not exact same name) in use in different communities!
  - Then, some work to abstract the underlying idea can allow search more data while simplifying how to tag content (which could work regardless of cultures)

<!--
- Country Country-specific CODs (instead of FODs) labeled on Wikipedia around 2018
  - https://en.wikipedia.org/w/index.php?title=Common_Operational_Datasets&type=revision&diff=850537442&oldid=816439628
-->

<!-- ## Where are the other ontologies? -->

---

If you're a researcher looking for alternatives, consider [Implementation of FAIR Principles for Ontologies in the Disaster Domain: A Systematic Literature Review (doi.org/10.3390/ijgi10050324)](https://doi.org/10.3390/ijgi10050324) (and [Allan Mazimwe copy of ontologies](https://github.com/mazimweal/mazimweal.github.io/tree/master/onto)).