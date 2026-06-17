---
title: 🏠 Home — KnowledgeBase J
type: area
created: 2026-06-14
tags: [dashboard, moc]
status: evergreen
cssclasses: [home]
---

# 🏠 KnowledgeBase J

> [!tip] Mantra
> *Nessun file è un'isola; ogni dato è un potenziale collegamento verso una nuova idea.*

## 🚀 Navigazione PARA

> [!example]- 📌 01_Projects — obiettivi attivi
> - 🎓 [[00_MOC Maturità CAT 2026]]
> - 🏗️ [[00_MOC Ingegneria]]
> - ✈️ [[00_MOC Eder Voyage]]
> - 🌍 [[00_MOC Turismo]]
> - 👟 [[00_MOC Sneakhefe]]

> [!example]- 🌳 02_Areas — responsabilità continue
> - 🪪 [[00_MOC Burocrazia]]
> - 💰 [[00_MOC Finanze]]
> - 🏛️ [[00_MOC Architettura CAD]]
> - 🐈 [[00_MOC Casa e Animali]]

> [!example]- 📚 03_Resources & Archivio
> - 📓 [[00_MOC Appunti Notion]] — appunti scolastici importati da Notion
> - 🗃️ [[00_MOC Varie]]
> - 🗄️ `04_Archive` — progetti conclusi / inattivi
> - 🖼️ `Attachments` — allegati e media (organizzati per categoria)

## 🔥 Progetti attivi
```dataview
TABLE status AS "Stato", file.mtime AS "Aggiornata"
FROM "01_Projects"
WHERE type = "project"
SORT file.mtime DESC
```

## 📝 Ultime note modificate
```dataview
TABLE file.folder AS "Cartella", file.mtime AS "Modificata"
FROM "" 
WHERE file.name != "00_Home"
SORT file.mtime DESC
LIMIT 10
```

## 🌱 Note da far crescere (Seme → Evergreen)
```dataview
LIST
FROM ""
WHERE status = "seed"
SORT file.ctime ASC
```

## 🕳️ Note orfane (senza link)
```dataview
LIST
FROM ""
WHERE length(file.inlinks) = 0 AND length(file.outlinks) = 0 AND file.name != "00_Home"
```
