# AI Interaction Notes

This file documents how AI assistance was used for the homework design process.

## Topics discussed with AI

1. Separation into ontology modules (social, place, time, event, action, plot).
2. Minimum axiom set to support deductions (inverse properties, transitivity, class restrictions, disjointness).
3. Alignment with course-provided modules (`fo.ttl`, `meo.ttl`, `rcc.ttl`).
4. Competency-question-driven checks and SPARQL templates.

## Reconstructed interaction notes

1. Prompt theme: how to separate event structure from narrative plot structure without duplicating the same concept.
   Outcome: keep `Story`, `Episode`, and `PlotPoint` in a dedicated plot module and link them to events through `realizedByEvent` and `eventInEpisode`.
2. Prompt theme: whether actions should be merged into events.
   Outcome: retain a dedicated action module because intentional acts need agent, target, and instrument relations that are not always properties of the enclosing event.
3. Prompt theme: how to satisfy the spatial-temporal consistency use case from the homework.
   Outcome: instantiate temporal entities explicitly and add a small hypothetical validation example for impossible co-location queries.
4. Prompt theme: what counts as "rich axioms" for a compact ontology.
   Outcome: add inverse properties, transitivity, qualified cardinality, equivalent classes, disjointness, and existential restrictions rather than multiplying classes.

## Design outcomes influenced by AI iteration

1. Explicit separation between knowledge model and instance file.
2. Dedicated action module instead of merging actions into generic events.
3. Narrative structure module with climax/resolution and ending-event relation.
4. Inclusion of labels/comments for terms to satisfy documentation requirements.

## Validation strategy suggested by AI

1. Maintain a requirement checklist mapped to files.
2. Validate each competency question against example instance data.
3. Add richer axioms before adding large numbers of classes.
4. Make sure every major custom module is exemplified in the instance file.
5. Prefer explicit temporal anchors in the data so event ordering is not only asserted at the event-to-event level.
