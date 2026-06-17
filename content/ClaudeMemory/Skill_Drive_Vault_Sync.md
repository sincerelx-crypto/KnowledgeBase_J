# Skill: Google Drive Sync & Categorization

Questa skill consente a Claude di importare in modo sicuro ed efficiente i file accademici, i disegni CAD e i documenti dal Google Drive locale dell'utente al vault Obsidian (`KnowledgeBase_J`), organizzandoli automaticamente secondo il metodo PARA.

## 🎯 Obiettivo
Cercare nuovi file o importare in massa file da Google Drive locale al vault, categorizzandoli secondo le tematiche scolastiche e professionali di J., ignorando al contempo file multimediali pesanti, installer e configurazioni ridondanti.

---

## 🛠️ Risorse Disponibili
Lo script principale che esegue questa operazione si trova nel sistema locale all'indirizzo:
- 📄 Script: `/Users/jeantiagouri/.gemini/antigravity-ide/scratch/import_drive_files.py`

### Cartella Sorgente (Google Drive locale)
`/Users/jeantiagouri/Library/CloudStorage/GoogleDrive-christian.tiagouri@itgdellaporta-porzio.edu.it/Il mio Drive`

---

## 🔄 Flusso di Lavoro per Claude

Ogni volta che l'utente chiede di "sincronizzare", "importare file dal drive" o "aggiornare il vault dal drive", Claude deve eseguire i seguenti passaggi:

### 1. Esecuzione del Dry-Run (Verifica preventiva)
Prima di copiare qualsiasi file, esegui lo script in modalità simulazione per mostrare all'utente l'elenco dei file che verranno copiati e dove verranno inseriti:
```bash
python3 /Users/jeantiagouri/.gemini/antigravity-ide/scratch/import_drive_files.py --dry-run
```
Mostra all'utente la sintesi dei file per categoria e chiedi conferma.

### 2. Esecuzione dell'Importazione
Una volta ricevuta la conferma dell'utente, esegui lo script per effettuare la copia reale dei file:
```bash
python3 /Users/jeantiagouri/.gemini/antigravity-ide/scratch/import_drive_files.py
```

### 3. Gestione della Latenza di Google Drive
*Nota*: Molti file nel Google Drive locale potrebbero essere scaricati on-demand (hydration). La copia potrebbe richiedere tempo per scaricare file di grandi dimensioni. Mostra pazienza e monitora periodicamente lo stato del processo di copia controllando la cartella di destinazione.

---

## 📊 Regole di Categorizzazione e Filtri

Se lo script deve essere modificato o integrato, rispetta le seguenti regole di filtraggio:

### Destinazioni e Parole Chiave
1. **🎓 Maturità CAT 2026** (`01_Projects/Maturita CAT 2026/Materiali_Drive`):
   - Parole chiave: `solaio`, `solai`, `murature`, `computo`, `dcf`, `goldoni`, `petrarca`, `rivoluzione americana`, `locandiera`, `scheda libro`, `topografia`, `verbale assemblea`, `classe`, `pcto`, `dati`, `relazion`, `ambiente`.
2. **🏗️ Test Ammissione Ingegneria** (`01_Projects/Test Ammissione Ingegneria/Materiali_Drive`):
   - Parole chiave: `matematica`, `logaritmi`, `limiti`, `dominio`, `accumulazione`.
3. **🏛️ Architettura CAD** (`02_Areas/Architettura CAD/Materiali_Drive`):
   - Estensioni `.dwg`, `.dxf` o parole chiave `villa`, `disegno`.
4. **🗃️ Varie / Drive_Import** (`03_Resources/Varie/Drive_Import`):
   - Qualsiasi altro file supportato.

### Cartelle Escluse (Ignorate Ricorsivamente)
- `music`, `pictures`, `downloads`, `illustrations`, `optimizer pro`, `lol`, `rainmeter`, `crashpad`, `cache`, `temp`.

### Estensioni Consentite
- `.md`, `.txt`, `.pdf`, `.docx`, `.doc`, `.pages`, `.rtf`, `.gdoc`
- `.xlsx`, `.xls`, `.gsheet`, `.numbers`, `.csv`
- `.pptx`, `.ppt`, `.gslides`, `.key`
- `.dwg`, `.dxf`, `.dcf`
- `.png`, `.jpg`, `.jpeg`, `.webp`
