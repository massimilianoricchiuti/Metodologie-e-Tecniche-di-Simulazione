# Registro dei prompt dell’esperimento

I quattro file `prompt-A-zero-shot.txt`, `prompt-B-few-shot.txt`, `prompt-C-cot-controlled.txt` e `prompt-D-validation.txt` conservano il testo originariamente inviato ai modelli. Gli estratti delle risposte e le valutazioni sono nella [pagina Prompt e LLM](../prompts.html).

## Rapporto con il risultato attuale

Le proprietà locali, fra cui `hasArchaeologicalProvenanceSite`, e il riferimento a `dcterms:spatial` appartengono alle proposte storiche. Non costituiscono la modellazione attuale e non vengono sostituiti retroattivamente nei prompt o nelle risposte osservate.

Il 10 settembre 2026 la verifica della [Q3](../queries/query-eu-03-beni-arco-filtrati.rq) ha documentato `a-loc:hasLocationType a-loc:FindingLocation` per tutti e cinque i beni collegati alla Domus. La [Q7](../queries/query-eu-07-construct-collegamenti-diretti.rq) richiede questa qualificazione e materializza cinque triple con `arco-lite:hasFindingLocation`, riusando la proprietà ArCo Lite senza definizioni locali aggiuntive.

Il [Turtle finale](../rdf/domus_enrichment.ttl) contiene 5 triple. Il [Turtle sperimentale](../rdf/domus_enrichment_experimental.ttl) conserva 113 triple e documenta le proposte sottoposte a revisione, comprese quelle escluse. La correttezza sintattica dell’output sperimentale non certifica le sue asserzioni. Le verifiche del risultato vigente sono nel [report di validazione](../rdf/validation-report.md).
