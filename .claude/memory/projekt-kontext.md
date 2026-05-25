---
name: projekt-kontext
description: Ziel, Struktur, Tech-Stack, Meilensteine und Interview-Erkenntnisse des Atemschutzbuch-Projekts
metadata:
  type: project
---

Digitales Atemschutzbuch für freiwillige Feuerwehren (Größe offen). Aktuelles Ziel: Bedarfsvalidierung via One-Pager Landing Page (Milestone M1).

**Repo-Struktur (Monorepo):**
- `website/` → Cloudflare Pages (Plain HTML + CSS + Vanilla JS, kein Framework)
- `app/` → Später: VPS (Coolify / GitHub Actions)
- `logo.png` → Repo-Root, Canva C4-Variante

**Linear:** https://linear.app/renek/project/atemschutzbuch-8cc8404438af

**M1-Tickets:**
- REN-48: Design Festlegung → Done (2026-05-24)
- REN-35: One-Pager Konzept & Struktur → In Progress (website/index.html implementiert, 2026-05-25)
- REN-54: Light/Dark Mode → Backlog, Low (Prototyp in Landing Page eingebaut)
- REN-36: One-Pager Design & Implementierung
- REN-37: Freigabe-Workflow interaktiv
- REN-38: SVG App-Mockups
- REN-39: GitHub Repo & Cloudflare Pages Setup — CF Pages noch nicht eingerichtet
- REN-40: Bedarfsvalidierung Interviews (internes Interview done 2026-05-24)
- REN-53: Website-Fragebogen (ausfüllbar/versendbar)

**Backlog-Tickets (App):**
- REN-41: Einsatz- & Übungserfassung (FwDV-7-Pflichtfelder vollständig)
- REN-42: Konfigurierbarer Freigabe-Workflow (mehrstufig)
- REN-43: G26.3 & Belastungsübung Verwaltung
- REN-44: Dashboard & Auswertungen
- REN-45: Benachrichtigungen & Erinnerungen
- REN-46: Mandantenverwaltung & Rollensystem
- REN-47: PDF/CSV Export
- REN-49: KoAtEx-Dok / §14 GefStoffV Expositionsdokumentation
- REN-50: Onboarding-Wizard
- REN-51: Preisgestaltung & Kalkulation
- REN-52: Automatisiertes Abrechnungssystem

**Rechtlicher Rahmen (aus Domain-Interview 2026-05-24):**
- FwDV 7: Atemschutznachweis Pflichtfelder (Datum, Einsatzstelle, Dauer, Maske-Nr., Gerät-Nr., Gerätetyp)
- §14 GefStoffV + KoAtEx-Dok: Expositionsverzeichnis Pflicht, 40 Jahre, Gemeinde haftet
- G26.3: Datum + Bestanden/Nicht bestanden, gleiche Bestätigungshierarchie
- Freigabe-Berechtigte: Gruppenführer, Löschzugführer, Wehrführer, Feuerwehrverwaltung

**Pricing-Modell (beschlossen 2026-05-24):**
- Pro aktivem (tauglichem) AGT, jährlich, 12-Monats-Zyklen
- Monatlich kündbar, Abrechnung automatisiert (Stripe o.ä.)

**Entscheidungsprozess Kunden:**
- Wehrführung entscheidet, braucht Budget + IT-Freigabe der Gemeinde
- Haupthindernisse: DSGVO, IT-Sicherheit, SaaS-Skepsis

**Cloudflare Pages:** Noch nicht eingerichtet (Stand 2026-05-25). Wenn eingerichtet: zunächst Zugriff beschränken (CF Access oder Password), erst bei Fertigstellung öffentlich schalten (REN-55).

**Why:** M1 ist Validierungsphase — erst One-Pager live, dann App bauen. Domain-Interview hat §14 GefStoffV als unbekanntes aber starkes Compliance-Argument bestätigt.

**How to apply:** Kein Code ohne explizite Anweisung. Design-Entscheidungen aus [[design-system]] gelten. §14 GefStoffV / KoAtEx-Dok ist zentrales Verkaufsargument — immer hervorheben.
