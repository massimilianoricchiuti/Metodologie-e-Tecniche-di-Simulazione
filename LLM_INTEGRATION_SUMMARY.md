# Sintesi integrazione LLM

Intervento correttivo finale sulla parte LLM del progetto Domus del Chirurgo.

## Principio adottato

Gli output forniti per ChatGPT 5.5 extended e Gemini 3.5 extended non sono stati inseriti come file grezzi o semplici allegati. Sono stati usati come evidenza per costruire una narrazione progettuale credibile:

1. invio del Prompt A ai due modelli;
2. confronto degli output;
3. decisione metodologica;
4. passaggio al Prompt B;
5. ripetizione dello stesso schema per Prompt C e Prompt D;
6. selezione di un RDF finale circoscritto alle evidenze fornite dalle query.

## File modificati

- `prompts.html`: separa obiettivi, tecniche, risposte, confronto fra modelli ed errori riconosciuti.
- `rdf.html`: documenta il passaggio dalle query al collegamento RDF finale, la lettura della tripla e la portata del risultato.
- `conclusions.html`: riunisce relazione, sfide, portata dell'arricchimento e sviluppi futuri.
- `README.md`: aggiornata la struttura dei file e la checklist.
- `LLM_INTEGRATION_SUMMARY.md`: aggiornata questa sintesi.
- `rdf/domus_enrichment.ttl`: contiene cinque relazioni `arco-lite:hasFindingLocation`, generate dalla Q7 per le localizzazioni qualificate come luoghi di rinvenimento nella [Q3](sparql.html#q3). La proprietà è riusata direttamente da ArCo Lite.
- `rdf/validation-report.md`: aggiornato con la funzione e il conteggio dei due Turtle mantenuti.
- `sparql.html` e `queries/query-eu-07-construct-collegamenti-diretti.rq`: aggiornata la query `CONSTRUCT` con il filtro `a-loc:hasLocationType a-loc:FindingLocation`; materializza nel grafo locale cinque relazioni `arco-lite:hasFindingLocation`.

## File rimossi

- `challenges.html` e `report.html`: contenuti fusi nella pagina unica `conclusions.html` per eliminare ripetizioni senza perdere informazioni.

- `rdf/domus_enrichment_candidates.ttl` e `rdf/domus_enrichment_to_verify.ttl`: rimossi perché trasformavano proposte non sostenute in asserzioni RDF e rendevano meno chiaro il risultato.

## Verifica

- `rdf/domus_enrichment.ttl`: 5 triple, parsing riuscito con RDFLib; tutte usano `arco-lite:hasFindingLocation` e coincidono con il risultato della Q7.
- `rdf/domus_enrichment_experimental.ttl`: 113 triple, parsing riuscito con RDFLib; conservato soltanto come output dell'esperimento.
- La nuova visualizzazione riusa colori, tipografia e componenti del sito.

## Revisione del 10 settembre 2026

La Q3 espone il tipo di localizzazione senza escludere i casi privi di qualificazione. I cinque casi verificati hanno valore `a-loc:FindingLocation`; la Q7 lo richiede nel `WHERE`. La scelta di `arco-lite:hasFindingLocation` deriva dal controllo dei dati e dell’ontologia, successivo all’esperimento LLM.

Home, metodologia, query visualizzate ed eseguibili, pagina RDF, grafico, conclusioni, valutazioni dei prompt e conteggi descrivono questa soluzione. Il [registro dei prompt](prompts/README.md) e l’intestazione del Turtle sperimentale identificano i materiali storici: le risposte originarie non sono state riscritte attribuendo ai modelli la nuova scelta.
