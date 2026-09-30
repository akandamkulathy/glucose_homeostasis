# EnergyFlow

An interactive model of human energy metabolism and blood-glucose regulation, built as a
replacement for the Just Physiology module in the "Control of Blood Glucose" physiology
laboratory. Open `index.html` in a browser; there is no build step, no dependency and no
server.

Reservoirs hold chemical energy. Arrows are the rates at which energy moves between them.
Students set conditions, run the clock, and read the result.

## Layout and features

- **Layout.** The diagram spans the width of the page with the measurements in a rail beside
  it and the alert strip beneath. Directly under the diagram sit the Controls, with Defaults
  in their header, and the Clock; Food intake, Workload, Run and Advance are all visible with
  the diagram on screens down to 1366 x 768. Below those, on a shared grid, are the control
  log, the recorded graphs, the reservoir contents and the energy ledger.
- **Diagram grammar.** Rounded boxes are stores, heavily dashed boxes are circulating pools,
  square boxes with a solid left edge are rates, and the funnel marks the one node with a
  capacity limit, liver convergence. Its meter shows the gateway load; past 100% the surplus
  leaves as ketone bodies. Systemic convergence is every tissue outside the liver, and ketone
  bodies flow only there, since the liver cannot use them.
- **Measurements** show their normal ranges at every level, and each range bar extends its
  scale, marked with an arrow, when a reading runs past the printed maximum.
- **Orientation** is a single entry rather than something scattered across levels. It offers a
  short tour of the screen and five hands-on tasks, listed in order with the level each
  belongs to. Starting a task switches to that level automatically, so a student at Level 6
  need not know the tasks live at Levels 1 to 3. Completed tasks are marked, the tour's last
  step hands off to the same list, and the whole thing is reachable from Menu at any time.
- **Finishing a module** offers four choices: stay with the subject, start it again, go back
  to whichever list it was opened from, or leave and open the main menu. The module banner
  carries the same route back, so choosing to stay does not strand anyone.

The previous published version is kept as `index.previous.html`.

## Starting

A welcome screen offers a level and two ways in: the guided modules for that level, or the
model with no set task. Both are also reachable directly by URL, which skips the welcome
screen and is useful for linking from a Canvas question.

To publish, enable GitHub Pages on the repository and point it at the branch root.

## Levels and modes

Both are set by URL, so a Canvas question can link straight to the right view.

`index.html?level=3&mode=explore`

**Levels** control what exists in the model. Earlier levels do not hide later elements, they
do not render them, so nothing can be revealed ahead of the question that teaches it.

| Level | Adds | Controls |
|---|---|---|
| 1 · Fuel and demand | glucose pool → liver and systemic convergence → energy use | food intake, workload |
| 2 · The reserves | liver and muscle glycogen, adipose, cell protein, fatty acids | — |
| 3 · The regulators | insulin and glucagon, with regulator badges | beta-cell capacity |
| 4 · Perturbation | — | glucose infusion, insulin sensitivity, GLP-1 agonist, meal pattern |
| 5 · Overflow | ketone bodies (from liver convergence), arterial pH | — |
| 6 · Failure and rescue | insulin ⊣ glucagon | insulin infusion, glucagon receptor blocker |
| Open investigation | everything | + acute illness (stress hormones) |

**Open investigation** sits beside the numbered levels rather than after them. It exposes
every control plus an acute-illness term representing the counter-regulatory response to
infection or injury, which is not part of the laboratory sequence. Every illness term is
exactly neutral at zero, so the taught levels behave identically whether or not it exists.

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

**Control room.** The flow diagram, status alerts, readouts with normal ranges, three live
traces beneath the diagram, and the energy ledger. Arrow thickness scales with the rate of
energy transfer and the dashes travel faster as that rate rises, so an active pathway reads
as motion. Regulator badges brighten and grow as each hormone drives its flow harder; click
a hormone to trace every action it has.

**Graphs.** One expanded plot with the full set beneath it; click any graph to expand it.
Each graph takes its own independent and dependent variable, graphs can be added and removed,
normal ranges are shaded, and the same set appears under the diagram in the control room.
Gridlines fall on round numbers. Data are recorded about every four simulated minutes, so
short events such as the recovery from a glucose load can be read directly rather than
estimated. Moving the pointer across a graph marks the nearest recorded sample and labels it
with its time and value; clicking drops a pin there, so several points can be compared at
once, and clicking a pin again removes it. Pinned coordinates are also listed beneath the
expanded plot. Save a run to leave it on the plot and compare two conditions directly. The
controls and clock move here with you, so you can adjust and re-run without switching tabs.

**Modules.** Twelve guided investigations, one set per level. Opening a module shows its
brief first, as a chart for the patients, and only then loads the model. Each states what is
being investigated and what has to be determined; none says which control to move. Three are
patients presented as a chart, one is a threshold hunt, and the rest are open investigations
whose answers are recorded in the lab assignment rather than in the app.

Challenge and patient modules verify the state of the model, not the procedure used to reach
it, and hold the target for a set number of simulated hours before completing. Completion
raises a dialogue, faded in over about a second, carrying the debrief and a choice of what to
do next, so the result is not something to be discovered by scrolling back up. All eight
investigations and all four verified modules are reachable from the level they belong to, and
the clinical modules are also available under Open investigation. There are no hints; that is
what the teaching assistants are for.

## What the model reproduces

A continuously integrated balance of glucose, liver and muscle glycogen, adipose lipid, cell
protein, and ketone bodies for a 70 kg adult, driven by an insulin/glucagon pair with
physiological response curves. Resting demand is 75 kcal/h.

Every figure below was read back from the engine at the control settings named in the
condition, rather than transcribed from an earlier draft.

| Condition | Result |
|---|---|
| 12 h fast | plasma glucose falls about 20%, 102 → 80 mg/dL |
| 24 h fast | glucose plateaus near 80 mg/dL; liver glycogen effectively empty |
| 5-day starvation | glucose ~75 mg/dL, ketoacids ~18 mg/dL, pH ~7.38 |
| Intense exercise (8× rest), fasted | glucose falls to ~61 as muscle glycogen drains, recovers to ~74 while liver glycogen lasts, then falls again once it is gone; exhaustion at about 19 h |
| Moderate exercise (4× rest), fasted | sustained on gluconeogenesis at ~73 mg/dL; reserves exhausted at day 19 |
| IV glucose tolerance test, 1,000 mg/min for 1 h | peak ~257 mg/dL, below 140 in about 25 min |
| Insulin production set to zero, 36 h | glucose ~450 mg/dL, ketoacids ~74 mg/dL, pH ~7.26 |
| Insulin infusion into that subject | glucose ~94 mg/dL, ketoacids 0, pH 7.40: every variable returns toward normal together |
| Insulin without food | glucose ~48 mg/dL, no ketones, normal pH |
| Glucagon action blocked in ketoacidosis | glucose falls to ~259 but does not normalise; ketones and pH fully correct |
| Insulin sensitivity 25%, eating 2,600 kcal/day | glucose ~140 mg/dL **with** insulin ~46 µU/mL |
| GLP-1 agonist, beta-cell capacity 50% | glucose 114 → 94 mg/dL |
| GLP-1 agonist, healthy fasting subject | no hypoglycaemia; the effect is glucose-dependent |

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
the liver. Exercise ketosis is therefore mild, about 11 mg/dL at an intense workload, rather
than approaching the diabetic range.

A run stops when the subject reaches a state that could not be survived, and says which:
reserves exhausted, profound hypoglycaemia, life-threatening acidosis, extreme
hyperglycaemia, or exhaustion. The last of these is the basis of exercise fatigue: once
muscle glycogen is gone and the blood glucose supplying the working muscle is falling, hard
work cannot continue. A fasted subject at an intense workload reaches that point at about
19 hours, so the model will not let a subject work at 8× resting demand for nine days.

Every combination of the eight controls at their extremes has been swept for physiological
nonsense; all of them either run cleanly or halt with a named reason.

### Structure

Metabolic convergence is split into **liver** and **systemic** at every level, so that
students can see which tissue is processing what. "Systemic" means the rest of the body
outside the liver, and each node says so.

Convergence has a chemical identity, and the node descriptions give it: acetyl-CoA, the
two-carbon unit that carbohydrate, fat and many amino acids are all broken down to before
entering the citric acid cycle. Naming it is what makes the gateway limit legible rather than
arbitrary, and it is also why fatty acids cannot become glucose: there is no route from
acetyl-CoA back to pyruvate. Gluconeogenesis competes for the same intermediates, chiefly
oxaloacetate, which acetyl-CoA needs in order to enter the cycle at all.

Ketone bodies are produced from **liver convergence**, not directly from fatty acids. They
are the overflow when acetyl-CoA arrives faster than the hepatic gateway can pass it, and the
capacity meter on the liver node shows how far past that limit the system is running.

Three design choices carry most of the teaching weight:

- **Muscle glycogen cannot reach the blood.** It flows straight to systemic convergence.
- **Ketones are made in one compartment and spent in another.** Liver convergence → ketone
  bodies → systemic convergence.
- **Ketone clearance saturates.** Past roughly 40 mg/dL, raising production no longer raises
  removal, which is why a modest increase in ketogenesis separates harmless starvation
  ketosis from diabetic ketoacidosis.

The GLP-1 agonist is glucose-dependent in both of its actions: the incretin effect on insulin
secretion only operates above the normal range, and the suppression of glucagon fades out
below it, so counter-regulation is preserved. It therefore corrects hyperglycaemia without
driving a fasting subject low, and does little in a subject with no beta cells at all.

## Working with a session

- **Undo** rolls back the last advance, meal or reset, so a mis-set control does not cost a
  whole protocol.
- **Sessions are saved automatically.** Closing the tab or refreshing offers to restore the
  subject, the graphs and the level from where you left off, rather than starting again.
- **Eat in meals** delivers the same daily energy in three absorption windows instead of
  continuously, which produces the postprandial rise and fall that continuous feeding cannot
  show.
- **Give a meal** delivers a single meal as a discrete bolus, absorbed over a few hours, on
  top of whatever continuous intake is set. Because the liver extracts a large share on first
  pass, a 600 kcal meal raises plasma glucose to about 110 mg/dL in a healthy fasted subject,
  far below the peak the same amount of glucose produces intravenously.
- On a narrow screen the diagram keeps its size and scrolls sideways rather than shrinking to
  the point of illegibility.

## Reduced motion

The app honours the operating system's reduced-motion setting. Beyond the usual CSS
transitions, this also stops the travelling dashes on the arrows and the pulsing of the
hormone badges, both of which are driven from JavaScript and are not covered by a media
query. With motion reduced, arrow thickness alone carries the rate, and the legend says so.
The guided orientation moves between steps without animating.

## Help and record-keeping

Every box in the diagram can be clicked for a short description of what it represents,
including the chemistry behind the convergence nodes for students who want it.

Each control carries a **?** button giving a one-paragraph explanation and a typical value, so
a student confused by one slider does not have to run the whole orientation to find out about
it. Press Escape or click away to dismiss.

**What you have done** logs every action in order, with the simulated time at which it was
taken: food intake changed, advanced 12 h, glucose infusion set to 1,000 mg/min. It reads as
the protocol the student actually ran, which is the quickest way for either of you to see
whether a wrong answer came from wrong reasoning or a wrong procedure.

## Demo links

Any state can be opened directly, which is useful in lecture or from a Canvas question:

`?level=6&scenario=dka&readout=bars&theme=dark`

`scenario` accepts fed, fast, exercise, starve, gtt, t1dm, dka, treat, t2dm. `readout` accepts
numbers or bars. `theme` accepts dark.

## Limits

A teaching model of energy flow, not a clinical tool. Parameters were fitted to reproduce the
behaviours above rather than derived from first principles; it is not HumMod. Individual
pathways are compressed into single arrows, food arrives continuously unless meals are turned
on, and body mass and temperature are fixed. Simulated time is capped at 21 days, with a
warning past 14. Use it for direction, sequence, and magnitude.

## Credits

Developed by **Akhil Kandamkulathy**.

Built with the assistance of Claude, an AI tool developed by Anthropic. The physiological
content, calibration targets, and pedagogical design are the author's own.

© 2026 Akhil Kandamkulathy. Provided for educational use.
