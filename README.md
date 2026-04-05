# Submission

This folder contains the final modular OWL/Turtle submission for the story-plot homework.

## Main ontology files

- [model-story.ttl](model-story.ttl): master ontology importing all conceptual modules
- [fo.ttl](fo.ttl), [meo.ttl](meo.ttl), [rcc.ttl](rcc.ttl): corrected and reused provided ontologies
- [model-social.ttl](model-social.ttl): social relations between characters
- [model-place.ttl](model-place.ttl): place hierarchy and spatial relations
- [model-time.ttl](model-time.ttl): temporal vocabulary and relations
- [model-event.ttl](model-event.ttl): event classes and event relations
- [model-action.ttl](model-action.ttl): action model linked to agents, targets, items, and events
- [model-plot.ttl](model-plot.ttl): narrative structure (story, episode, plot point, climax, resolution)

## Instance and support files

- [instances-narn-lite.ttl](instances-narn-lite.ttl): instance ontology importing the master model
- [competency-questions.md](competency-questions.md): competency questions and SPARQL templates
- [documentation.html](documentation.html): human-readable documentation
- [ai-interactions.md](ai-interactions.md): AI-assisted design notes
- [requirements-checklist.md](requirements-checklist.md): requirement-to-file mapping
- [catalog-v001.xml](catalog-v001.xml): Protégé local import mapping file

## Validation

The ontology imports load correctly in Protégé and HermiT completes without errors.
ELK also loads the ontology, but reports expected incompleteness warnings because
this model uses OWL features outside the OWL 2 EL profile, including inverse
properties, disjoint object properties, inverse property expressions, and
qualified minimum cardinality restrictions. These warnings do not indicate an
error in the ontology; they only mean ELK may not compute all inferences for
this more expressive model.
