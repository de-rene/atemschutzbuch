---
name: feedback-linear-assignee
description: Linear Issues immer René zuweisen
metadata:
  type: feedback
---

Neu erstellte Linear Issues immer René (assignee: "me") zuweisen.

**Why:** René ist der einzige Nutzer im Workspace, explizite Anweisung.

**How to apply:** Bei jedem `save_issue`-Aufruf `assignee: "me"` setzen, auch wenn nicht explizit erwähnt.
