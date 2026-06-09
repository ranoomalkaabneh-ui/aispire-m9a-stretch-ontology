# aispire-m9a-stretch-ontology

# Board Games Ontology

## Domain

I chose board games because I enjoy tabletop games and the domain has clear entities and relationships that are easy to model in RDF.

## Entity Types and Relationships

Classes:

- Game
- StrategyGame (subclass of Game)
- PartyGame (subclass of Game)
- Designer
- Genre

Relationships:

- Game → genre → Genre
- Game → designer → Designer
- Game → year → publication year
- Game → playTime → average play time (optional)

## Non-Obvious Modeling Decision

I modeled StrategyGame and PartyGame as subclasses of Game instead of storing the game type as a text property. This allows subclass-aware SPARQL queries using `rdfs:subClassOf*` and makes the ontology easier to extend with new game categories.

## SKOS and Subclass Usage

SKOS labels are used on Genre instances:

- Strategy → altLabel "Tactical"
- Party → altLabel "Social"

This allows users to search using either preferred labels or alternative labels.

Subclass hierarchy:

- StrategyGame rdfs:subClassOf Game
- PartyGame rdfs:subClassOf Game

This enables queries that retrieve all games regardless of specific subtype.

## Optional Property

The property `:playTime` is optional. Some games include it while others do not.