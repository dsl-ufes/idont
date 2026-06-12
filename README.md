# ID-O: Information Disorder Ontology

A reference ontology for the Information Disorder framework, grounded in [OntoUML](https://ontouml.org) and the [Unified Foundational Ontology (UFO)](http://purl.org/nemo/gufo).

## Prefix and URI

| Prefix | Namespace |
|--------|-----------|
| `ido:` | `http://purl.org/dsl/ido#` |

## Files

| File | Description |
|------|-------------|
| `information-disorder.ttl` | TBox — Turtle (primary serialization) |
| `information-disorder.rdf` | TBox — RDF/XML (alternative serialization) |
| `abox-war-of-the-worlds.ttl` | ABox — War of the Worlds illustrative case |
| `queries/competency-questions.sparql` | SPARQL queries for all 5 competency questions |

## Ontology Overview

ID-O models information disorder as a structured socio-temporal phenomenon composed of:

- **InformationDisorderEpisode** — a temporally delimited episode or campaign
- **EpisodePhase** — a bounded phase within an episode, specialized into `CreationPhase`, `ProductionPhase`, and `DistributionPhase`
- **InformationDisorder** — the disorder classification, specialized into `Misinformation`, `Disinformation`, and `Malinformation`
- **InformationDisorderMessage** — communicative content classified by a disorder type, characterized by `basedOnReality` and `intentionToHarm`
- **AgentParticipation** — relator mediating an `Agent` and an `EpisodePhase`, with a `participationRole` and optional `Motivation`

## Loading in Protégé

1. Open Protégé and select **File > Open**
2. Load `information-disorder.ttl` for the ontology alone, or `abox-war-of-the-worlds.ttl` to also load the illustrative case (it imports the TBox automatically)
3. Protégé will automatically resolve the `gufo:` import from `http://purl.org/nemo/gufo`
4. Run the HermiT or Pellet reasoner to enable inference over the class hierarchy

## Running the SPARQL Queries

The queries in `queries/competency-questions.sparql` must be executed over both files loaded together (TBox + ABox). They can be run directly in Protégé via the **SPARQL Query** tab, or using any SPARQL engine.

Each query is prefixed with:
```sparql
PREFIX ido: <http://purl.org/dsl/ido#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
```

> **Note:** CQ2 uses `rdfs:subClassOf*` to traverse the `EpisodePhase` hierarchy. A reasoner or SPARQL engine with RDFS entailment must be active for this query to return results.

## Instantiation

The ABox (`abox-war-of-the-worlds.ttl`) contains an illustrative instance of the 1938 *War of the Worlds* radio broadcast as a `Misinformation` episode, covering three phases and the participation of `OrsonWelles`, `CBSRadio`, and `MercuryTheatreOnTheAir`.

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

## Reference

> Anonymous submission. *A Reference Ontology for Information Disorder*. Proceedings of the Brazilian Symposium on Multimedia and the Web (WebMedia), 2026.
