# Competency Questions

These are the competency questions the ontology is designed to answer.
I tried to write SPARQL queries for most of them to test the model.

Prefixes used (same for all queries):

```sparql
PREFIX fo: <http://purl.org/family/>
PREFIX krr: <http://example.org/krr/story/>
PREFIX rcc: <https://purl.org/region/rcc8/>
```

---

**1. Who is the parent of X?**

```sparql
SELECT ?parent WHERE {
  krr:turin fo:isAChildOf ?parent .
}
```

**1b. Who is X married to?**

```sparql
SELECT ?spouse WHERE {
  krr:hurin fo:isMarriedTo ?spouse .
}
```

---

**2. Where did character X go during the story?**

```sparql
SELECT ?place WHERE {
  ?e krr:involvesCharacter krr:turin .
  ?e krr:occursIn ?place .
}
```

---

**3. Who was involved in event E?**

```sparql
SELECT ?character WHERE {
  krr:e4_fallOfNargothrond krr:involvesCharacter ?character .
}
```

---

**4. Did event E1 happen before event E2?**

```sparql
SELECT ?t1 ?t2 WHERE {
  krr:e2_turinInDoriath krr:hasTemporalEntity ?t1 .
  krr:e5_deathOfTurin krr:hasTemporalEntity ?t2 .
  ?t1 krr:before ?t2 .
}
```

If this query returns a result then yes, e2 happened before e5.

---

**5. Where did event E occur?**

```sparql
SELECT ?place WHERE {
  krr:e3_turinInNargothrond krr:occursIn ?place .
}
```

---

**6. Is it possible for a character to be in two places at the same time?**

This one is more of a validation check. I modeled a test case in the instance file
where Turin is attached to two disconnected places (dorLomin and nargothrond) at
the same temporal entity (t_conflict). The query below should return results if
such an inconsistency exists:

```sparql
SELECT ?e1 ?e2 ?place1 ?place2 WHERE {
  ?e1 krr:involvesCharacter krr:turin .
  ?e1 krr:occursIn ?place1 .
  ?e1 krr:hasTemporalEntity ?t .
  ?e2 krr:involvesCharacter krr:turin .
  ?e2 krr:occursIn ?place2 .
  ?e2 krr:hasTemporalEntity ?t .
  ?place1 rcc:dc ?place2 .
}
```

If it returns rows, the two places are disconnected (rcc:dc) so the character
cannot physically be in both — this is an impossible situation.

---

**7. What event ends story S?**

```sparql
SELECT ?event WHERE {
  krr:narnStory krr:hasEndingEvent ?event .
}
```

---

**8. What item was used in event E?**

```sparql
SELECT ?item WHERE {
  krr:e4_fallOfNargothrond krr:usesItem ?item .
}
```

For actions specifically (e.g. a sword used to slay):

```sparql
SELECT ?item WHERE {
  krr:a2_slaysGlaurung krr:usesInstrument ?item .
}
```

---

**9. My own question: Which characters appear at a climax event?**

I wanted to see who is involved at the most important story point.

```sparql
SELECT ?character WHERE {
  ?e a krr:Climax .
  ?e krr:involvesCharacter ?character .
}
```

---

**10. My own question: Which events have a time assigned to them?**

This checks that the temporal modeling is actually used in the instance data.

```sparql
SELECT ?event ?time WHERE {
  ?event a krr:Event .
  ?event krr:hasTemporalEntity ?time .
}
```
