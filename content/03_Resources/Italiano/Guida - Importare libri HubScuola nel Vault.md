---
tags: [guida, hubscuola, vault, automazione, claude]
tipo: reference
---

# Guida: Importare libri HubScuola Young nel Vault

> Usa la skill **`hubscuola-to-vault`** — di' a Claude:
> *"Metti il libro [URL] nel vault"* oppure *"Importa il libro di [materia] da HubScuola"*

---

## Libri già importati

| Libro | Materia | Cartella | Viewer |
|-------|---------|----------|--------|
| Il bello della letteratura 3 | Italiano | [[MOC - Il bello della letteratura 3\|📘 MOC]] | [Apri](https://young.hubscuola.it/viewer/6547940?page=1) |

---

## Come funziona la skill

La skill apre il viewer HubScuola nel tuo Chrome, estrae l'indice completo del libro e crea automaticamente:

- **1 nota MOC** con tutto l'indice e link cliccabili a ogni sezione
- **1 nota per ogni Unità/Capitolo** con sezioni pronte per gli appunti
- **Link diretti** a ogni pagina del viewer (`?page=N`)

### Perché link e non testo copiato?

Le pagine HubScuola sono **immagini protette** (DRM), non testo HTML. Non è possibile copiarle. I link diretti ti permettono di aprire qualsiasi pagina con un click da Obsidian.

---

## Processo tecnico (per riferimento)

1. Apre `young.hubscuola.it/viewer/{book_id}?page=1`
2. Clicca "Indice" → espande tutte le sezioni
3. Estrae il TOC via JavaScript: `document.querySelector('.modal-popup-body-content').innerText`
4. Clicca un'Unità e confronta URL risultante con PAG. nel sidepanel → calcola **offset**
   - Formula: `URL_page = book_page_stampata + offset`
   - Esempio libro 3: PAG. 16 → URL page 38 → **offset = 22**
5. Crea cartella `03_Resources/[Materia]/[Libro]/`
6. Genera MOC + note unità con link calcolati

---

## Per aggiungere un nuovo libro

Di' a Claude:
```
Metti nel vault il mio libro di [materia]:
https://young.hubscuola.it/viewer/XXXXXX?page=1
```

Claude userà automaticamente la skill `hubscuola-to-vault`.
