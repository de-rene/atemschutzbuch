# Atemschutzbuch Landing Page — Implementierungsplan

## Context

Bedarfsvalidierungs-Landingpage für ein geplantes digitales Atemschutzbuch für kleine freiwillige Feuerwehren (20–80 AGTs). Es gibt noch keine App — die Seite zeigt geplante Features mit Mockups und einem interaktiven Freigabe-Workflow-Graphen, um Interesse zu messen (Interviews mit FF-Entscheidern als nächster Schritt).

**Repo:** `de-rene/atemschutzbuch`  
**Branch:** `claude/atemschutzbuch-landing-oEFM1` (Feature) → Merge auf `main` (Deployment)  
**Deployment:** Cloudflare Pages, direkt aus Repo-Root, kein Build-Schritt

---

## HTML-Struktur

### Head
- `lang="de"`, charset, viewport, title, description
- Open Graph Tags (og:title, og:description, og:image)
- Google Fonts Preconnect + Link: Fraunces + Source Serif 4 mit `display=swap`
- `<link rel="stylesheet" href="style.css">`

### Nav
```html
<header class="site-header">
  <nav class="nav-bar">
    <span class="nav-logo">Atemschutzbuch</span>
    <a href="#kontakt" class="btn btn--primary btn--sm">Interesse bekunden</a>
  </nav>
</header>
```

### Section 1: Hero (dark bg)
- Badge: „Für Feuerwehren mit 20–80 AGTs"
- H1 mit `<span class="text-accent">` für Fraunces-Italic-Swash
- Subline: FwDV-7-konform, rechtssicher, kein Papierchaos
- Zwei Buttons: Primary CTA + Ghost „Features ansehen"
- Trust-Badges: FwDV 7 konform · DSGVO-gerecht · 40 Jahre Aufbewahrung

### Section 2: Problem (warm bg)
4 Problem-Cards:
1. Unleserliche Handschriften → Fehler bei der Auswertung
2. Vergessene Eintragungen → Lücken in der Dokumentation
3. Manuelle Freigabe → Keine Nachvollziehbarkeit
4. Papierverlust → 40-Jahres-Aufbewahrungspflicht gefährdet

### Section 3: Features (weiß)
7 Feature-Cards (`<article class="feature-card">`):
- `.feature-card__mockup` — SVG (inline, viewBox 240×400, Phone-Frame)
- `.feature-card__icon` — Inline SVG Icon
- `.feature-card__heading` — H3
- `.feature-card__text` — 1–2 Sätze

### Section 4: Freigabe-Workflow (dark bg)
```html
<div class="workflow__tabs" role="tablist">
  <button data-workflow="standard" role="tab">Standard</button>
  <button data-workflow="stellvertreter" role="tab">Mit Stellvertreter</button>
  <button data-workflow="ablehnung" role="tab">Mit Ablehnung</button>
</div>
<div id="workflow-stage" role="tabpanel" aria-live="polite">
  <!-- SVG gerendert von workflow.js -->
</div>
<div id="workflow-detail" aria-live="polite">
  <!-- Erklärungstext bei Node-Klick -->
</div>
```

### Section 5: Für wen? (warm bg)
- 3 Persona-Cards: AGT, Beauftragter, Wehrführer
- Größenindikator: 20–80 AGTs visuell dargestellt
- Begleittext: kein Enterprise-Tool, budget-bewusst

### Section 6: CTA/Kontakt (Feuerwehr-Rot bg)
Formspree-Formular:
- Name (required), Feuerwehr (required), E-Mail (required)
- AGT-Anzahl (Select: <20, 20-40, 40-60, 60-80, >80)
- Nachricht (optional, Textarea)
- Datenschutz-Checkbox (required)
- Submit-Button
- `#form-feedback` mit `aria-live="polite"` für Success/Error

### Footer
- Brand-Spalte + Links (Impressum, Datenschutz)
- `<details id="impressum">` + `<details id="datenschutz">` inline
- Copyright: „© 2025 Atemschutzbuch. Noch kein Produkt — eine Idee auf dem Prüfstand."

Scripts am Ende: `workflow.js`, `main.js`

---

## CSS-Architektur (`style.css`)

### Custom Properties
```css
:root {
  --color-base:          #1a1a1a;
  --color-base-soft:     #2d2d2d;
  --color-surface:       #f5f4f0;
  --color-surface-alt:   #ffffff;
  --color-accent:        #CC2222;
  --color-accent-hover:  #a81b1b;
  --color-accent-light:  rgba(204, 34, 34, 0.08);
  --color-text-primary:  #1a1a1a;
  --color-text-secondary:#555555;
  --color-text-muted:    #888888;
  --color-text-inverse:  #ffffff;
  --color-border:        #e0ddd8;

  --font-display: 'Fraunces', Georgia, serif;
  --font-body:    'Source Serif 4', Georgia, serif;

  /* Fluid type scale mit clamp() */
  --text-xs:   clamp(0.75rem,  0.7rem + 0.2vw,  0.875rem);
  --text-sm:   clamp(0.875rem, 0.8rem + 0.3vw,  1rem);
  --text-base: clamp(1rem,     0.95rem + 0.25vw, 1.125rem);
  --text-lg:   clamp(1.125rem, 1rem + 0.5vw,    1.375rem);
  --text-xl:   clamp(1.25rem,  1.1rem + 0.75vw,  1.75rem);
  --text-2xl:  clamp(1.5rem,   1.25rem + 1.25vw, 2.25rem);
  --text-3xl:  clamp(2rem,     1.5rem + 2vw,     3.25rem);
  --text-hero: clamp(2.5rem,   1.75rem + 3.5vw,  5rem);

  --space-1: 0.25rem; --space-2: 0.5rem; --space-3: 0.75rem;
  --space-4: 1rem; --space-6: 1.5rem; --space-8: 2rem;
  --space-12: 3rem; --space-16: 4rem; --space-20: 5rem; --space-24: 6rem;

  --container-max: 1200px;
  --container-pad: clamp(1rem, 5vw, 2.5rem);
  --section-pad:   clamp(3rem, 8vw, 7rem);

  --radius-sm: 4px; --radius-md: 8px; --radius-lg: 16px; --radius-xl: 24px;
  --shadow-sm: 0 1px 3px rgba(0,0,0,0.08);
  --shadow-md: 0 4px 16px rgba(0,0,0,0.10);
  --shadow-lg: 0 8px 32px rgba(0,0,0,0.14);
  --transition-fast: 150ms ease;
  --transition-base: 250ms ease;
  --transition-slow: 400ms ease;
}
```

### Layer-Reihenfolge
1. Custom Properties
2. CSS Reset / Base
3. Typografie-Scale
4. Layout-Utilities (`.container`, Grid-Helper)
5. Component-Styles (in Section-Reihenfolge)
6. Utility-Classes
7. `@media (min-width: 640px)` und `@media (min-width: 1024px)`

### Responsive Breakpoints
- Mobile-First Base: 0px+
- Tablet: `@media (min-width: 640px)` — 2-col Grids
- Desktop: `@media (min-width: 1024px)` — 3/4-col, Hero-Layout

### Button-System
```css
.btn { /* inline-flex, 2px border, font-weight 600, transition */ }
.btn--primary { background: var(--color-accent); color: white; }
.btn--ghost   { background: transparent; border-color: currentColor; }
.btn--sm { padding: var(--space-2) var(--space-4); font-size: var(--text-sm); }
.btn--lg { padding: var(--space-3) var(--space-8); font-size: var(--text-lg); }
```

### Scroll-Reveal (CSS-Seite)
```css
.reveal { opacity: 0; transform: translateY(24px); transition: opacity 0.5s ease, transform 0.5s ease; }
.reveal.is-visible { opacity: 1; transform: none; }
```

---

## SVG-Mockups (7 Stück, inline in Feature-Cards)

Jedes Mockup: `viewBox="0 0 240 400"`, Phone-Frame via `<rect rx="20">`, dekorativ (`role="img" aria-label="..."`).

| Feature | Mockup-Inhalt |
|---|---|
| Einsatz- & Übungserfassung | Input-Felder (Datum, Dauer, Verbrauch), roter Submit-Button |
| Freigabe-Workflow | Mini-Graph: 3 Knoten, Verbindungslinien, mittlerer pending |
| G26.3 Verwaltung | Tabelle: Name/G26.3/Gültig-bis, grüne Checks/rote X |
| Dashboard | Balkendiagramm + Stat-Cards |
| Benachrichtigungen | 3 Notification-Items mit Icon/Titel/Zeitstempel |
| Mandantenverwaltung | User-Liste mit farbigen Rollen-Badges |
| PDF/CSV Export | Export-Dialog: Format-Toggle, Datumsbereich, Export-Button |

Zeichnungskonventionen: `<rect rx>` für abgerundete Elemente, `<text font-family="sans-serif">` für Labels, `fill="var(--color-accent)"` für Akzente. Max. ~60 Zeilen pro SVG.

---

## Interaktiver Workflow-Graph (`workflow.js`)

### Datenstruktur
```javascript
const WORKFLOWS = {
  standard: {
    label: 'Standard-Workflow',
    nodes: [
      { id: 'agt',          label: 'AGT',          sublabel: 'Atemschutzgeräteträger',  x: 80, y: 60,  r: 32, detail: '...' },
      { id: 'beauftragter', label: 'Beauftragter', sublabel: 'Atemschutzbeauftragter', x: 80, y: 200, r: 32, detail: '...' },
      { id: 'freigabe',     label: 'Freigabe',     sublabel: 'Unveränderlich gespeichert', x: 80, y: 340, r: 32, detail: '...' }
    ],
    edges: [
      { from: 'agt', to: 'beauftragter', label: 'einreichen' },
      { from: 'beauftragter', to: 'freigabe', label: 'freigeben' }
    ]
  },
  stellvertreter: { /* AGT → Beauftr. ODER Stellvertr. → Freigabe */ },
  ablehnung:      { /* AGT → Beauftr. → Ablehnen → AGT (Kreis) ODER → Freigabe */ }
};
```

### SVG-Rendering (ohne externe Bibliothek)
- `document.createElementNS('http://www.w3.org/2000/svg', ...)` für alle Elemente
- `<defs>` mit `<marker id="arrowhead">` (normal + rot für Ablehnung)
- Kanten als `<path>` mit quadratischem Bézier:

```javascript
function edgePath(fromNode, toNode, offset = 0) {
  const dx = toNode.x - fromNode.x;
  const dy = toNode.y - fromNode.y;
  const len = Math.sqrt(dx*dx + dy*dy);
  const startX = fromNode.x + (dx/len) * fromNode.r;
  const startY = fromNode.y + (dy/len) * fromNode.r;
  const endX   = toNode.x   - (dx/len) * toNode.r;
  const endY   = toNode.y   - (dy/len) * toNode.r;
  const midX = (startX + endX) / 2 + offset * (-dy/len);
  const midY = (startY + endY) / 2 + offset * (dx/len);
  return `M ${startX} ${startY} Q ${midX} ${midY} ${endX} ${endY}`;
}
```

- Return-Kante (Ablehnung → AGT) mit `offset = 40` für sichtbare Umgehungskurve
- Knoten als `<g class="workflow-node" data-node-id>` → `<circle>` + `<text>` Label + Sublabel

### Interaktion
```javascript
function switchTab(key) { /* Tab aktiv setzen, renderWorkflow(key) */ }
function renderWorkflow(key) {
  stage.classList.add('is-transitioning');       // opacity: 0
  setTimeout(() => {
    stage.replaceChildren(buildSVG(WORKFLOWS[key]));
    stage.classList.remove('is-transitioning');
  }, 250);
}
function onNodeClick(nodeId, detail) {
  // .is-active setzen, Detail-Text in #workflow-detail injizieren
  detailEl.scrollIntoView({ behavior: 'smooth', block: 'nearest' }); // Mobile
}
```

---

## `main.js` — Verantwortlichkeiten

```javascript
(function() {
  'use strict';
  function initSmoothScroll() { /* <a href="#..."> abfangen */ }
  function initNavScroll()    { /* IntersectionObserver auf #hero → .is-scrolled */ }
  function initScrollReveal() { /* IntersectionObserver auf .reveal → .is-visible */ }
  function initFormHandler()  { /* fetch() POST, Success/Error, Constraint Validation */ }

  document.addEventListener('DOMContentLoaded', function() {
    initSmoothScroll();
    initNavScroll();
    initScrollReveal();
    initFormHandler();
  });
})();
```

Guard: `if (!window.IntersectionObserver) return;` in Reveal und Nav-Scroll.

---

## Implementierungsreihenfolge

**Phase 1 — Fundament**
1. `CLAUDE.md` ✓
2. `index.html` Skeleton (DOCTYPE, Head, leere Section-Stubs, Script-Tags)
3. `style.css` Custom Properties, Reset, Typografie, Container, Buttons, Section-Basis
4. `main.js` leere IIFE

**Phase 2 — Statische Sections**
5. Hero + Problem + Für wen + CTA/Kontakt HTML + CSS
6. Footer mit `<details>` Impressum/Datenschutz

**Phase 3 — Features + Mockups**
7. Features-Section HTML, 7 SVG-Mockups inline

**Phase 4 — Workflow**
8. Workflow-Section HTML (Tabs + Stage + Detail)
9. `workflow.js` (Daten → buildSVG → Tab-Logic → Node-Click)

**Phase 5 — JS-Polish**
10. `main.js` alle 4 Funktionen

---

## Verifikation

**Lokal testen:**
```bash
python3 -m http.server 8080
```
- DevTools: 375px / 768px / 1440px
- Alle 3 Workflow-Tabs, Node-Klick zeigt Detail-Text
- Form-Validierung (leere Felder, fehlende Checkbox)
- Kein horizontaler Overflow: `document.documentElement.scrollWidth === window.innerWidth`

**Qualitätsziele:**
- Lighthouse > 90 Performance + Accessibility
- Gesamtgröße < 300KB (HTML + CSS + JS + inline SVGs)
- Google Fonts mit `display=swap`

**Deployment:**
- Merge auf `main` → Cloudflare Pages Auto-Deploy
- Build command: leer; Output directory: `/`
- Formspree-Placeholder nach Account-Einrichtung ersetzen
