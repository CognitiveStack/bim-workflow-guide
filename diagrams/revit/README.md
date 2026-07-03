# Revit Diagrams — Exports & Versioning

This folder holds the **Revit-authored coordination diagram** and its published exports.

> **Revit is the visual authoring environment. PNG exports are the version-controlled visual artifacts. Markdown is the long-form explanation.**

## How versioning works here

- The source Revit model (`.rvt`) is **not committed to Git** by default — Revit files are binary and do not diff usefully. See [docs/versioning-and-exports.md](../../docs/versioning-and-exports.md).
- The **PNG/PDF exports** under `exports/` are the Git-versioned visual artifacts.
- Future `.rvt` versioning may use an external archive folder or **Git LFS** if needed.

## Exports

| Diagram ID | File | Version | Purpose | Notes |
|---|---|---|---|---|
| BIM-001 | [`exports/ad-coordination-workflow-v06.png`](exports/ad-coordination-workflow-v06.png) | v06 | Autodesk Coordination Workflow — overview teaching diagram | **Current.** Higher-resolution, cleaner export (3785×1495) |
| BIM-001 | [`exports/ad-coordination-workflow-v05.png`](exports/ad-coordination-workflow-v05.png) | v05 | Autodesk Coordination Workflow — overview teaching diagram | Superseded by v06; first committed export |

## Current diagram

![Autodesk Coordination Workflow](exports/ad-coordination-workflow-v06.png)

*Autodesk Coordination Workflow — Revit-generated 3D teaching diagram showing consultant models, contractor models, Design Collaboration, the Common Data Environment, Model Coordination, RFIs, Issues, and the Federated Model.*

Explained in the [README guide](../../README.md).
