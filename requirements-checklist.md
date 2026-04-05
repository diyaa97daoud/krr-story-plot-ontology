# Homework Requirement Checklist

Source iterated: course homework page "Modelling story plots".

## Required deliverables

- [x] Multiple ontology modules in Turtle
- [x] Family module
- [x] Space/RCC module
- [x] Place module
- [x] Time module
- [x] Event module
- [x] Plot module
- [x] Separate instance Turtle file
- [x] Documentation artifact
- [x] Competency questions
- [x] AI-interaction notes

## File mapping

- Family: `fo.ttl`
- Character world/peoples: `meo.ttl`
- Space (RCC): `rcc.ttl`
- Social: `model-social.ttl`
- Place: `model-place.ttl`
- Time: `model-time.ttl`
- Event: `model-event.ttl`
- Actions: `model-action.ttl`
- Plot: `model-plot.ttl`
- Master model import: `model-story.ttl`
- Instances: `instances-narn-lite.ttl`
- Competency questions: `competency-questions.md`
- Documentation: `documentation.html`
- AI notes: `ai-interactions.md`

## Requirement-focused observations

1. Small number of classes/properties but enriched with inverse properties,
   transitivity, disjointness, and existential restrictions.
2. Story instances are examples only; most work is ontology-level modeling.
3. Competency questions are directly tied to terms present in the ontology.
4. Second iteration added richer constructs: equivalent classes, qualified
   cardinality, and nested class expressions across event/action/plot modules.
5. Current instance file now includes explicit temporal entities, sub-events,
   additional action types, and a hypothetical spatio-temporal validation case.

## Remaining optional improvements

1. Optionally align event-time relations with OWL-Time.
2. Generate HTML directly from ontology annotations with Widoco or LODE.
