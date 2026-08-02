# Fuel & Reserve

An interactive companion for the **Regulation of Blood Glucose** laboratory.

Students adjust food intake, workload, and insulin production, then watch chemical
energy move between reservoirs in real time. Reservoirs hold energy; arrows are rates.

## Why this exists

The laboratory simulation reports concentrations. This tool reports **flows** — where
each kilocalorie reaching a cell is coming from at any moment, and what is refilling
the blood glucose pool. That reframing is the point: it makes the substrate hierarchy,
the 24-hour hand-off from glycogen to gluconeogenesis, and the ketone overflow visible
as movement rather than as a list of facts.

## Running it

Open `index.html` in any modern browser. No build step, no dependencies, no server.
Everything is in the single file. To publish, enable GitHub Pages on the repository
and point it at the branch root.

## The three views

**Control room** — the reservoir diagram, live readouts, and the energy ledger.
Six preset conditions set up fed baseline, fasting, intense exercise, day 3 of
starvation, untreated type 1 diabetes, and insulin treatment.

**Experiment recorder** — time-series traces of glucose, hormones, ketones, pH,
glycogen, adipose, protein, and hepatic glucose output. Students can run a condition
and read the curves the way they would read simulation output.

**Teaching studio** — short written explanations tied to specific laboratory questions.

## What the model does

A continuously integrated balance of glucose, liver and muscle glycogen, adipose lipid,
body protein, and ketone bodies for a 70 kg adult at rest, driven by an insulin/glucagon
pair with physiological response curves.

Behaviours it reproduces:

| Condition | Result |
|---|---|
| 12 h fast | plasma glucose falls ~20% |
| 24 h fast | glucose plateaus; liver glycogen effectively empty |
| 72 h – 21 d starvation | glucose stable ~74 mg/dL, ketones ~23 mg/dL, pH ~7.37 |
| Intense exercise | muscle glycogen collapses, liver reserve preserved |
| No insulin, 36 h | glucose ~406 mg/dL, ketones ~136 mg/dL, pH ~7.12 |
| Insulin given | all variables return toward normal together |

Two design choices carry most of the teaching weight:

- **Muscle glycogen cannot reach the blood.** It flows straight to metabolic
  convergence, never back to the glucose pool.
- **Ketone clearance saturates.** Past roughly 40 mg/dL, raising production no longer
  raises removal. This is why a modest increase in ketogenesis separates harmless
  starvation ketosis from diabetic ketoacidosis.

## Limits

A teaching model of energy flow, not a clinical tool. Individual pathways are compressed
into single arrows, food arrives continuously rather than as meals, and body temperature
and mass are fixed. Use it for direction, sequence, and magnitude.
