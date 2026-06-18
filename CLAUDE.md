# Atemschutzbuch

## Arbeitsanweisung

Kein Code schreiben, bevor es nicht explizit angewiesen wird. Nicht danach fragen.

---

## Projekt

Digitales Atemschutzbuch für kleine freiwillige Feuerwehren (20–80 AGTs).
Open Source / Self-hosted (Repo vorerst privat). Aktuelles Ziel: Bedarfsvalidierung via One-Pager Landing Page.

Linear: https://linear.app/renek/project/atemschutzbuch-8cc8404438af

---

## Repo-Struktur (Monorepo)

```
/
├── website/   ← GitHub Pages (Branch: main, Folder: /website)
├── app/       ← Später: App → VPS, Self-hosted (Docker)
└── CLAUDE.md
```

---

## GitHub Pages

> Ablöst Cloudflare Pages (Grundsatzentscheidung 2026-06-18: OSS/Self-hosted). Einrichtung → REN-125. CF Pages löschen & Account schließen → REN-124.

| Einstellung | Wert |
|---|---|
| Branch | `main` |
| Folder | `/website` |
| URL (default) | `https://de-rene.github.io/atemschutzbuch/` |
| Custom Domain | `atemschutzbuch.de` (optional, → REN-55) |
| Build | *(kein Build-Step, plain HTML)* |

---

## Tech-Constraints (website/)

- Plain HTML + CSS + vanilla JS — kein Framework, kein Build-Step
- Google Fonts CDN: DM Sans
- Scripts am Ende von `<body>`

---

## Design-Tokens

| Token | Wert |
|---|---|
| `--color-accent` | `#dc2626` |
| `--color-dark` | `#0f0f0f` |
| `--color-surface` | `#f9fafb` |
| `--color-muted` | `#6b7280` |
| `--font` | DM Sans (vollständig serifenlos, kein zweiter Font) |

---

## Branch-Strategie

- `main` = production
- Feature-Branches → PR → merge nach `main`

---

## Lokale Entwicklung

```bash
cd website/
python3 -m http.server 8080
```

Node.js ist nicht installiert — kein `npm`, `node` oder Node-basierter Dev-Server.
