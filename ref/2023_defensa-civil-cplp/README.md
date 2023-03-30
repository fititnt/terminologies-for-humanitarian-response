


## Brasil


```overpassql
// Limites administrativos sem IBGE:GEOCODIGO

[out:json][timeout:240];

area [name = "Santa Catarina"] [boundary=administrative][admin_level=4]-> .uf;

rel [type=boundary][boundary=administrative][admin_level]
  // Limite pelo máximo admin_level desejado dentro
  // da Unidade da Federação (10, 9, 8, 7, 6, 5, 4):
  (if: t["admin_level"] <= 10 )
  [!"IBGE:GEOCODIGO"]  (area.uf);

out center;

{{style:
  relation {text: eval('tag("name") . " (" . tag("admin_level") . ")"')}
}}

```

```overpassql
// Limites administrativos sem IBGE:GEOCODIGO

[out:json][timeout:240];

area [name = "Brasil"] [boundary=administrative][admin_level=2]-> .pais;

rel [type=boundary][boundary=administrative][admin_level]
  // Limite pelo máximo admin_level desejado dentro
  // da Unidade da Federação (10, 9, 8, 7, 6, 5, 4):
  (if: t["admin_level"] <= 6 )
  [!"IBGE:GEOCODIGO"]  (area.pais);

out center;

{{style:
  relation {text: eval('tag("name") . " (" . tag("admin_level") . ")"')}
}}

```

```
// Hospitais

[out:json][timeout:25];
{{geocodeArea:Santa Catarina}}->.searchArea;
(
  node["healthcare"="hospital"](area.searchArea);
  way["healthcare"="hospital"](area.searchArea);
  relation["healthcare"="hospital"](area.searchArea);
);
// print results
out body;
>;
out skel qt;
```

// Vide https://www.openstreetmap.org/way/939407207 (precisaria mais de um ref)

```
// Base de ambulâncias

[out:json][timeout:25];
{{geocodeArea:Santa Catarina}}->.searchArea;
(
  node["emergency"="ambulance_station"](area.searchArea);
  way["emergency"="ambulance_station"](area.searchArea);
  relation["emergency"="ambulance_station"](area.searchArea);
);
// print results
out body;
>;
out skel qt;
```


## Timor-Leste

```overpassql
// OverpassQL para Timor-Leste.
// Fonte oficial: http://timor-leste.gov.tl/?p=91&lang=pt
// Geopackage: https://data.humdata.org/dataset/cod-ab-tls
// Link: https://overpass-turbo.eu/s/1sUL

/*  NOTA: Apenas Sucos em Tutuala foram cadastrados, tem o resto do país. */


[out:json][timeout:240];
area ["name:pt" = "Timor-Leste"] [boundary=administrative][admin_level=2]-> .pais;
(
  // Pais | UNOCHA admin-0 | admin_level=2
  //rel [type=boundary][boundary=administrative][admin_level=2] (area.pais);

  // OSM admin_level=3 não usado

  // Distritos | UNOCHA admin=1 | admin_level=4
  rel [type=boundary][boundary=administrative][admin_level=4] (area.pais);

  // Subdistritos | UNOCHA admin=2 | admin_level=5
  rel [type=boundary][boundary=administrative][admin_level=5] (area.pais);

  // Sucos | UNOCHA admin=3 | admin_level=6
  rel [type=boundary][boundary=administrative][admin_level=6] (area.pais);

  // OSM admin_level=7 não usado
  // OSM admin_level=8 não usado
  // OSM admin_level=9 não usado
  // OSM admin_level=10 não usado
);

out body center;
(._;>;);
out;

```

### Nnós representativos que não são place

```overpassql
// OverpassQL para Timor-Leste.
// Fonte oficial: http://timor-leste.gov.tl/?p=91&lang=pt
// Geopackage: https://data.humdata.org/dataset/cod-ab-tls
// URL: https://overpass-turbo.eu/s/1sVH
/*  NOTA: Apenas Sucos em Tutuala foram cadastrados, tem o resto do país. */


[out:json][timeout:240];
area ["name:pt" = "Timor-Leste"] [boundary=administrative][admin_level=2]-> .pais;
(
  // Pais | UNOCHA admin-0 | admin_level=2
  //rel [type=boundary][boundary=administrative][admin_level=2] (area.pais);

  // O

```

- https://www.openstreetmap.org/changeset/99979596
  - https://estatal.gov.tl/wp-content/uploads/2020/08/Diploma-Ministerial-n.%C2%BA-199GMMAEOTIX09-de-16-de-Setembro-Fixa-o-nu%CC%81mero-de-Sucos-e-Aldeias-em-Territo%CC%81rio-Nacional.pdf