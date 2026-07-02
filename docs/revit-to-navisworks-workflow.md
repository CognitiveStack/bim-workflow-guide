# Revit → Navisworks Workflow

## Key idea

**Revit is where the model is authored and changed. Navisworks is where the federated model is reviewed and clashes are detected.**

- **NWC** files are exported snapshots / caches from Revit.
- **NWF** is the Navisworks working file that references the NWC files.
- **NWD** is a published, frozen model.

## Workflow

1. Open the correct Revit discipline model.
2. Make the design or coordination change.
3. Export a fresh NWC.
4. Overwrite the old NWC in the Navisworks cache folder.
5. Open or refresh the Navisworks NWF.
6. Rerun the clash test.
7. Confirm whether the clash is resolved.

## Folder logic

| Folder | Holds |
|---|---|
| `/revit/current/` | the live working Revit models |
| `/navisworks/02_NWC_Cache/` | exported NWC snapshots |
| `/navisworks/03_NWF_Working/` | Navisworks working files |

## Do not treat the NWC as the source model

The **RVT is the authoring source.** The NWC is an **exported coordination snapshot**. If a clash is found, you fix it in Revit and re-export the NWC — you never "fix" the NWC directly.

## Relationship to Forma Model Coordination

Navisworks is a **desktop coordination workbench** — strong for deep, detailed clash analysis, viewpoints, and reports. Forma **Model Coordination** is **collaboration-first** — strong for shared, cloud-based, trackable coordination across the whole team. They complement each other; see [Forma Model Coordination](forma-model-coordination.md).

---

*See also: [Federated Model callout](callouts/06-federated-model.md) · [Forma Model Coordination](forma-model-coordination.md) · [versioning and exports](versioning-and-exports.md)*
