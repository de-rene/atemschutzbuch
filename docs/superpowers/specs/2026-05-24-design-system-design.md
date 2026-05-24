# Design System — Atemschutzbuch

**Datum:** 2026-05-24  
**Status:** Abgeschlossen, genehmigt  
**Ticket:** REN-48

---

## Entscheidungen

### Stimmung
Modern + Zuverlässig. Kein klischeehaftes Feuerwehr-Design, sondern ein professionelles SaaS-Produkt das Vertrauen signalisiert.

### Layout (One-Pager Hero)
Split Hero: Text und CTAs links, dunkles App-Mockup rechts. Zeigt das Produkt sofort ohne es beschreiben zu müssen.

### Typografie
**DM Sans** — durchgehend serifenlos. Weicher und freundlicher als Inter, weniger korporativ.

- Google Fonts CDN: `DM Sans` (400, 500, 600, 700, 800)
- Kein zweiter Font.

### Farben

| Token | Wert | Verwendung |
|---|---|---|
| `--color-accent` | `#dc2626` | CTAs, Labels, Akzente, Logo |
| `--color-accent-hover` | `#b91c1c` | Hover-States |
| `--color-base` | `#0f0f0f` | Hero-Hintergrund, Footer, App-Mockup |
| `--color-surface` | `#f9fafb` | Problem-Section, Für-wen-Section |
| `--color-surface-alt` | `#ffffff` | Nav, Features-Section, Cards |
| `--color-text` | `#0f0f0f` | Fließtext auf hell |
| `--color-text-muted` | `#6b7280` | Subtexte, Beschreibungen |
| `--color-text-inverse` | `#ffffff` | Text auf dunklem Hintergrund |
| `--color-border` | `#e5e7eb` | Card-Borders |

### Section-Hintergründe (in Reihenfolge)

1. **Top-Bar** → `#dc2626` (rot)
2. **Nav** → `#ffffff`
3. **Hero** → `#ffffff` (Split: links weiß, rechts `#0f0f0f`)
4. **Problem** → `#f9fafb`
5. **Features** → `#ffffff`
6. **Workflow** → `#0f0f0f`
7. **Für wen** → `#f9fafb`
8. **CTA** → `#dc2626`
9. **Footer** → `#0f0f0f`

### Logo

- **Icon:** Rote Kreismarke mit stilisierter Atemschutzmaske (Canva-generiert, C4-Variante)
- **Datei:** `logo.png` im Repo-Root
- **Wortmarke:** `Atemschutz` + `buch` (buch in `#dc2626`)
- **Kombination:** Icon links, Wortmarke rechts, gap 0 (Whitespace im Bild dient als Abstand)
- **Nav-Größe:** Icon 64×64px, Schriftzug 1.375rem / 800 weight

### Buttons

```css
.btn--primary { background: #dc2626; color: #fff; border-radius: 8px; }
.btn--ghost   { color: #374151; font-weight: 500; }
.btn--sm { padding: 0.5rem 1.1rem; font-size: 0.775rem; }
.btn--lg { padding: 0.625rem 1.375rem; font-size: 0.875rem; }
```

### Trust-Badges (Hero)
Drei grüne Checkmarks: **FwDV 7** · **DSGVO** · **Offline-fähig**

### Announcement-Bar
Roter Streifen ganz oben mit Beta-Hinweis + Pill-Badge.

### Cards (Problem-Section)
Weißer Hintergrund, `border: 1px solid #e5e7eb`, `border-top: 3px solid #dc2626`, `border-radius: 0 0 8px 8px`.

### Footer
```
Made with ❤️ in Lemgo
```
Hintergrund `#0f0f0f`, Text `rgba(255,255,255,0.28)`.

---

## Mockup-Dateien

Alle unter `.superpowers/brainstorm/`:

| Datei | Inhalt |
|---|---|
| `font-dm-final.html` | **Finales Mockup** — vollständiger One-Pager-Entwurf |
| `design-direction.html` | Frühe Layout-Entscheidung (A/B/C) |
| `font-comparison.html` | Font-Vergleich Inter / DM Sans / Geist |
| `logo-v3.html` | SVG-Logo-Konzepte v3 |

---

## Noch offen (nicht Teil dieses Tickets)

- Fluid Typography Scale (`clamp()`) → REN-36
- Mobile-Breakpoints → REN-36
- SVG App-Mockups (Features-Section) → REN-38
- Interaktiver Workflow-Graph → REN-37
