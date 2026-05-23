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

| Einstellung | Wert |
|---|---|
| Root directory | `website` |
| Build command | *(leer)* |
| Build output directory | `website` |
| Build watch paths | `website/**` |

---

## Tech-Constraints (website/)

- Plain HTML + CSS + vanilla JS — kein Framework, kein Build-Step
- Google Fonts CDN: Fraunces (Headings) + Source Serif 4 (Body)
- Scripts am Ende von `<body>`

---

## Design-Tokens

| Token | Wert |
|---|---|
| `--color-base` | `#1a1a1a` |
| `--color-surface` | `#f5f4f0` |
| `--color-accent` | `#CC2222` |
| `--font-display` | Fraunces, Georgia, serif |
| `--font-body` | Source Serif 4, Georgia, serif |

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
