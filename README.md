# Fuel &amp; Reserve

An interactive simulation of human energy metabolism, built as a candidate replacement for
the Just Physiology module in the Regulation of Blood Glucose laboratory.

Reservoirs hold chemical energy. Arrows are the rates at which energy moves between them.
Students set conditions, run the clock, and read the result.

## Starting

A welcome screen offers a level and two ways in: the guided modules for that level, or the
model with no set task. Both are also reachable directly by URL, which skips the welcome
screen — useful for linking from a Canvas question.

## Running it

Open `index.html`. No build step, no dependencies, no server. To publish, enable GitHub
Pages on the repository and point it at the branch root.

## Levels and modes

Both are set by URL, so a Canvas question can link straight to the right view.

`index.html?level=3&mode=explore`

**Levels** control what exists in the model — earlier levels do not hide later elements,
they do not render them, so nothing can be revealed ahead of the question that teaches it.

| Level | Adds | Controls |
|---|---|---|
| 1 · Fuel and demand | glucose pool → liver and systemic convergence → energy use | food intake, workload |
| 2 · The reserves | liver and muscle glycogen, adipose, cell protein, fatty acids | — |
| 3 · The regulators | insulin and glucagon, with regulator badges | beta-cell capacity |
| 4 · Perturbation | — | glucose infusion, GLP-1 agonist |
| 5 · Overflow | ketone bodies (from liver convergence), arterial pH | — |
| 6 · Failure and rescue | insulin ⊣ glucagon | insulin infusion, glucagon receptor blocker |

**Modes** control how much the student can do.

| Mode | Shows |
|---|---|
| `view` | Diagram and readouts only. A live reference figure for a pre-lab question. |
| `demo` | Adds the clock. Watch a preset condition unfold. |
| `explore` | Full controls, graphs, and patient cases. Default. |

## Modules

| Level | Module | Kind |
|---|---|---|
| 1 | The size of the pool | investigate |
| 2 | Twenty-four hours without food | investigate |
| 2 | Working muscle | investigate |
| 3 | The hormone response | investigate |
| 3 | What glucagon reaches | investigate |
| 4 | Glucose tolerance | investigate |
| 4 | Removing insulin | investigate |
| 4 | Finding the threshold | challenge |
| 5 | Five days without food | challenge |
| 6 | Patient A · 19 years | patient |
| 6 | Patient B · 20 years | patient |
| 6 | Unrestricted model | investigate |
| 6 | An investigational drug | investigate |

## The three views

**Control room** — the flow diagram, status alerts, readouts with normal ranges, three live
traces beneath the diagram, and the energy ledger. Arrow thickness scales with the rate of
energy transfer and the dashes travel faster as that rate rises, so an active pathway reads
as motion. Regulator badges brighten and grow as each hormone drives its flow harder; click
a hormone to trace every action it has.

**Graphs** — one expanded plot with the full set beneath it; click any graph to expand it.
Each graph takes its own independent and dependent variable, graphs can be added and removed,
and the same set appears under the diagram in the control room. Normal ranges are shaded.
Save a run to leave it on the plot and compare two conditions directly. The controls and clock
move here with you, so you can adjust and re-run without switching tabs.

**Modules** — thirteen guided investigations, one set per level. Opening a module shows its
brief first — for patients, as a chart — and only then loads the model. Each states what is being
investigated and what has to be determined; none says which control to move. Three are
patients presented as a chart, one is a threshold hunt, and the rest are open investigations
whose answers are recorded in the lab assignment rather than in the app.

Challenge and patient modules verify the state of the model, not the procedure used to reach
it, and hold the target for a set number of simulated hours before completing. A debrief
unlocks only on completion. There are no hints — that is what the teaching assistants are
for.

## What the model reproduces

A continuously integrated balance of glucose, liver and muscle glycogen, adipose lipid, cell
protein, and ketone bodies for a 70 kg adult, driven by an insulin/glucagon pair with
physiological response curves.

| Condition | Result |
|---|---|
| 12 h fast | plasma glucose falls about 20% |
| 24 h fast | glucose plateaus; liver glycogen effectively empty |
| 5-day starvation | glucose ~76 mg/dL, ketoacids ~15 mg/dL, pH ~7.38 |
| Intense exercise | muscle glycogen collapses, liver reserve preserved |
| IV glucose tolerance test | peak ~253 mg/dL, below 140 within 30 min |
| Insulin production set to zero, 36 h | glucose ~455 mg/dL, ketoacids ~74 mg/dL, pH ~7.26 |
| Insulin infusion | every variable returns toward normal together |
| Insulin without food | glucose ~44 mg/dL, no ketones, normal pH |
| Glucagon action blocked in ketoacidosis | glucose falls to ~267 but does not normalise; ketones and pH fully correct |
| GLP-1 agonist, reduced beta-cell capacity | glucose 135 → 101 mg/dL |
| GLP-1 agonist, healthy fasting subject | no hypoglycaemia — the effect is glucose-dependent |

### Structure

Metabolic convergence is split into **liver** and **systemic** at every level, so that
students can see which tissue is processing what. "Systemic" means the rest of the body
outside the liver, and each node says so.

Ketone bodies are produced from **liver convergence**, not directly from fatty acids — they
are the overflow when fatty acid energy arrives faster than the hepatic gateway can pass it.
The capacity meter on the liver node shows how far past that limit the system is running.

Three design choices carry most of the teaching weight:

- **Muscle glycogen cannot reach the blood.** It flows straight to systemic convergence.
- **Ketones are made in one compartment and spent in another.** Liver convergence → ketone bodies → systemic convergence.
- **Ketone clearance saturates.** Past roughly 40 mg/dL, raising production no longer raises
  removal — which is why a modest increase in ketogenesis separates harmless starvation
  ketosis from diabetic ketoacidosis.

The GLP-1 agonist is modelled as glucose-dependent, so it corrects hyperglycaemia without
driving a healthy subject low, and does little in a subject with no beta cells.

## Limits

A teaching model of energy flow, not a clinical tool. Parameters were fitted to reproduce
the behaviours above rather than derived from first principles; it is not HumMod. Individual
pathways are compressed into single arrows, food arrives continuously rather than as meals,
and body mass and temperature are fixed. Simulated time is capped at 21 days, with a warning
past 14. Use it for direction, sequence, and magnitude.
