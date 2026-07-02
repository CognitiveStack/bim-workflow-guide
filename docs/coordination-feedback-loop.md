# Coordination Feedback Loop

## The BIM coordination workflow is not linear

Coordination is **iterative**. Model Coordination finds clashes and coordination risks. Important problems become **Issues** or **RFIs**. The responsible team updates the source model. The model is republished into the CDE. The model is re-coordinated. The loop repeats until the issue is resolved.

> **Find → Raise → Fix → Republish → Re-coordinate**

The diagram shows two feedback loops: the **RFI loop** and the **Issues loop**.

## RFI loop

A coordination review identifies a question that needs design input. The **RFI** goes back to the consultants / design model authors. The consultants respond, revise the design if needed, and republish through **Design Collaboration** into the CDE.

**Example:** A duct route appears to require a beam penetration. The contractor cannot approve this alone. The question becomes an RFI to the structural / design team.

## Issues loop

Model Coordination identifies a construction or trade coordination problem. The **Issue** goes back to the contractor / trade model authors. The trade team updates the model and republishes it into the CDE.

**Example:** A mechanical duct clashes with a cable tray. The issue is assigned to the relevant trade team. The trade model is updated and re-coordinated.

## Important: the loops return to the model authors, not just the CDE

The return arrows should **not** be explained as returning to the CDE only. The CDE stores and manages information, but **people fix models**. The loops return to the model authors. Their updated models then flow forward again into the CDE.

| Thing | What it does |
|---|---|
| **CDE** | Stores, versions, routes, and records information |
| **Model authors** | Fix the source models |
| **Model Coordination** | Tests the shared / federated model environment |
| **Issues and RFIs** | Create accountable feedback loops |

## Short summary

> **Find → Raise → Fix → Republish → Re-coordinate → Verify**

---

*See also: [workflow overview](workflow-overview.md) · [Model Coordination callout](callouts/05-model-coordination.md) · [non-obvious coordination risks](coordination-risks/non-obvious-clashes.md)*
