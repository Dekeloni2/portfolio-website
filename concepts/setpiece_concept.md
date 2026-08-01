# Setpiece — Concept Brief

**One-line pitch:** Before every fight you arrange your units on a small grid; adjacency and placement decide an automatic battle. Your skill lives entirely in how well you solved the board before the swords come out.

**Genre:** Puzzle auto-battler · Pixel · **Mobile-first**
**Team:** Solo
**Target market:** Israel — mobile-first by design, not a port. Build for how people actually play here.
**Proves (portfolio goal):** Original mechanic design + market-aware casual design.

### Platform & market notes
- **Mobile is the platform, not a stretch goal.** Design the whole thing for a phone held one-handed: the 3×3 board and every unit must be readable and tappable on a ~6" screen. Prototype on-device early, not on desktop.
- **Localize for Israel from the start.** Plan for Hebrew and right-to-left (RTL) UI — RTL mirrors layout, so bake it into the UI structure now rather than retrofitting. English as the second language.
- **Casual-session shape.** A run should fit a short mobile sitting (a few minutes, one hand). This reinforces the small-board / short-run scope already chosen.

---

## The one mechanic

The pre-fight placement puzzle *is* the game. Everything else — combat, art, meta — exists only to serve it. That is also the scope rule: if a feature doesn't make the placement puzzle better, it's a candidate for the cut list.

Units are **shaped pieces** (polyomino / Tetris-style), and the player **drags, drops, and rotates** them onto a small grid. A piece that would overhang the board edge can't be placed — so *fitting the team onto the board is itself the puzzle*. The roster is larger than the board can hold, so **which units you field, and in what rotation, is the core decision.** Every piece placed on the board can attack; placement and adjacency shape how the fight goes.

Combat is **multi-turn**: solve the board → hit *proceed* → the turn resolves → return to the board and re-arrange survivors → repeat until the fight ends. **Units that die are gone for the rest of the run (permadeath).** So the board *decays* over a fight — as units die it gets easier to pack but weaker to field, creating natural death-spiral tension and comeback moments. Skill lives in how well you solve each successive board, not in reflexes.

## Combat model — DECISION: deterministic (recommended, vetoable)

Combat is **fully deterministic**: the same placement against the same enemy always produces the same result. The tension is "did I solve it correctly?", answered in ~10 seconds of auto-battle.

- *Why deterministic for the MVP:* cleanest read of the mechanic, dramatically less to balance solo, and "100% of the skill is in the solve" is the sharpest possible portfolio story.
- *Probabilistic variant (v2 flavor, not now):* add light RNG so placement stacks the odds across a roguelike run. More replay, but much more tuning burden. Deferred.

## Design pillars

1. **The board is the whole game.** Combat is a readout of a good decision, never a skill test of its own.
2. **Legible over deep.** A small grid and one rule per unit means every choice is understandable at a glance. Depth comes from interactions, not from unit count.
3. **Solve, don't grind.** A run is a sequence of puzzles that escalate; the player gets better at *seeing* solutions, not at farming.

## Core loop (single run)

1. See your roster (bigger than the board) and the enemy.
2. Drag, rotate, and pack unit pieces onto the grid — fit is the puzzle; overhanging pieces are illegal.
3. Hit proceed → the turn resolves → survivors return to the board to re-arrange. Dead units are gone for the run.
4. Repeat until the fight is won (or you're wiped).
5. Win → draft one new unit into your roster; the next fight is harder. ~5 fights = one run.

## MVP scope (ruthlessly small)

- **One board:** 3×3 or 4×4. Small grids force real trade-offs and stay legible.
- **6–8 unit types**, each with exactly one adjacency rule.
- **Deterministic auto-combat**, resolves in ~10s.
- **~5 escalating encounters** as one run, with a one-unit draft between fights.
- **Placeholder pixel art** — readable shapes over polish.

### Explicitly cut for MVP (v2 candidates)
Prestige / meta-progression · story & narrative · large rosters · monetization · multiple board sizes · sound polish. (Touch UX and on-device readability are **not** cut — they're core to a mobile-first build.)

## Starter roster (concrete example — 7 units, one rule each)

- **Vanguard** — front-row body; soaks the first hits. Wants an empty tile behind it to protect.
- **Archer** — deals ranged damage but only if a unit sits directly in front of it (needs a body to hide behind).
- **Healer** — heals every unit orthogonally adjacent to it each round. Rewards clustering.
- **Duelist** — gains bonus damage when it has NO adjacent allies (a lone-wolf that punishes crowding).
- **Bannerman** — buffs all units in its row; useless in a column. Placement axis matters.
- **Trapper** — damages the enemy unit in the opposing column before combat starts; position picks the target.
- **Anchor** — corner-only unit; strong, but eats a constrained tile, forcing the rest of the solve around it.

The fun is the friction between rules — the Healer wants clustering, the Duelist wants isolation, the Vanguard wants space behind it — on a grid too small to satisfy everyone.

## What "done" looks like

A vertical slice: one run of 5 hand-tuned puzzles that a playtester finishes and says "let me try that again, I think I can solve it cleaner." If that sentence happens, the mechanic works and the rest is content.

## Suggested build order

1. Grid + placement UI (drag a unit onto a tile).
2. Deterministic combat resolver (turn order, adjacency rules apply).
3. The 7 units, as data-driven rules (mirror your Brave the Wilderness approach — one flat row per unit so you tune from a table, not code).
4. 5 hand-authored encounters + the draft-between-fights step.
5. Playtest, tune, cut anything that muddies the read.

---

## Sample encounter (worked example)

> ⚠️ Predates the piece-shape model — this example treats units as single cells. Still valid for illustrating the adjacency *rules*, but the real puzzle also layers in polyomino fit + rotation. Redo once piece shapes are defined.

**Grid:** 3×3, front row (row 1) faces the enemy. Coordinates are (row, col), row 1 = front.
**Your hand:** Vanguard, Archer, Healer, Bannerman, Duelist.
**Enemy:** a bruiser front-center that focus-fires your front row, plus a ranged attacker on the enemy back line.

*Rule refinement used here:* Vanguard **shields the ally directly behind it** (cleaner than "wants an empty tile behind"), which is what creates the Archer combo below. Worth adopting.

**Intended optimal solution:**

- **(1,1) Vanguard** — front-left. Tanks the bruiser and shields the ally directly behind it.
- **(2,1) Archer** — directly behind Vanguard: *activated* (a body sits in front) **and** *shielded*. This is your carry.
- **(3,1) Healer** — orthogonally adjacent to the Archer; heals it every round.
- **(2,2) Bannerman** — shares row 2 with the Archer, buffing its damage.
- **(3,3) Duelist** — isolated back corner, no adjacent allies, so its damage bonus is live. Cleans up whatever leaks through.

**Why it's the solve:** four units funnel value into the Archer — the front body activates it, the Vanguard shields it, the Healer sustains it, the Bannerman buffs it — turning one ranged unit into an unkillable damage engine. Meanwhile the Duelist is deliberately exiled to a corner, because clustering it (the instinct the Healer and Bannerman push you toward) would cancel its bonus. That tug-of-war — cluster for support vs. isolate the lone wolf — on a grid too small to do both is the puzzle.

---

*Concept v1 — deterministic MVP. Open decision flagged above if you'd rather go probabilistic.*
