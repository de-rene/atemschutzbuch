---
name: design-system
description: Abgenommenes Design-System für den Atemschutzbuch One-Pager (REN-48), mit Humanisierungsiteration aus REN-35-Brainstorming
metadata:
  type: project
---

Design wurde in REN-48 vom Nutzer abgenommen (2026-05-24). Humanisierung (Hero App-UI, Copy) in REN-35-Session iteriert.

**Typografie:** DM Sans, vollständig serifenlos. Kein zweiter Font.

**Farben:**
- Akzent: `#dc2626` (Rot)
- Dunkel: `#0f0f0f`
- Hell: `#f9fafb`
- Weiß: `#ffffff`
- Text gedämpft: `#6b7280`

**Layout Hero:** Split — Text/CTA links, dunkles App-Mockup rechts.

**Hero App-Mockup (humanisiert):** Realistisches App-UI mit echten Feldern (Einsatzstelle, Einsatzart, Dauer, Maske·Gerät, AGT, Freigabe-Status) — kein abstraktes Punkte/Balken-Mockup mehr. Inhalte: FF Lemgo, 24.05.2026, Brandeinsatz.

**Hero Eyebrow:** `FwDV 7 · §14 GefStoffV · DSGVO-konform`

**Trust-Badges (Hero):** Nur FwDV 7 und DSGVO. „Offline-fähig" wurde entfernt — keine bewusste Produktentscheidung.

**Logo:** Rote Kreismarke mit Atemschutzmaske (`logo.png` im Repo-Root). Icon links neben Wortmarke, gap 0, Icon 64px, Schriftzug 1.375rem/800.

**Wortmarke:** `Atemschutz` (dunkel) + `buch` (#dc2626).

**Section-Hintergründe (Reihenfolge):**
1. Top-Bar → `#dc2626`
2. Nav → `#ffffff`
3. Hero → `#ffffff` links / `#0f0f0f` rechts
4. Problem → `#f9fafb`
5. Features → `#ffffff`
6. Workflow → `#0f0f0f`
7. Für wen → `#f9fafb`
8. CTA → `#dc2626`
9. Footer → `#0f0f0f`

**Problem-Section (4 Cards):**
1. Handschrift unleserlich
2. Lücken im Buch
3. Freigabe dauert
4. Haftung bei der Gemeinde (§14 GefStoffV, 40 Jahre) — ersetzt "Papierverlust"

**Problem-Section Intro-Copy:** Betont Gemeinde-Haftung und §14 GefStoffV als zentrales Argument.

**Footer:** `Made with ❤️ in Lemgo` — kein weiterer Inhalt.

**Stimmung:** Modern + Zuverlässig. SaaS-artig, kein Klischee-Feuerwehr-Look. Humanisiert durch echten Datensatz statt generische Platzhalter.

**Aktuelles Mockup:** `.superpowers/brainstorm/one-pager-v1.html` — vollständiger One-Pager mit allen Sections.

**Why:** Offline-fähig wurde nie als Feature beschlossen. 4. Problem-Card auf §14-GefStoffV-Haftung geändert weil das das stärkste und unbekannteste Argument ist.

**How to apply:** Vor jeder Design- oder CSS-Entscheidung diese Tokens verwenden. Kein „Offline-fähig" mehr einbauen ohne explizite Produktentscheidung.
