# Versioning and Exports

## The philosophy

> **Revit produces the diagram. Markdown explains the diagram. GitHub versions the learning system.**

The Revit `.rvt` file is the **visual authoring environment**. The **GitHub repo is the documentation source of truth.**

## Why the .rvt is not the main Git artifact

Revit files are **binary**. Git can store them, but it cannot produce useful line-by-line diffs, so committing the `.rvt` gives you size and noise without meaningful version history.

Instead, the repo versions the things Git is good at:

| Artifact | Role | In Git? |
|---|---|---|
| Revit `.rvt` | Diagram authoring file | No (archived separately, or Git LFS later if needed) |
| PNG / PDF exports | Published visual artifacts | **Yes** |
| Markdown docs | Explanation / source of truth | **Yes** |
| GitHub | Versioned educational repo / website source | — |

Git versions the **exported diagrams** and the **Markdown docs**. The Revit source file can be archived separately or later managed with **Git LFS** if binary versioning becomes necessary.

## Excluded binaries

Autodesk binaries are excluded from Git by default (see `.gitignore`): `.rvt`, `.rfa`, `.nwc`, `.nwf`, `.nwd`, and similar. Do not commit these unless explicitly requested.

## Naming and referencing

- Exports live under [`diagrams/revit/exports/`](../diagrams/revit/README.md).
- Preferred naming pattern: `ad-coordination-workflow-v06.png` (lowercase, versioned).
- Markdown pages reference the **current** diagram version. When a new export supersedes it, update the references and record the new version in the [exports table](../diagrams/revit/README.md).

The current primary Phase 2 diagram is **`ad-coordination-workflow-v06.png`**.

---

*See also: [diagrams/revit README](../diagrams/revit/README.md) · [README guide](../README.md)*
