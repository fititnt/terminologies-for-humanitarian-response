---
layout: page
title: About
permalink: /about/
---

> _"An ontology is a formal, explicit specification of a shared conceptualization."_
> -- [N. Guarino et al.](https://iaoa.org/isc2012/docs/Guarino2009_What_is_an_Ontology.pdf)

YAOHEA is an early attempt of formal specification using as upper ontology the
[Basic Formal Ontology (BFO)](https://basic-formal-ontology.org/)
and encoding with [Web Ontology Language (OWL)](https://en.wikipedia.org/wiki/Web_Ontology_Language))
of **already existing practices**
on concepts with proof of already be used for data exchange on it's focused area and the authors.


## Relation to existing practices on international humanitarian action

While it does have as starting point one more _top-down approach_
(as the references for _"common operational datasets"_ actually are from _"Common Operational Datasets (CODs endorsed by the guardian UN OCHA)"_)
there's a clear intention of focus on what is know to exist outside target audience of [such CODs](https://cod.unocha.org/). YAOHEA as side effect interlink concepts (including how to find more datasets) which are not explicitly considered as recommendation on humanitarian action (but could be). Some implications:

1. **Published ontologies are not literal translations.** The preference labels can intentionally diverge from terminology used either because more common terms exist for such concepts, or special circumstances to avoid confusion. However, they need to be good enough to allow create one specific implementation (which can be an endorsed terminology, less abstract than ontology).
2. **The numeric codes are stable way to use as reference.** The use of interlingual neutral codes are good practice on ontology engineering, speed up initial work, and allows changes over time without break implementation.
3. (... TODO talk about mapping OSM tags and etc)
4. (... TODO talk about Wikidata)

> @TODO explain more

<!--

This is the base Jekyll theme. You can find out more info about customizing your Jekyll theme, as well as basic Jekyll usage documentation at [jekyllrb.com](https://jekyllrb.com/)

You can find the source code for Minima at GitHub:
[jekyll][jekyll-organization] /
[minima](https://github.com/jekyll/minima)

You can find the source code for Jekyll at GitHub:
[jekyll][jekyll-organization] /
[jekyll](https://github.com/jekyll/jekyll)


[jekyll-organization]: https://github.com/jekyll

-->


## Trivias
1. The _"Humanitarian Emergency Assistance"_ is based on the title of [A/RES/46/182](https://undocs.org/Home/Mobile?FinalSymbol=A/RES/46/182).
2. The _"Yet Another Ontology"_ is based on the fact that a few dozens of formal ontologies in the last decades attempted data exchange on areas related to A/RES/46/182. Some are not even online anymore.
    1. However, the close to de facto use tend to be limited to lightweight controlled vocabularies
3. The use in English of _"of"_ and "_for_" with `<some subject> for <humanitarian>` instead of `<some subject> (is) <humanitarian>` (e.g. "data for humanitarian use" instead of "humanitarian data") is because of:
    1. Something inanimate cannot be humanitarian. This does not make sense, even if in languages such as English make shorter sentences.
    2. Some authors such as Hugo Slim prefer to use "humanitarian action" over terms such as "humanitarian aid" also to explicitly make a distinction.