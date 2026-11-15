# Lightweight Quadcopter Arm — Structural Optimisation

**Autodesk Fusion 360 | CAD design and static finite element analysis | November 2026**

A short aerospace engineering portfolio project comparing a baseline solid drone arm with an optimised version containing three rounded through-slots.

![CAD designs](Results/CAD_Comparison.png)

## Objective and result

**Question:** Can the arm be made lighter without falling below a static factor of safety of **2** or exceeding **2 mm** total deflection under a **15 N upward motor load**?

| Metric | Baseline arm | Optimised arm | Result |
|---|---:|---:|---|
| CAD-based mass estimate | 77.38 g | 63.84 g | **17.49% lighter** |
| Maximum von Mises stress | 27.938 MPa | 35.431 MPa | Higher with cutouts |
| Minimum safety factor | 7.409 | 5.842 | **Both pass** (>=2) |
| Maximum total displacement | 0.424 mm | 0.580 mm | **Both pass** (<2 mm) |

**Outcome:** The optimised arm meets all three selected project targets under the simplified static loading assumptions. Its increased stress (26.8%) and deflection (36.8%) quantify the weight–stiffness trade-off.

> **Measurement note:** Stress, safety factor and displacement are the *actual Autodesk Fusion 360 static stress results*, read from the completed simulation screenshots. The masses are earlier STEP-volume calculations using assumed aluminium density of 2.70 g/cm³; they have **not yet been independently confirmed in Fusion 360 Physical Properties**.

## Design and analysis

- Arm geometry: 170 mm nominal mounting-centre spacing, 20 mm beam width, 6 mm thickness, 36 mm diameter motor mounting pad, 35 × 30 mm body mounting pad.
- Lightweight design: three rounded through-slots, approximately 30 × 10 mm each; end mounting pads retained.
- Material in Fusion: **Aluminum 6061 T6 0 Cold Formed**.
- Simulation: **Static Stress** study, fixed constraint on the body-end vertical face, **15 N upwards in global +Z** at the motor pad (14 mm radius limited load target).
- For a fair comparison, the material and the 15 N loading method are the same for both designs.

### Von Mises stress

![Fusion 360 stress comparison](Results/Stress_Comparison.png)

### Total displacement

![Fusion 360 displacement comparison](Results/Displacement_Comparison.png)

## Repository contents

```text
Drone-Arm-Structural-Optimisation/
├── README.md
├── CAD/
│   ├── Baseline_Arm.step
│   └── Optimised_Arm.step
├── Results/
│   ├── CAD_Comparison.png
│   ├── Stress_Comparison.png
│   └── Displacement_Comparison.png
└── Engineering_Report.pdf
```

**Opening CAD in Fusion 360:** Upload the `.step` files through the Fusion Data Panel. To include native Fusion `.f3d` files, open each STEP in Fusion and use **File → Export → Fusion Files (.f3d)**, then add them to `CAD/`. Imported STEP geometry does not recover a parametric feature history. *This ZIP includes STEP solids, not native `.f3d` exports.*

## Limitations and next steps

This is a comparative **static** study, not a flight-certified component assessment. The body connection is simplified as rigidly fixed; no realistic bolted joint, motor torque, vibration, fatigue, lateral load, contact or experimental validation has been assessed. A Fusion-native mesh-refinement check and confirmation of CAD mass properties are useful next steps.

See [Engineering_Report.pdf](Engineering_Report.pdf) for the full three-page project report.
