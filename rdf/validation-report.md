# Validazione RDF/Turtle

I due file Turtle mantenuti nel progetto sono stati analizzati localmente con RDFLib.

| File | Funzione | Esito parsing | Triple lette |
|---|---|---:|---:|
| [`domus_enrichment.ttl`](domus_enrichment.ttl) | Arricchimento finale | riuscito | 12 |
| [`domus_enrichment_experimental.ttl`](domus_enrichment_experimental.ttl) | Output originario dei modelli, conservato per documentare l'esperimento | riuscito | 113 |

Nel file finale, sette triple definiscono la proprietà locale `hasArchaeologicalContextSite`; cinque collegano al sito ArCo della Domus del Chirurgo i beni `0800675608`, `0800675609`, `0800675610`, `0800675611` e `0800675612`. Il nodo del sito emerge dalla [Q1](../sparql.html#q1); la [Q3](../sparql.html#q3) documenta i cinque percorsi indiretti e la [Q7](../sparql.html#q7) li materializza come collegamenti diretti in un grafo locale.

La Q7 è stata eseguita sull'endpoint ArCo l'8 settembre 2026: l'output Turtle conteneva 12 triple distinte, coincidenti con le sette triple di schema e i cinque collegamenti conservati nel file finale. `CONSTRUCT` produce un nuovo grafo RDF, ma non inserisce né modifica dati nell'endpoint interrogato.

Nella stessa data, la query [`check-direct-artifact-site-link.rq`](../sparql-checks/check-direct-artifact-site-link.rq), estesa a tutti e cinque i beni, ha restituito `false`: nell'endpoint non era presente alcuna tripla diretta fra quei beni e il sito della Domus.

Il parsing conferma la correttezza sintattica, non la verità storica o catalografica delle affermazioni. La revisione semantica è documentata nella pagina [`Arricchimento RDF`](../rdf.html); per questo il file finale non include le ulteriori entità e relazioni presenti nell'output sperimentale. In particolare, le [Q4](../sparql.html#q4) e [Q5](../sparql.html#q5) non individuano il corredo specifico della Domus, mentre la [Q6](../sparql.html#q6) non individua il medico Eutyches come persona collegata al sito.
