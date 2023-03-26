## Timor-Leste

```overpassql
// OverpassQL para Timor-Leste.
// Fonte oficial: http://timor-leste.gov.tl/?p=91&lang=pt
// Geopackage: https://data.humdata.org/dataset/cod-ab-tls

[out:json][timeout:240];
area ["name:pt" = "Timor-Leste"] [boundary=administrative][admin_level=2]-> .pais;
(
  // Pais | UNOCHA admin-0 | admin_level=2
  rel [type=boundary][boundary=administrative][admin_level=2] (area.pais);

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

/* 
NOTA: Apenas Sucos em Tutuala foram cadastrados, tem o resto do país. 
*/
```