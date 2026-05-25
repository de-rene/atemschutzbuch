---
name: design-system
description: Abgenommenes Design-System für den Atemschutzbuch One-Pager, Stand 2026-05-25
metadata:
  type: project
---

Design abgenommen in REN-48 (2026-05-24), iteriert in REN-35-Session (2026-05-25).

**Typografie:** DM Sans, vollständig serifenlos. Kein zweiter Font.

**Farben:**
- Akzent: `#dc2626` (Rot)
- Dunkel: `#0f0f0f`
- Hell: `#f9fafb`
- Weiß: `#ffffff`
- Text gedämpft: `#6b7280`

**Produktionsdatei:** `website/index.html` — deployed via Cloudflare Pages aus `website/`.

**Layout:** Seite als gerundete Box (`border-radius: 14px`, `overflow: hidden`) mit grauem Body-Hintergrund (`#d4d4d4`, `padding: 2rem 5%`).

**Hero:** Split-Grid (1fr 1fr). Links: Copy + CTA. Rechts: App-Mockup, Hintergrund `#fff` (gleich wie links).

**Hero App-Mockup:** Browser-Window (`max-width: 580px`) mit Chrome-Bar (Traffic-Lights + URL-Leiste), Sidebar-Navigation (Einsätze / Übungen / AGTs / Dashboard) und Detailansicht eines Einsatzes. Dunkler Schatten (`box-shadow: 0 12px 48px rgba(0,0,0,0.28)`). Light/Dark-Switcher (☀️/🌙) positioniert absolut oben rechts in der Hero-Box — schaltet nur das Browser-Fenster, nicht den Hintergrund. Default: Dark Mode.

**Hero Eyebrow:** `FwDV 7 · §14 GefStoffV · DSGVO-konform` (normale Schreibweise, kein uppercase)

**Trust-Badges:** Entfernt (wurden komplett aus der Seite genommen, 2026-05-25).

**CTA-Button:** „Kontakt aufnehmen" (ehemals „Jetzt vormerken").

**Eyebrows (alle roten Unterüberschriften):** `text-transform: none` — normale Groß-/Kleinschreibung, kein ALL-CAPS.

**Logo:** `website/logo.png` (kopiert aus Repo-Root). Icon 76px, Wortmarke 1.625rem/800, `margin-left: -0.375rem` (Text nah am Icon).

**Wortmarke:** `Atemschutz` (dunkel) + `buch` (#dc2626).

**Kein Nav-Menü** — One-Pager braucht keines. Nur Logo + Wortmarke in eigenem Bereich unter dem roten Top-Streifen.

**Section-Hintergründe (Reihenfolge):**
1. Top-Bar → `#dc2626` (leer, nur als roter Akzentstreifen)
2. Logo-Bereich → `#ffffff`
3. Hero → `#ffffff` beidseitig
4. Problem → `#f9fafb`
5. Features → `#ffffff`
6. Workflow → `#0f0f0f`
7. Für wen → `#f9fafb`
8. FAQ → `#ffffff`
9. CTA → `#dc2626`
10. Footer → `#0f0f0f`

**Problem-Section (4 Cards):**
1. Handschrift unleserlich
2. Lücken im Buch
3. Freigabe dauert
4. Haftung bei der Gemeinde (§14 GefStoffV, 40 Jahre)

**FAQ-Section:** 3 aufklappbare Fragen (`<details>`/`<summary>`, kein JS). Themen: §14 GefStoffV Rechtssicherheit, Hardware-Anforderungen, Datenschutz/DSGVO.

**Footer:** `Made with ❤️ in Lemgo` — kein weiterer Inhalt.

**Stimmung:** Modern + Zuverlässig. SaaS-artig, kein Klischee-Feuerwehr-Look.

**Why:** Trust-Badges entfernt weil redundant (Eyebrow trägt dieselbe Info). Uppercase entfernt auf Wunsch — wirkt ruhiger. CTA-Text geändert weil „vormerken" zu unverbindlich klingt für Validierungszweck.

**How to apply:** Vor jeder Design- oder CSS-Entscheidung diese Tokens verwenden. Kein „Offline-fähig" ohne explizite Produktentscheidung.
