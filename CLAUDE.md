# Atemschutzbuch

## Arbeitsanweisung

Kein Code schreiben, bevor es nicht explizit angewiesen wird. Nicht danach fragen.

---

## Projekt

Digitales Atemschutzbuch für kleine freiwillige Feuerwehren (20–80 AGTs).
Aktuelles Ziel: Bedarfsvalidierung via One-Pager Landing Page.

Linear: https://linear.app/renek/project/atemschutzbuch-8cc8404438af

---

## Repo-Struktur (Monorepo)

```
/
├── website/   ← CF Pages (Root: website/, Watch: website/**)
├── app/       ← Später: App → VPS (Coolify oder GitHub Actions)
└── CLAUDE.md
```

---

## Cloudflare Pages

> **Noch nicht eingerichtet** (Stand 2026-05-25). Sobald aktiv: Zugriff zunächst auf interne Nutzer beschränken (CF Access oder Password-Protection). Öffentliche Live-Schaltung → REN-55.



| Einstellung | Wert |
|---|---|
| Root directory | `website` |
| Build command | *(leer)* |
| Build output directory | `website` |
| Build watch paths | `website/**` |

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
