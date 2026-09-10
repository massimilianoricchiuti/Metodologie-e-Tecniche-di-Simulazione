# Progetto MTS (GEPID) — Sito web

Sito statico per il progetto del corso [**Metodologie e Tecniche di Simulazione**](https://www.unibo.it/it/studiare/insegnamenti-competenze-trasversali-moocs/insegnamenti/insegnamento/2025/483945) (GEPID, Università di Bologna):
**la Domus del Chirurgo di Rimini nel knowledge graph ArCo, fra lacune di rappresentazione e LLM.**
HTML/CSS/JS puro, senza build — pronto per **GitHub Pages**.

## File

| File | Contenuto |
|------|-----------|
| `index.html` | Home: progetto, contesto, finalità, fonti e team |
| `methodology.html` | Percorso di scoperta del gap + gap a 4 livelli |
| `sparql.html` | Le 7 query reali con codice, estratti verificati, conteggi, interpretazione e collegamenti ai sorgenti |
| `queries/` | I sette file SPARQL `.rq`: sei query `SELECT` di analisi e una `CONSTRUCT` di materializzazione |
| `prompts.html` | Perché sono stati usati gli LLM, tecniche, risposte, confronto ed errori riconosciuti |
| `rdf.html` | Dalle evidenze delle query alle triple finali, con workflow e rappresentazione grafica |
| `conclusions.html` | Esito, workflow, gap, sfide, conclusioni e sviluppi futuri |
| `styles.css` | Foglio di stile condiviso |
| `main.js` | Menu mobile accessibile, chiusura da tastiera ed evidenziazione della pagina corrente |
| `prompts/` | I quattro prompt originari (A zero-shot, B few-shot, C CoT, D validazione) e il registro che ne distingue la funzione storica dalla soluzione vigente |
| `rdf/` | `domus_enrichment.ttl` (5 triple con `arco-lite:hasFindingLocation`), output sperimentale, evidenze della Q3 e report di validazione |
| `sparql-checks/` | Query SPARQL di controllo sull'arricchimento proposto |

## Stato dei requisiti

- [x] Homepage con titolo, abstract, team
- [x] Menu fisso, identico e nella stessa posizione su ogni pagina, con stato corrente e collegamento «Salta al contenuto»
- [x] Sezione argomento con contesto
- [x] Sezione metodologia (gap, metodo, strumenti)
- [x] Pagina con tutte le query SPARQL + estratti effettivi, conteggi e commenti coerenti con gli output
- [x] Pagina conclusiva unica con workflow, discussione delle sfide, esito e sviluppi futuri
- [x] Query `SELECT` con OPTIONAL, DISTINCT, UNION, FILTER, REGEX, LIMIT e ORDER BY
- [x] Query `CONSTRUCT` riproducibile che genera il sotto-grafo RDF locale delle cinque relazioni di rinvenimento con `arco-lite:hasFindingLocation`
- [x] Link a entità esterne navigabili (Wikipedia, Wikidata, ArCo, catalogo)
- [x] Le 3 tecniche di prompting con prompt reali (zero-shot, few-shot, chain-of-thought) → `prompts.html`, `prompts/`
- [x] Confronto di ≥2 LLM (ChatGPT 5.5 extended, Gemini 3.5 extended) → `prompts.html`
- [x] Pagina separata di arricchimento RDF, Turtle finale e validazione → `rdf.html`, `rdf/`
- [x] Codice e materiali nel repository GitHub

## Modellazione del rinvenimento

La [Q3](queries/query-eu-03-beni-arco-filtrati.rq) mostra il tipo delle localizzazioni tramite `OPTIONAL`: per i cinque beni della Domus è `a-loc:FindingLocation`. La [Q7](queries/query-eu-07-construct-collegamenti-diretti.rq) richiede esplicitamente questo valore e genera soltanto `?entity arco-lite:hasFindingLocation ?site`. Il Turtle finale contiene cinque triple di dati e riusa la proprietà ufficiale senza uno schema locale.

La [pagina RDF](rdf.html) motiva la scelta; il [report di validazione](rdf/validation-report.md) e i [risultati Q3 del 10 settembre 2026](rdf/evidence/q3-finding-locations-2026-09-10.json) ne documentano le evidenze. I [prompt originali](prompts/README.md) e il Turtle sperimentale mantengono le formulazioni storiche, con la loro funzione esplicitata.
