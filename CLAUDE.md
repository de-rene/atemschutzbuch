# Atemschutzbuch — Projektdokumentation

## Arbeitsanweisung für Claude

**Kein Code schreiben, bevor es nicht explizit angewiesen wird. Nicht danach fragen.**

---

## Was ist das?

Digitales Atemschutzbuch für kleine freiwillige Feuerwehren (20–80 Aktive).
Ersetzt das analoge Papierbuch. Kernidee: Freigabe-Workflow – AGT erfasst Einsatz/Übung,
Atemschutzbeauftragter bestätigt, danach unveränderlich gespeichert.

**Aktuelles Ziel:** Statische One-Pager Landing Page zur Bedarfsvalidierung.
Die Seite zeigt geplante Features mit Mockups und einem interaktiven Freigabe-Workflow-Graphen.
Danach werden bekannte Feuerwehr-Chefs befragt (Go/No-Go für MVP).

---

## Repo-Struktur (Monorepo)

```
/
├── website/        ← Cloudflare Pages (Root: website/, Watch: website/**)
│   ├── index.html
│   ├── style.css
│   ├── main.js
│   ├── workflow.js
│   └── assets/
│       ├── mockups/
│       └── icons/
├── app/            ← Später: App-Code → VPS-Deployment (Coolify / GitHub Actions)
├── CLAUDE.md       ← Diese Datei
└── PLAN.md         ← Detaillierter Implementierungsplan Website
```

---

## Cloudflare Pages Konfiguration

| Einstellung | Wert |
|---|---|
| Root directory | `website` |
| Build command | *(leer)* |
| Build output directory | `website` |
| Build watch paths (include) | `website/**` |

→ Commits in `app/` triggern keinen Website-Build.

---

## App-Deployment (später)

- **Coolify** auf eigenem VPS (Hetzner o.ä.) — Monorepo-fähig, `app/` als Root konfigurierbar
- Alternative: GitHub Actions → SSH auf VPS (`cd app/ && docker compose up -d`)
- Kein Vendor-Lock-in zu Cloudflare

---

## Tech-Constraints (Website)

- **Kein** npm, kein Node.js, kein Build-Step, kein Framework
- Plain HTML + CSS + vanilla JS
- Google Fonts via CDN (Fraunces für Headings, Source Serif 4 für Body)
- Scripts am Ende von `<body>`, kein render-blocking

---

## Design-Tokens

| Token | Wert | Verwendung |
|---|---|---|
| `--color-base` | `#1a1a1a` | Anthrazit — dunkle Sections |
| `--color-surface` | `#f5f4f0` | Warmes Off-White — helle Sections |
| `--color-accent` | `#CC2222` | Feuerwehr-Rot — CTAs, Akzente |
| `--font-display` | Fraunces, Georgia, serif | Headings |
| `--font-body` | Source Serif 4, Georgia, serif | Fließtext |

---

## One-Pager Sections

1. **Hero** — dark bg — Headline, Value Prop, CTA
2. **Problem** — warm surface — 4 Problem-Cards
3. **Features** — weiß — 7 Feature-Cards mit SVG-Mockups
4. **Freigabe-Workflow** — dark bg — interaktiver SVG-Graph, 3 Varianten
5. **Für wen?** — warm surface — Personas + Größenindikator
6. **CTA/Kontakt** — Feuerwehr-Rot — Formspree-Formular
7. **Footer** — Impressum + Datenschutz als `<details>`-Elemente

---

## Interaktiver Workflow-Graph

Drei umschaltbare Varianten (Tab-Navigation):

1. **Standard:** AGT → Beauftragter → Freigabe
2. **Mit Stellvertreter:** AGT → Beauftragter ODER Stellvertreter → Freigabe
3. **Mit Ablehnung:** AGT → Beauftragter → Ablehnen (mit Begründung) → AGT korrigiert → erneut einreichen

Umsetzung: SVG + vanilla JS, `document.createElementNS`, keine externe Bibliothek.

---

## Formspree

Formular-Endpoint in `website/index.html`:
```html
<form action="https://formspree.io/f/PLACEHOLDER" ...>
```
→ `PLACEHOLDER` nach Formspree-Account-Einrichtung ersetzen.  
Fallback ohne Account: `action="mailto:rene.kamp@me.com"` + JS-Fetch-Handler entfernen.

---

## Lokale Entwicklung

```bash
cd website/
python3 -m http.server 8080
```

Browser öffnen: http://localhost:8080

---

## Branch-Strategie

- `main` = production → automatisches Cloudflare-Deployment (nur wenn `website/**` geändert)
- Features auf eigenen Branches, Merge via PR nach `main`

---

## Rechtliches

- FwDV 7 erlaubt elektronische Dokumentation
- 40 Jahre Aufbewahrungspflicht für Expositionsdaten
- Keine echten Gesundheitsdaten (nur „G26.3 bestanden/nicht bestanden") → vereinfachte DSGVO
- Impressum + Datenschutz inline im Footer als `<details>`

---

## Linear-Projekt

https://linear.app/renek/project/atemschutzbuch-8cc8404438af

| ID | Titel | Status |
|---|---|---|
| REN-35 | One-Pager: Konzept & Struktur | In Progress |
| REN-36 | One-Pager: Design & Implementierung | Todo |
| REN-37 | Interaktiver Freigabe-Workflow-Graph | Todo (Sub von REN-36) |
| REN-38 | App-Mockups für Feature-Darstellung | Todo (Sub von REN-36) |
| REN-39 | GitHub Repo & Cloudflare Pages Setup | Todo |
| REN-40 | Bedarfsvalidierung: Interviews mit FF-Entscheidern | Todo |
