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
- `rdf/domus_enrichment.ttl`: ridotto alla definizione minima della proprietà locale e al solo collegamento bene–sito sostenuto dalla [Q3](sparql.html#q3).
- `rdf/validation-report.md`: aggiornato con la funzione e il conteggio dei due Turtle mantenuti.

## File rimossi

- `challenges.html` e `report.html`: contenuti fusi nella pagina unica `conclusions.html` per eliminare ripetizioni senza perdere informazioni.

- `rdf/domus_enrichment_candidates.ttl` e `rdf/domus_enrichment_to_verify.ttl`: rimossi perché trasformavano proposte non sostenute in asserzioni RDF e rendevano meno chiaro il risultato.

## Verifica

- `rdf/domus_enrichment.ttl`: 8 triple, parsing riuscito con RDFLib.
- `rdf/domus_enrichment_experimental.ttl`: 113 triple, parsing riuscito con RDFLib; conservato soltanto come output dell'esperimento.
- La nuova visualizzazione riusa colori, tipografia e componenti del sito.


