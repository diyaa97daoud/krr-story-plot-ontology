# Competency Questions and SPARQL Templates

Prefix block for all queries:

```sparql
PREFIX fo: <http://purl.org/family/>
PREFIX krr: <http://example.org/krr/story/>
PREFIX rcc: <https://purl.org/region/rcc8/>
```

1. Who is parent of X? married to X? relative to X?

```sparql
SELECT ?parent ?spouse WHERE {
  OPTIONAL { krr:turin fo:isAChildOf ?parent . }
  OPTIONAL { krr:hurin fo:isMarriedTo ?spouse . }
}
```

2. Where did character X go during the story?

```sparql
SELECT DISTINCT ?place WHERE {
  ?e krr:involvesCharacter krr:turin ;
     krr:occursIn ?place .
}
```

3. Who was involved in event E?

```sparql
SELECT ?character WHERE {
  krr:e4_fallOfNargothrond krr:involvesCharacter ?character .
}
```

4. Did event E1 happen before event E2?

```sparql
ASK {
  krr:e2_turinInDoriath krr:beforeEvent krr:e5_deathOfTurin .
}
```

5. Where did event E occur?

```sparql
SELECT ?place WHERE {
  krr:e3_turinInNargothrond krr:occursIn ?place .
}
```

6. Is it possible to be in location L1 and L2 at the same time?

```sparql
ASK {
  ?e1 krr:involvesCharacter krr:turin ;
      krr:occursIn krr:dorLomin ;
      krr:hasTemporalEntity krr:t_conflict .
  ?e2 krr:involvesCharacter krr:turin ;
      krr:occursIn krr:nargothrond ;
      krr:hasTemporalEntity krr:t_conflict .
  krr:dorLomin rcc:dc krr:nargothrond .
}
```

Interpretation rule: the dataset contains a hypothetical validation example where
the same character is attached to two disconnected places at the same temporal
entity, which should be treated as an impossible co-location pattern.

7. What event ends story S?

```sparql
SELECT ?event WHERE {
  krr:narnStory krr:hasEndingEvent ?event .
}
```

8. What item was used as part of event E or action A?

```sparql
SELECT ?item WHERE {
  { krr:e4_fallOfNargothrond krr:usesItem ?item . }
  UNION
  { krr:a2_slaysGlaurung krr:usesInstrument ?item . }
}
```

9. Additional question: Which characters can be inferred as protagonists?

```sparql
SELECT ?c WHERE {
  ?c a krr:Character ;
     krr:participatesInEvent ?e .
  ?pp a krr:Climax ;
      krr:realizedByEvent ?e .
}
```

10. Additional question: Which events have an explicitly modeled temporal anchor?

```sparql
SELECT ?event ?time WHERE {
  ?event a krr:Event ;
         krr:hasTemporalEntity ?time .
}
```
