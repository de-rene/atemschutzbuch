---
name: projekt-kontext
description: Ziel, Struktur und Tech-Stack des Atemschutzbuch-Projekts
metadata:
  type: project
---

Digitales Atemschutzbuch für kleine freiwillige Feuerwehren (20–80 AGTs). Aktuelles Ziel: Bedarfsvalidierung via One-Pager Landing Page (Milestone M1).

**Repo-Struktur (Monorepo):**
- `website/` → Cloudflare Pages (Plain HTML + CSS + Vanilla JS, kein Framework)
- `app/` → Später: VPS (Coolify / GitHub Actions)
- `logo.png` → Repo-Root, Canva C4-Variante

**Linear:** https://linear.app/renek/project/atemschutzbuch-8cc8404438af

**Aktuelle Tickets (M1):**
- REN-48: Design Festlegung → abgeschlossen 2026-05-24
- REN-35: One-Pager Konzept & Struktur (6 Sections)
- REN-36: One-Pager Design & Implementierung
- REN-37: Freigabe-Workflow interaktiv
- REN-38: SVG App-Mockups

**Why:** M1 ist Validierungsphase — erst One-Pager live, dann App bauen.

**How to apply:** Kein Code ohne explizite Anweisung. Alle Design-Entscheidungen wurden in REN-48 abgenommen — [[design-system]] gilt als Grundlage für REN-35/REN-36.
