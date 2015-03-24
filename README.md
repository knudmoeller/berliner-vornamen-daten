# Description

RDF ([DataCube](http://www.w3.org/TR/vocab-data-cube)) representation of open data on the frequency of given names in Berlin, by year and by district (2012-2014).


## Example Queries

### Frequencies for a given name and year, by district

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#> 
PREFIX qb: <http://purl.org/linked-data/cube#> 
PREFIX sdmx-code: <http://purl.org/linked-data/sdmx/2009/code#> 
PREFIX sdmx-dimension: <http://purl.org/linked-data/sdmx/2009/dimension#> 
PREFIX namevoc: <http://data.datalysator.com/vocab/> 

SELECT DISTINCT ?district_name ?count
WHERE {
  ?obs a qb:Observation ;
    sdmx-dimension:refTime 2013 ;
    namevoc:name_dim ?name ;
    namevoc:district_dim ?district ;
    namevoc:count_measure ?count ;
  .
  
  ?name rdfs:label  "Paul" ;
    namevoc:sex sdmx-code:sex-M ;
  .
  
  ?district rdfs:label ?district_name .
  
}
ORDER BY desc(?count) ?district_name
```

## Source

The RDF data is based on open data published by the [Berliner Landesamt für Bürger- und Ordnungsangelegenheiten](http://www.berlin.de/labo/) under [CC-BY-3.0](http://creativecommons.org/licenses/by/3.0/de/): 

- http://daten.berlin.de/datensaetze/liste-der-häufigen-vornamen-2012
- http://daten.berlin.de/datensaetze/liste-der-häufigen-vornamen-2013
- http://daten.berlin.de/datensaetze/liste-der-häufigen-vornamen-2014

## License

This data is made available under the Public Domain Dedication and License v1.0 whose full text can be found at: http://www.opendatacommons.org/licenses/pddl/1.0/