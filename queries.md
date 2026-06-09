# Query 1: Subclass-Aware Query

"""sparql
PREFIX : <http://aispire.example.org/boardgames/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?game
WHERE {
  ?game a ?type .
  ?type rdfs:subClassOf* :Game .
}
"""

# Query 2: SKOS-Disambiguated Query

"""sparql
PREFIX : <http://aispire.example.org/boardgames/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?game ?name
WHERE {
  ?genre (skos:prefLabel|skos:altLabel) "Tactical" .
  ?game :genre ?genre ;
        :name ?name .
}
"""

# Query 3: Games Published After 2015

"""sparql
PREFIX : <http://aispire.example.org/boardgames/>

SELECT ?game ?year
WHERE {
  ?game :year ?year .
  FILTER(?year > 2015)
}
ORDER BY ?year
"""