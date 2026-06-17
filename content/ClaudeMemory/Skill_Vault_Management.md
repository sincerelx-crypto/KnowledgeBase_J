# Skill: Vault Knowledge Manager

Questa skill definisce il modo in cui Claude interagisce con il vault di Obsidian di J. 

## 🎯 Obiettivo
Trasformare l'output tecnico di Claude in conoscenza strutturata e permanente, utilizzando il vault come memoria principale e fonte di verità.

## 🛠 Operazioni Standard

### 1. Accesso alla Conoscenza (Read)
- **Query**: Quando Claude ha bisogno di contesto, effettuerà ricerche nel vault prima di chiedere all'utente.
- **Pattern**: `grep -r "termine" "/Users/jeantiagouri/Library/Mobile Documents/com~apple~CloudDocs/KnowledgeBase_J"`
- **Integrazione**: Claude leggerà le note correlate per allinearsi allo stile, agli obiettivi e alle decisioni passate di J.

### 2. Aggiornamento della Memoria (Write/Edit)
- **Log di Progetto**: Al termine di ogni task, Claude aggiornerà la nota di progetto corrispondente in `01_Projects` o creerà un nuovo log.
- **Knowledge Capture**: Se durante il lavoro emerge un concetto nuovo o una soluzione a un problema complesso, Claude creerà una nota in `03_Resources`.
- **Aggiornamento Stato**: Claude aggiornerà i file di stato (es. `00_Home.md`) se l'utente lo richiede o se è fondamentale per la visione d'insieme.

### 3. Manutenzione del Vault
- **Linking**: Claude userà i link di Obsidian `[[Nome Nota]]` per collegare le nuove informazioni a quelle esistenti.
- **Tagging**: Utilizzerà i tag appropriati per categorizzare le informazioni.

## 🔄 Flusso di Lavoro "Post-Task"
Ogni volta che un task viene marcato come `completed`, Claude eseguirà:
1. **Sintesi**: Genererà un riassunto conciso di *cosa* è stato fatto e *perché*.
2. **Localizzazione**: Identificherà la nota nel vault che deve essere aggiornata.
3. **Scrittura**: Applicherà le modifiche usando il tool `Edit` per preservare il contenuto esistente.
