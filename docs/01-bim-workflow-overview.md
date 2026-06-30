# 01 — BIM Workflow Overview

## What this topic means

The **BIM workflow** is the full journey that building information takes — from the moment a design team starts modelling, through coordination and construction, to the day the finished model and its data are handed to the owner.

It is bigger than any single tool or task. Authoring a model, federating models, detecting clashes, managing issues, and producing as-built records are all *parts* of the BIM workflow.

A common beginner mistake is to think "BIM = clash detection." It isn't. Clash detection is one step. The workflow hierarchy looks like this:

```
BIM Workflow
└─ BIM Coordination
   └─ Federated Models
      └─ MEP Coordination
         └─ Clash Detection
            └─ Issue Management
               └─ Model Updates
                  └─ Construction Support
                     └─ As-Built / Owner Handover
```

## Why it matters

On a real project, many disciplines design at the same time and each builds its own model. Without a workflow that brings those models together, conflicts are only discovered on site — where fixing them is slow and expensive.

A clear BIM workflow:
- keeps every team working from coordinated information,
- catches conflicts early (in the model, not on site),
- creates a reliable record for construction and handover,
- and gives the owner accurate information about what was actually built.

## Where it fits in the workflow

This overview is the **map for the whole repo**. Every other document zooms into one stage:

| Stage | Where to read more |
|---|---|
| Federated model | `02-federated-models.md` |
| MEP coordination | `03-mep-coordination.md` |
| Clash detection | `04-clash-detection.md` |
| Cloud coordination (Forma) | `05-forma-model-coordination.md` |
| Navisworks coordination | `06-navisworks-workflow.md` |
| Automation (Revit MCP) | `07-revit-mcp-automation.md` |

## Typical tools involved

- **Revit** — authoring architectural, structural, and MEP models.
- **Civil 3D** — authoring site and civil models.
- **Autodesk Forma** — cloud Data Management, Design Collaboration, and Model Coordination.
- **Navisworks Manage** — federating models and running detailed clash detection.
- **Autodesk Construction Cloud** — the wider cloud environment connecting design and construction.
- **GitHub** — (here) documenting and version-controlling the workflow itself.

## The stages, end to end

1. **Discipline models** — each team owns its own model.
2. **Authoring tools** — models are created in Revit, Civil 3D, etc.
3. **Publish models** — teams publish to a shared cloud location.
4. **Design packages** — published models are organized for sharing.
5. **Model coordination space** — a cloud space where all models meet.
6. **Federated model** — models combined into one coordinated view.
7. **Coordination review** — teams review the combined model together.
8. **Clash detection** — automatic checks find conflicts and clearance issues.
9. **Issues assigned** — each problem becomes a tracked issue.
10. **Model updates** — teams fix their models; the cycle repeats.
11. **Shop drawings** — coordinated models drive fabrication/installation drawings.
12. **Construction / installation** — the building is built.
13. **As-built updates** — models updated to match what was built.
14. **Owner handover** — final model and asset data delivered to the owner.

## Simple example

Imagine a small **fire station** project:

- The **architect** models the building shell and rooms in Revit.
- The **structural engineer** models the columns, beams, and slabs.
- The **MEP engineer** models ducts, pipes, cable trays, and the sprinkler system.
- The **civil engineer** models the site, parking, and drainage in Civil 3D.

Each team publishes its model into a shared **coordination space**. The models are combined into a **federated model**. A coordination review and **clash detection** reveal that a large supply duct runs straight through a structural beam. That conflict becomes an **issue**, assigned to the MEP team. They reroute the duct, **update** their model, and the federated model refreshes. Once everything fits, the coordinated information feeds **shop drawings** and **construction**, and the **as-built** model is handed over to the owner.

That whole story — not just the duct-versus-beam check — is the BIM workflow.

---

*Next: [02 — Federated Models](02-federated-models.md). New to the terms? See the [Glossary](glossary.md).*
