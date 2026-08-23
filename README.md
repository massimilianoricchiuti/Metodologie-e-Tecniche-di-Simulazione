# Progetto MTS (GEPID) — Sito web

Sito statico per il progetto del corso [**Metodologie e Tecniche di Simulazione**](https://www.unibo.it/it/studiare/insegnamenti-competenze-trasversali-moocs/insegnamenti/insegnamento/2025/483945) (GEPID, Università di Bologna):
**la Domus del Chirurgo di Rimini nel knowledge graph ArCo, fra lacune di rappresentazione e LLM.**
HTML/CSS/JS puro, senza build — pronto per **GitHub Pages**.

## File

| File | Contenuto |
|------|-----------|
| `index.html` | Home: progetto, contesto, finalità, fonti e team |
| `methodology.html` | Percorso di scoperta del gap + gap a 4 livelli |
| `sparql.html` | Le 6 query reali con codice, estratti verificati, conteggi, interpretazione e collegamenti ai sorgenti |
| `queries/` | I sei file SPARQL `.rq` riportati nella pagina delle query |
| `prompts.html` | Perché sono stati usati gli LLM, tecniche, risposte, confronto ed errori riconosciuti |
| `rdf.html` | Dalle evidenze delle query alla tripla finale, con workflow e rappresentazione grafica |
| `conclusions.html` | Esito, workflow, gap, sfide, conclusioni e sviluppi futuri |
| `styles.css` | Foglio di stile condiviso |
| `main.js` | Menu mobile accessibile, chiusura da tastiera ed evidenziazione della pagina corrente |
| `prompts/` | I quattro prompt inviati agli LLM (A zero-shot, B few-shot, C CoT, D validazione) |
| `rdf/` | `domus_enrichment.ttl` (risultato finale, 8 triple), output sperimentale e report di validazione |
| `sparql-checks/` | Query SPARQL di controllo sull'arricchimento proposto |

## Stato dei requisiti

- [x] Homepage con titolo, abstract, team
- [x] Menu fisso, identico e nella stessa posizione su ogni pagina, con stato corrente e collegamento «Salta al contenuto»
- [x] Sezione argomento con contesto
- [x] Sezione metodologia (gap, metodo, strumenti)
- [x] Pagina con tutte le query SPARQL + estratti effettivi di 1–3 righe, conteggi e commenti coerenti con gli output
- [x] Pagina conclusiva unica con workflow, discussione delle sfide, esito e sviluppi futuri
- [x] Tutte le keyword SPARQL: OPTIONAL, DISTINCT, UNION, FILTER, REGEX, LIMIT, ORDER BY
- [x] Link a entità esterne navigabili (Wikipedia, Wikidata, ArCo, catalogo)
- [x] Le 3 tecniche di prompting con prompt reali (zero-shot, few-shot, chain-of-thought) → `prompts.html`, `prompts/`
- [x] Confronto di ≥2 LLM (ChatGPT 5.5 extended, Gemini 3.5 extended) → `prompts.html`
- [x] Pagina separata di arricchimento RDF, Turtle finale e validazione → `rdf.html`, `rdf/`
- [x] Codice e materiali nel repository GitHub


