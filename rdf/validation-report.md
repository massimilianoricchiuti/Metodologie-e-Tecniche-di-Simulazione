# Validazione RDF/Turtle e materializzazione del rinvenimento

Verifica eseguita il **10 settembre 2026**, a partire dalle **16:44 UTC**, sull’[endpoint SPARQL ArCo](https://dati.cultura.gov.it/sparql). Parsing e controlli locali eseguiti con **RDFLib 7.6.0**.

## Risultato vigente

| File | Funzione | Parsing | Triple |
|---|---|---|---:|
| [domus_enrichment.ttl](domus_enrichment.ttl) | Risultato finale: relazioni `arco-lite:hasFindingLocation` | Riuscito | 5 |
| [domus_enrichment_experimental.ttl](domus_enrichment_experimental.ttl) | Archivio dell’output originario dei modelli, comprese le proposte escluse | Riuscito | 113 |

Il Turtle finale riusa direttamente `https://w3id.org/arco/ontology/arco-lite/hasFindingLocation`. Contiene soltanto cinque triple di dati: la definizione della proprietà appartiene all’ontologia ufficiale e non viene duplicata o modificata nel grafo locale.

## Evidenza del ruolo di rinvenimento

La [Q3](../queries/query-eu-03-beni-arco-filtrati.rq) espone `?locationType` attraverso `OPTIONAL`, conservando anche eventuali beni privi di qualificazione. L’esecuzione ha restituito cinque righe, tutte con `a-loc:FindingLocation`. I [risultati SPARQL completi](evidence/q3-finding-locations-2026-09-10.json) conservano gli URI dei beni e delle localizzazioni, le etichette e i tipi osservati.

| Bene archeologico | Etichetta restituita dalla Q3 | Tipo di localizzazione |
|---|---|---|
| `0800675608` | mosaico (metà/ metà II-III) | `a-loc:FindingLocation` |
| `0800675609` | bacile (prima metà III) | `a-loc:FindingLocation` |
| `0800675610` | capitello corinzio (opera parietale) (metà/ metà II-III) | `a-loc:FindingLocation` |
| `0800675611` | vasca (prima metà III) | `a-loc:FindingLocation` |
| `0800675612` | Ermarco (statua/ maschile, piede) (prima metà III) | `a-loc:FindingLocation` |

Per tutti i casi il percorso raggiunge il sito `https://w3id.org/arco/resource/Site/341671000c872aa799b1e99ae08ca1e8`.

La [Q7](../queries/query-eu-07-construct-collegamenti-diretti.rq) richiede congiuntamente:

- un bene di tipo `arco:ArchaeologicalProperty`;
- una risorsa di tipo `a-loc:TimeIndexedTypedLocation`, collegata al bene;
- il collegamento della localizzazione alla Domus tramite `a-loc:atSite`;
- la qualificazione `a-loc:hasLocationType a-loc:FindingLocation`.

Il template materializza `?entity arco-lite:hasFindingLocation ?site`. L’esecuzione della Q7 sull’endpoint ha prodotto **5 triple distinte**, identiche, come insieme RDF, a quelle del Turtle finale. La `CONSTRUCT` produce un grafo locale e non modifica ArCo.

## Scelta ontologica

La definizione di [hasFindingLocation in ArCo Lite 1.0](https://github.com/ICCD-MiBACT/ArCo/blob/master/ArCo-release/ontologie/arco-lite/1.0/arco-lite.owl) descrive un rapporto fra un bene culturale e un altro bene culturale che ne costituisce la sede di rinvenimento. La proprietà è una sottoproprietà di `arco-lite:hasRelatedWork`, con inversa `arco-lite:isFindingLocationOf`; dominio e codominio formali sono `owl:Thing`.

La Domus è qui interpretata come sede archeologica fisica del rinvenimento. La tipizzazione del suo nodo come `cis:Site` non costituisce, da sola, un’incompatibilità con dominio o codominio. Il riuso è motivato dal significato del sito e dalla qualificazione delle localizzazioni, non soltanto dalla permissività del dominio e del codominio.

Nell’[ontologia Location](https://github.com/ICCD-MiBACT/ArCo/blob/master/ArCo-release/ontologie/location/location.owl), `a-loc:FindingLocation` è un individuo di `a-loc:LocationType`; viene usato come valore di `hasLocationType`, non come classe del nodo intermedio. La Q7 esplicita una regola di materializzazione del progetto: non assume che un generico percorso bene–localizzazione–sito implichi automaticamente un rinvenimento, né dichiara equivalenze o nuove gerarchie fra proprietà ufficiali.

## Controlli eseguiti

| Controllo | Esito |
|---|---|
| Q3 sull’endpoint: beni e tipi delle localizzazioni | 5 beni, tutti qualificati come luoghi di rinvenimento |
| Q7 sull’endpoint confrontata con il Turtle finale | Insiemi RDF identici, 5 triple |
| [ASK sui collegamenti diretti](../sparql-checks/check-direct-artifact-site-link.rq), nei due versi fra i cinque beni e la Domus | `false` nell’endpoint ufficiale alla data della verifica |
| Q7 su dati sintetici con luogo di rinvenimento, localizzazione attuale, altro tipo e tipo assente | Materializzato soltanto il caso di rinvenimento |
| Due percorsi di rinvenimento per la medesima coppia bene–sito | Una sola tripla nel risultato |
| Parsing di tutti i file SPARQL del progetto | 13 file validi |
| Query Q3/Q7 nei file, nei blocchi HTML e nei collegamenti di esecuzione | Coerenti |
| Collegamenti interni e ancore HTML | Nessun riferimento mancante |
| Prompt originari ed estratti delle risposte dei modelli | Contenuto preservato |
| Grafo del Turtle sperimentale rispetto alla versione precedente | Identico: cambia soltanto l’intestazione esplicativa |

Il risultato `false` dell’ASK riguarda soltanto i cinque beni e il nodo della Domus indicati nella query. Non è una conclusione sull’intero dataset o su eventuali altri URI del sito.

## Portata e materiali storici

Il parsing verifica la sintassi; il confronto con Q3, Q7 e le definizioni ontologiche sostiene la corrispondenza semantica adottata. La relazione diretta conserva il rinvenimento, mentre il pattern ArCo originale rimane il riferimento per la localizzazione qualificata e per le eventuali informazioni temporali.

Il risultato non cataloga il corredo chirurgico o Eutyches. Le Q4–Q6 non hanno individuato URI pertinenti per tali entità nelle ricerche documentate; questo non dimostra che esse siano assenti da qualunque fonte o da ogni possibile interrogazione del grafo.

I prompt e gli output sperimentali conservano le proprietà locali proposte in origine. Il [registro dei prompt](../prompts/README.md) e la [pagina di confronto](../prompts.html) distinguono questi documenti storici dalla soluzione vigente. Le loro formulazioni non vengono retroattivamente attribuite alla Q7 aggiornata.

## Identificazione dei file verificati

- SHA-256 del Turtle finale: `83ac4c389efe9497fcabbe0a199bb25e9b9010b223b74340fcd5a224272eb21f`.
- SHA-256 dei risultati Q3 archiviati: `6a89f8ba4a1bf6dab7e299784b5e63c14f6f7174e34ea8569b7ce437d5bb6146`.
