# Validazione RDF/Turtle

I due file Turtle mantenuti nel progetto sono stati analizzati localmente con RDFLib.

| File | Funzione | Esito parsing | Triple lette |
|---|---|---:|---:|
| [`domus_enrichment.ttl`](domus_enrichment.ttl) | Arricchimento finale | riuscito | 8 |
| [`domus_enrichment_experimental.ttl`](domus_enrichment_experimental.ttl) | Output originario dei modelli, conservato per documentare l'esperimento | riuscito | 113 |

Nel file finale, sette triple definiscono la proprietà locale `hasArchaeologicalContextSite`; una collega il reperto ArCo `0800675608` al sito ArCo della Domus del Chirurgo. Il nodo del sito emerge dalla [Q1](../sparql.html#q1); la [Q3](../sparql.html#q3) documenta il reperto e il percorso indiretto che già li collega.

Il parsing conferma la correttezza sintattica, non la verità storica o catalografica delle affermazioni. La revisione semantica è documentata nella pagina [`Arricchimento RDF`](../rdf.html); per questo il file finale non include le ulteriori entità e relazioni presenti nell'output sperimentale. In particolare, le [Q4](../sparql.html#q4) e [Q5](../sparql.html#q5) non individuano il corredo specifico della Domus, mentre la [Q6](../sparql.html#q6) non individua il medico Eutyches come persona collegata al sito.
