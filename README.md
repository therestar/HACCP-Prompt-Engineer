# HACCP Prompt Engineer 
Questa repository contiene un progetto dedicato alla realizzazione di una dashboard interattiva per l’esplorazione dei richiami alimentari pubblicati dal [Ministero della Salute](https://www.salute.gov.it/new/). L’obiettivo è trasformare i dati testuali dei richiami in informazioni strutturate a supporto dell’analisi dei rischi e delle attività HACCP.
![dashboard showcase][https://github.com/therestar/test/blob/main/dashboard_showcase.gif]

# Prompt finali

## Prompt 1
> Analizza questi 7 richiami alimentari ed estrai le informazioni principali: 
data, prodotto, produttore, lotto, motivo del richiamo.


## Prompt 2
> Analizza i richiami ed estrai le informazioni in formato JSON con questi campi:
Analizza i richiami ed estrai le informazioni in formato JSON con questi campi:
```json
{
"id": "int",
"data_richiamo": "DD/MM/YYYY",
"denominazione_vendita": "string",
"motivo_richiamo": "string",
"lotto": "string o array",
"tipo_rischio": "microbiologico|chimico|fisico|allergene|etichettatura",
"avvertenze": "string"
}
```

IMPORTANTE: 
  - Se un campo è assente, usa "" 
  - Per i lotti multipli, usa array: ["lotto1", "lotto2"] 
  - Sii preciso sulle date (formato italiano) 
  - Il motivo del richiamo deve essere dettagliato 
  - Se è presente la marca nella denominazione di vendita, omettila
  - Tratta la revoca di richiamo come un normale richiamo.



## Prompt 3
> Sei un consulente HACCP esperto.
> Analizza questi richiami e fornisci:
### ANALISI HACCP:
```json
{"id_richiamo": "id del richiamo a cui si riferisce",
"categoria_pericolo": "biologico|chimico|fisico|allergene",
"gravità": "bassa|media|alta|critica",
"fase_produzione_critica": "ricevimento materie prime|produzione|confezionamento|etichettatura|conservazione",
"ccp_coinvolto": "descrizione del Critical Control Point che ha fallito",
"azioni_correttive_suggerite": ["azione 1","azione 2"],
"misure_preventive": ["misura 1","misura 2"]}
```

### RAGIONAMENTO (Chain-of-Thought)

Spiega passo passo:
- Perché hai assegnato questa gravità.
- Quale fase della produzione è più probabilmente coinvolta.
- Quali controlli HACCP avrebbero potuto prevenire il problema.


## Prompt 4
Sei uno sviluppatore frontend. 
Crea una Dashboard interattiva con le funzionalità:
- Visualizzazione dei richiami in formato tabulare
- Filtrare per tipo di rischio, data (anno), gravità
- Visualizzare i grafici di distribuzione dei rischi
- Esportare i dati in CSV

Non usare React.

Mantieni la risposta entro 200 righe di codice.

Inserisci in basso a destra il label "Realizzato con l'IA"
