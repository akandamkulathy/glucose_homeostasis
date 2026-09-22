# EnergyFlow

Interactive model of energy flow and blood-glucose regulation for the physiology laboratory
"Control of Blood Glucose". Open `index.html` in a browser; no installation is needed.

## Current layout and features

- **Layout.** The diagram spans the width of the page with the measurements in a rail beside
  it and the alert strip beneath. Directly under the diagram sit the Controls, with Defaults in
  their header, and the Clock; Food intake, Workload, Run and Advance are all visible with the
  diagram on screens down to 1366 x 768. Below those, on a shared grid, are the control log,
  the recorded graphs, the reservoir contents and the energy ledger.
- **Diagram grammar.** Rounded boxes are stores, heavily dashed boxes are circulating pools,
  square boxes with a solid left edge are rates, and the funnel marks the one node with a
  capacity limit, liver convergence. Its meter shows the gateway load; past 100% the surplus
  leaves as ketone bodies. Systemic convergence is every tissue outside the liver, and ketone
  bodies flow only there, since the liver cannot use them.
- **Measurements** show their normal ranges at every level, and each range bar extends its
  scale, marked with an arrow, when a reading runs past the printed maximum.

**Orientation** is a single entry rather than something scattered across levels. It offers a
one-minute tour of the screen and four short hands-on tasks, listed in order with the level
each belongs to. Starting a task switches to that level automatically, so a student at
Level 6 need not know the tasks live at Levels 1 to 3. Completed tasks are marked. The tour's
last step hands off to the same list, and the whole thing is reachable from Menu at any time.

Finishing a module offers four choices: stay with the subject, start it again, go back to
whichever list it was opened from, or leave and open the main menu. The module banner carries
the same route back, so choosing to stay does not strand anyone.

The previous published version is kept as `index.previous.html`.


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
| 4 · Perturbation | — | glucose infusion, insulin sensitivity, GLP-1 agonist, meal pattern |
| 5 · Overflow | ketone bodies (from liver convergence), arterial pH | — |
| 6 · Failure and rescue | insulin ⊣ glucagon | insulin infusion, glucagon receptor blocker |
| Open investigation | everything | + acute illness (stress hormones) |

**Open investigation** sits beside the numbered levels rather than after them. It exposes every
control plus an acute-illness term representing the counter-regulatory response to infection
or injury, which is not part of the laboratory sequence. Every illness term is exactly neutral
at zero, so the taught levels behave identically whether or not it exists.

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
| 6 | An investigational drug | investigate |

## The three views

**Control room** — the flow diagram, status alerts, readouts with normal ranges, three live
traces beneath the diagram, and the energy ledger. Arrow thickness scales with the rate of
energy transfer and the dashes travel faster as that rate rises, so an active pathway reads
as motion. Regulator badges brighten and grow as each hormone drives its flow harder; click
a hormone to trace every action it has.

**Graphs** — one expanded plot with the full set beneath it; click any graph to expand it.
Gridlines fall on round numbers, and moving the pointer across the expanded plot marks the
nearest recorded sample and reports its time and value. Data are recorded about every four
simulated minutes, so short events such as the recovery from a glucose load can be read
directly rather than estimated.
Each graph takes its own independent and dependent variable, graphs can be added and removed,
and the same set appears under the diagram in the control room. Normal ranges are shaded.
Hovering any graph places a marker on the nearest recorded sample and labels it with its
coordinates. Clicking drops a pin there, so several points can be compared at once; clicking
a pin again removes it, and the pinned coordinates are also listed beneath the expanded plot. Save a run to leave it on the plot and compare two conditions directly. The controls and clock
move here with you, so you can adjust and re-run without switching tabs.

**Modules** — twelve guided investigations, one set per level. Opening a module shows its
brief first — for patients, as a chart — and only then loads the model. Each states what is being
investigated and what has to be determined; none says which control to move. Three are
patients presented as a chart, one is a threshold hunt, and the rest are open investigations
whose answers are recorded in the lab assignment rather than in the app.

Challenge and patient modules verify the state of the model, not the procedure used to reach
it, and hold the target for a set number of simulated hours before completing. Completion
raises a dialogue — faded in over about a second — carrying the debrief and a choice of what
to do next, so the result is not something to be discovered by scrolling back up. All eight
investigations and all four verified modules are reachable from the level they belong to, and
the clinical modules are also available under Open investigation. There are no hints — that is what the teaching assistants are
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
| Fasted intense exercise | glucose falls to ~62 as muscle glycogen drains, recovers to ~74 while liver glycogen lasts, then falls again once it is gone; exhaustion at about 19 h |
| Fasted moderate exercise | sustained on gluconeogenesis at ~74 mg/dL; reserves exhausted at about day 19 |
| IV glucose tolerance test | peak ~245 mg/dL, below 140 in about 25 min |
| Insulin production set to zero, 36 h | glucose ~455 mg/dL, ketoacids ~74 mg/dL, pH ~7.26 |
| Insulin infusion | every variable returns toward normal together |
| Insulin without food | glucose ~44 mg/dL, no ketones, normal pH |
| Glucagon action blocked in ketoacidosis | glucose falls to ~267 but does not normalise; ketones and pH fully correct |
| Insulin sensitivity 25%, eating | glucose ~149 mg/dL **with** insulin ~53 µU/mL |
| GLP-1 agonist, reduced beta-cell capacity | glucose 135 → 101 mg/dL |
| GLP-1 agonist, healthy fasting subject | no hypoglycaemia — the effect is glucose-dependent |

### Energy conservation

Total energy expenditure is a constraint, not a label. At every step the model computes what
the body is spending and draws exactly that much from the reserves: glucose first, then
muscle glycogen, then fat, and finally body protein once fat can no longer cover the
shortfall. Glucose taken up beyond what is being spent is stored rather than oxidised, and
fatty acids mobilised beyond what is needed are re-esterified.

Obligate glucose uptake by brain and red cells uses saturable kinetics with a low Michaelis
constant, so it stays nearly flat until glucose falls well below normal. This matters: it is
why the brain cannot throttle its demand to match a failing supply, and it is what stops the
glucose pool from silently settling wherever production happens to leave it.

During exercise, working muscle consumes fatty acids directly, so proportionally less reaches
the liver. Exercise ketosis is therefore mild (about 11 mg/dL) rather than approaching the
diabetic range.

A run stops when the subject reaches a state that could not be survived, and says which:
reserves exhausted, profound hypoglycaemia, life-threatening acidosis, extreme
hyperglycaemia, or exhaustion. The last of these is the basis of exercise fatigue: once
muscle glycogen is gone and the blood glucose supplying the working muscle is falling, hard
work cannot continue. A fasted subject at an intense workload reaches that point at about
19 hours — the model will not let a subject work at 8× resting demand for nine days.

Every combination of the eight controls at their extremes has been swept for physiological
nonsense; all of them either run cleanly or halt with a named reason.

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

The GLP-1 agonist is glucose-dependent in both of its actions: the incretin effect on insulin
secretion only operates above the normal range, and the suppression of glucagon fades out
below it, so counter-regulation is preserved. It therefore corrects hyperglycaemia (132 to
101 mg/dL in a subject with reduced beta-cell capacity) without driving a fasting subject low,
and does little in a subject with no beta cells at all.

## Credits

Developed by **Akhil Kandamkulathy**.

Built with the assistance of Claude, an AI tool developed by Anthropic. The physiological
content, calibration targets, and pedagogical design are the author's own.

© 2026 Akhil Kandamkulathy. Provided for educational use.

## Working practices

- **Undo** steps back to before the last advance, so a mis-set control does not cost a whole protocol.
- **Sessions are saved automatically.** Reopening the model offers to restore the subject, the graphs, and the level from where you left off.
- **Hovering the expanded graph** reports the exact time and value beneath the pointer, snapped to the nearest recorded sample.
- **Eat in meals** delivers the same daily energy in three absorption windows instead of continuously, which produces the postprandial rise and fall that continuous feeding cannot show.
- On a narrow screen the diagram scrolls sideways at full size rather than shrinking to illegibility.

## Reduced motion

The app honours the operating system's reduced-motion setting. Beyond the usual CSS
transitions, this also stops the travelling dashes on the arrows and the pulsing of the
hormone badges, both of which are driven from JavaScript and are not covered by a media
query. With motion reduced, arrow thickness alone carries the rate, and the legend says so.
The guided orientation moves between steps without animating.

## Help and record-keeping

Every box in the diagram can be clicked for a short description of what it represents.

Each control carries a **?** button giving a one-paragraph explanation and a typical value, so
a student confused by one slider does not have to run the whole orientation to find out about
it. Press Escape or click away to dismiss.

**What you have done** logs every action in order, with the simulated time at which it was
taken — food intake changed, advanced 12 h, glucose infusion set to 1,000 mg/min. It reads as
the protocol the student actually ran, which is the quickest way for either of you to see
whether a wrong answer came from wrong reasoning or a wrong procedure.

## Demo links

Any state can be opened directly, which is useful in lecture or from a Canvas question:

`?level=6&scenario=dka&readout=bars&theme=dark`

`scenario` accepts fed, fast, exercise, starve, gtt, t1dm, dka, treat, t2dm. `readout` accepts
numbers or bars. `theme` accepts dark.

## Working with a session

A run can be undone step by step: **Undo** rolls back the last advance, meal, or reset. The
session is saved automatically, so closing the tab or refreshing offers to resume where you
left off rather than starting again.

**Give a meal** delivers a single meal as a discrete bolus, absorbed over a few hours, on top
of whatever continuous intake is set. Because the liver extracts a large share on first pass,
a 600 kcal meal raises plasma glucose to about 110 mg/dL in a healthy fasted subject — far
below the peak the same amount of glucose produces intravenously.

On a narrow screen the diagram keeps its size and scrolls sideways rather than shrinking to
the point of illegibility.

## Limits

A teaching model of energy flow, not a clinical tool. Parameters were fitted to reproduce
the behaviours above rather than derived from first principles; it is not HumMod. Individual
pathways are compressed into single arrows, food arrives continuously rather than as meals,
and body mass and temperature are fixed. Simulated time is capped at 21 days, with a warning
past 14. Use it for direction, sequence, and magnitude.
