# Cuadro de mando
Proyecto de investigación: Cuadro de mando sobre una base de conocimientos.

### Por: Carlos Moragón Corella.

## Objetivo del Trabajo de Investigación:

Investigar la web semántica y sus componentes, incluyendo su estructura, tecnologías subyacentes, y el lenguaje de consulta SPARQL, con el propósito de aplicar estos conocimientos en la recolección y análisis de datos para la creación de un cuadro de mando interactivo. Este trabajo se centrará en la obtención de datos sobre hospitales y sus empleados, utilizando consultas SPARQL sobre datos estructurados en formato RDF, para visualizar información relevante como la localización geográfica de los hospitales, el número de empleados, y las profesiones y nacionalidades del personal.

### Detalle del Objetivo:

#### 1. Investigación Teórica:

* Web Semántica: Explorar el concepto de la web semántica, sus objetivos, y cómo mejora la interoperabilidad de datos en la web.
* Estructura y Tecnologías: Examinar la estructura de la web semántica, incluyendo el RDF (Resource Description Framework) y ontologías.
* SPARQL: Analizar el lenguaje de consulta SPARQL, su sintaxis, y sus capacidades para extraer datos de bases de conocimiento semánticas.

#### 2. Aplicación Práctica:

* Recolección de Datos: Utilizar consultas SPARQL para obtener datos de hospitales, incluyendo detalles sobre la localización, número de empleados, profesiones y nacionalidades del personal.
* Visualización de Datos: Crear un cuadro de mando interactivo que permita visualizar y analizar los datos recolectados, facilitando la interpretación de la información y apoyando la toma de decisiones informadas.

Este enfoque permitirá combinar el entendimiento teórico de la web semántica y SPARQL con su aplicación práctica en la recolección y visualización de datos, proporcionando una comprensión integral del tema y demostrando su utilidad en contextos reales.

## Consulta:
```{txt}
#Datos de hospitales y sus empleados
SELECT DISTINCT ?nameLabel ?empleados ?paisLabel ?lon ?lat ?profesionLabel ?nacionalidadLabel WHERE {
  ?item wdt:P31/wdt:P279* wd:Q16917;
        wdt:P1128 ?empleados;
        wdt:P17 ?pais;
        p:P625 ?geo.
  

  OPTIONAL{
    ?item wdt:P2561 ?name.
  }.
  
  ?geo psv:P625 ?node.
  
  ?node wikibase:geoLongitude ?lon;
        wikibase:geoLatitude ?lat.
  
  ?empleado wdt:P108 ?item;
            wdt:P106 ?profesion;
            wdt:P27 ?nacionalidad.
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}
```

## Cuadro de mando PowerBI:

![cuadro_de_mando](https://github.com/carlosMoragon/cuadro_de_mando/blob/main/ImagenCuadro.png)

## Cuadro de mando ElasticSearch:
![ElasticSearch](https://github.com/carlosMoragon/cuadro_de_mando/blob/main/ImagenCuadroMando_ElasticSearch.png)

## Documentación:

#### RDF (Resource Description Framework):
* Source: https://www.w3.org/TR/1999/REC-rdf-syntax-19990222/

#### SPARQL:
* Source: https://www.w3.org/TR/sparql11-query/

## Web para consultas:
* Wikidata: https://query.wikidata.org/
