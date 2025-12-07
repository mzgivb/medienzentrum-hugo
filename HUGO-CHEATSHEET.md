# Hugo Cheat Sheet - Medienzentrum Gießen-Vogelsberg

## Schnellstart

### Seite lokal starten (Vorschau)
```bash
cd /Users/jochenleeder/Documents/mzgivb-demo/medienzentrum-demo
hugo server
```
Dann im Browser öffnen: `http://localhost:1313`

### Seite bauen (für Veröffentlichung)
```bash
hugo
```
Die fertige Seite liegt dann im Ordner `public/`

---

## Content-Pflege

### Ordnerstruktur
```
content/
├── _index.md          ← Startseite
├── blog/              ← Blog-Beiträge
│   ├── _index.md      ← Blog-Übersichtsseite
│   └── mein-post.md   ← Einzelner Beitrag
├── edupool/           ← Edupool-Bereich
├── fortbildungen/     ← Fortbildungen
├── mint-space/        ← MINT-Space
└── verleih/           ← Verleih
```

### Neuen Blog-Beitrag erstellen

1. Neue Datei anlegen: `content/blog/mein-neuer-beitrag.md`
2. Inhalt einfügen:

```markdown
---
title: "Mein neuer Beitrag"
date: 2025-12-07
draft: false
summary: "Kurze Beschreibung für die Übersicht"
---

Hier kommt der eigentliche Text.

## Unterüberschrift

Mehr Text hier...
```

### Bestehenden Beitrag bearbeiten

1. Datei im `content/`-Ordner finden
2. Mit Texteditor öffnen
3. Änderungen speichern
4. Mit `hugo server` Vorschau prüfen

---

## Markdown Basics

### Formatierung
```markdown
**fett**
*kursiv*
~~durchgestrichen~~
```

### Überschriften
```markdown
# Hauptüberschrift (H1)
## Unterüberschrift (H2)
### Kleinere Überschrift (H3)
```

### Listen
```markdown
- Punkt 1
- Punkt 2
- Punkt 3

1. Nummeriert
2. Zweiter Punkt
3. Dritter Punkt
```

### Links und Bilder
```markdown
[Linktext](https://example.com)

![Bildbeschreibung](/images/bild.jpg)
```

### Tabellen
```markdown
| Spalte 1 | Spalte 2 |
|----------|----------|
| Inhalt   | Inhalt   |
```

---

## Frontmatter (Metadaten)

Am Anfang jeder `.md`-Datei zwischen `---`:

```yaml
---
title: "Seitentitel"           # Pflicht
date: 2025-12-07               # Datum (YYYY-MM-DD)
draft: false                   # true = nicht veröffentlichen
summary: "Kurzbeschreibung"    # Für Übersichtsseiten
weight: 10                     # Sortierung (kleiner = weiter oben)
---
```

---

## Navigation bearbeiten

Die Navigation wird in `hugo.toml` definiert:

```toml
[[menus.main]]
  name = 'Startseite'
  pageRef = '/'
  weight = 10

[[menus.main]]
  name = 'Blog'
  pageRef = '/blog'
  weight = 20
```

`weight` bestimmt die Reihenfolge (kleiner = weiter links)

---

## Typische Workflows

### Workflow: Neuen Blog-Beitrag veröffentlichen

1. `hugo server` starten
2. Neue `.md`-Datei in `content/blog/` erstellen
3. Frontmatter + Inhalt schreiben
4. Im Browser prüfen (localhost:1313)
5. Wenn OK: `hugo` ausführen
6. `public/`-Ordner auf Server hochladen

### Workflow: Bestehende Seite ändern

1. `hugo server` starten
2. Datei in `content/` finden und bearbeiten
3. Speichern → Browser aktualisiert automatisch
4. Wenn OK: `hugo` ausführen
5. Deployen

### Workflow: Beitrag als Entwurf speichern

```yaml
---
title: "Noch nicht fertig"
draft: true    # ← Wird nicht veröffentlicht
---
```

Entwürfe lokal anzeigen:
```bash
hugo server -D
```

---

## Häufige Probleme

### Seite zeigt Änderung nicht an
- Browser-Cache leeren (Strg+F5)
- Hugo Server neu starten

### Beitrag erscheint nicht
- `draft: false` gesetzt?
- Datum nicht in der Zukunft?
- Datei im richtigen Ordner?

### Formatierung kaputt
- Leerzeile vor/nach Listen und Code-Blöcken
- Keine Tabs, nur Leerzeichen für Einrückung

---

## Nützliche Befehle

| Befehl | Beschreibung |
|--------|--------------|
| `hugo server` | Lokale Vorschau starten |
| `hugo server -D` | Vorschau inkl. Entwürfe |
| `hugo` | Seite bauen |
| `hugo --minify` | Seite bauen (komprimiert) |
| `hugo new blog/titel.md` | Neuen Beitrag erstellen |

---

## Dateiendungen

- `.md` = Markdown (Content)
- `.html` = Templates (nicht anfassen ohne HTML-Kenntnisse)
- `.toml` = Konfiguration
- `.css` = Styling

---

## Hilfe & Ressourcen

- [Hugo Dokumentation](https://gohugo.io/documentation/)
- [Markdown Guide](https://www.markdownguide.org/)
- [Hugo Schnellstart](https://gohugo.io/getting-started/quick-start/)
