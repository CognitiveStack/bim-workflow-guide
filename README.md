# CogStack BIM Coordination Workflow

This repo documents a modern **Autodesk-focused BIM coordination workflow** using Revit, Forma / ACC, Design Collaboration, Model Coordination, Navisworks, Issues, RFIs, and federated model handover.

## How this started

I built this to teach myself — and then others — how a modern BIM coordination workflow actually fits together. Too often "BIM coordination" is used as if it only means clash detection; I wanted one picture that shows the whole thing, from design through construction to operation, with the cloud running through all of it.

The spark was a diagram by **Jeffrey Pinheiro — The Revit Kid** — from his video ["3D Coordination Explained"](https://www.youtube.com/watch?v=2JOGvY9YplY&t=2991s):

![The diagram that inspired this project — by The Revit Kid](diagrams/inspiration/revit-kid-bim-coordination-workflow-original.png)

*Original diagram by Jeffrey Pinheiro (The Revit Kid), using Turner's White Plains Hospital project as the worked example. [Full credit](diagrams/inspiration/README.md).*

In his diagram, the blue **"Turner"** spine is the Construction Manager / General Contractor — the hub everything flows through. What struck me is that in a modern cloud workflow **that spine is replaced by the cloud itself**. So I rebuilt it: the spine became the **Common Data Environment**, made Autodesk-centric by the two blue **Forma** workflows sitting on it — **Design Collaboration** and **Model Coordination** (Forma was formerly ACC). And because my Revit skills are modest, I built the 3D model with the [pyRevit MCP server](https://github.com/CognitiveStack/revit-mcp-server).

> *Revit produces the diagram. Markdown explains the diagram. GitHub versions the learning system.*

---

## The result — Autodesk Coordination Workflow

![Autodesk Coordination Workflow](diagrams/revit/exports/ad-coordination-workflow-v06.png)

*Autodesk Coordination Workflow — my Revit-generated 3D teaching diagram: consultant models, contractor models, Design Collaboration, the Common Data Environment, Model Coordination, RFIs, Issues, and the Federated Model.*

## 📖 Read the full guide

Everything — the origin story, the diagram walkthrough, the six callouts, the feedback loop, Forma Model Coordination, Revit → Navisworks, Construction vs Operations, and non-obvious coordination risks — is on one page:

### → **[The Autodesk BIM Coordination Workflow — Complete Guide](docs/guide.md)**

---

## Reference pages

- [Glossary](docs/glossary.md) — key BIM terms
- [Revit 3D diagram build runbook](docs/08-revit-3d-workflow-diagram-plan.md) · [Build prompt](docs/08-revit-build-prompt.md) — how the diagram was built (pyRevit MCP)
- [Versioning & exports](docs/versioning-and-exports.md) — how diagrams and docs are version-controlled
- [Diagram exports & credit](diagrams/revit/README.md) · [Inspiration & credit](diagrams/inspiration/README.md)
- [PRD](PRD.md) — product requirements
- [Related CogStack repos](links/related-repos.md) · [Learning resources](links/learning-resources.md) *(coming soon)*
- Examples: [Harrismith Fire Station](examples/harrismith-fire-station/README.md) *(coming soon)* · [BIM Clash Visual Atlas](examples/bim-clash-visual-atlas/README.md) *(coming soon)*

---

## Versioning strategy

- **Revit `.rvt`** = diagram authoring file (not committed to Git — binary, no useful diffs; excluded via `.gitignore`).
- **PNG / PDF exports** = version-controlled visual artifacts under `diagrams/revit/exports/`.
- **Markdown docs** = explanation / source of truth.
- **GitHub** = versioned educational repo / website source.

See [docs/versioning-and-exports.md](docs/versioning-and-exports.md).

## Roadmap

- **Phase 1 (done):** Foundation — repo scaffold, first diagram, glossary.
- **Phase 2 (done):** The Revit-generated diagram becomes the primary artifact, explained in Markdown.
- **Phase 3 (this update):** Consolidated into a single-page [guide](docs/guide.md) with reference pages alongside.
- **Phase 4:** Worked examples — Harrismith Fire Station, BIM Clash Visual Atlas.

See [PRD.md](PRD.md) for the full product requirements.
