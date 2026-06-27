# IDONT: Information Disorder Ontology

IDONT is a reference ontology for the Information Disorder framework, grounded in [OntoUML](https://ontouml.org) and the [Unified Foundational Ontology (UFO)](http://purl.org/nemo/gufo).

## Prefix and URI

| Prefix | Namespace |
|--------|-----------|
| `idont:` | `https://purl.org/dsl/idont#` |
| `ex:` | `https://purl.org/dsl/idont/data/martian-invasion-cbs#` |

## Files

| File | Description |
|------|-------------|
| `information-disorder.ttl` | TBox in Turtle |
| `information-disorder.rdf` | TBox in RDF/XML |
| `abox-war-of-the-worlds.ttl` | ABox for the War of the Worlds illustrative case |
| `queries/competency-questions.sparql` | Aggregated SPARQL queries for the 5 competency questions |
| `queries/cq1-classification.rq` | CQ1 query |
| `queries/cq2-agents-in-each-phase.rq` | CQ2 query |
| `queries/cq3-content-formats.rq` | CQ3 query |
| `queries/cq4-message-reuse.rq` | CQ4 query |
| `queries/cq5-motivations.rq` | CQ5 query |

## Ontology Overview

IDONT models information disorder as a structured socio-temporal phenomenon composed of:

- **InformationDisorderEpisode**: a temporally delimited episode or campaign.
- **InformationDisorderEpisodePhase**: a bounded phase within an episode, specialized into `CreationPhase`, `ProductionPhase`, and `DistributionPhase`.
- **InformationDisorderEvent**: an information disorder occurrence, specialized into `MisinformationEvent`, `DisinformationEvent`, and `MalinformationEvent`.
- **Message**: communicative content characterized by `content`, `format`, and `basedOnReality`.
- **AgentParticipation**: a relator connecting an `Agent` to a `Message` in the context of a phase, with `participationType`, `intentionToHarm`, and `motivation`.
- **Motivation**: a quality associated with participation and classified by `MotivationType`.

## Competency Questions

The repository includes queries for the following CQs:

- **CQ1:** How can an information disorder event be classified as misinformation, disinformation, or malinformation?
- **CQ2:** Which agents participate in each phase of an information disorder episode?
- **CQ3:** Which content formats are associated with the message artifacts involved in each phase of the episode?
- **CQ4:** Which message artifact is reused across the phases of the episode?
- **CQ5:** What motivations characterize agents' participation in information disorder events?

## Instantiation

The ABox models the 1938 *War of the Worlds* CBS radio broadcast as an illustrative misinformation case. The episode contains three phases:

- `CreationPhase_MI`: Orson Welles participates as `Creator` and involves `WarOfTheWorldsScript`, a text message artifact.
- `ProductionPhase_MI`: CBS Radio participates as `Producer` and involves `WarOfTheWorldsBroadcast`, an audio message artifact.
- `DistributionPhase_MI`: Mercury Theatre on the Air participates as `Distributor` and reuses `WarOfTheWorldsBroadcast`.

This structure supports the paper's CQ3 result (`script -> text`, `broadcast -> audio`) and CQ4 result (the broadcast artifact reused in production and distribution).

## Loading in Protege

1. Open Protege and select **File > Open**.
2. Load `information-disorder.ttl` for the ontology alone.
3. Load `abox-war-of-the-worlds.ttl` together with the TBox to run the competency-question queries.
4. Run a reasoner if you need inferred class hierarchy results. The provided CQs work over the explicit triples in the current ABox.

## Running the SPARQL Queries

Run each `.rq` file over the combined graph:

```sh
information-disorder.ttl + abox-war-of-the-worlds.ttl
```

Expected result counts:

| CQ | Rows | Main result |
|----|------|-------------|
| CQ1 | 1 | `WarOfTheWorldsBroadcast` typed as `MisinformationEvent` |
| CQ2 | 3 | one agent per phase |
| CQ3 | 3 | creation uses text; production and distribution use audio |
| CQ4 | 3 | broadcast artifact appears in production and distribution |
| CQ5 | 6 | social, psychological, and financial motivations by agent participation |

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
