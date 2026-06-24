# Hex Card Game — Concept Note

A singleplayer/coop hex exploration game where each hexagon is an area to discover, and combat is resolved through a card/deck-building battle system.

## Origin
Hexbound picks up the original hex exploration concept from the early Trials of the Dungeon prototype. That game eventually shipped as a tile-based cooperative board game (physical product) — the hex concept was shelved when it pivoted. Hexbound is that shelved concept, rebuilt as a video game.

## Keywords
- **Dormant** — a hexagon placed on the map but not yet active. Has no effect until a player steps on it or a card activates it.
- **Rotation** — a full cycle where all players have taken at least 1 action.
- **Activate** — to trigger a hexagon's effect, either by stepping on it or via a card.

## Two-Layer Structure

**Exploration Layer** — Players build and traverse the hex map themselves. Hexagons are earned (e.g. as combat rewards) and placed by the player — the map is player-authored, not procedurally generated. Players place and activate hexagons to build the dungeon, find the Key Hexagon, and escape.

**Battle Layer** — Landing on a battle hexagon triggers a card duel against an AI enemy. Your deck determines how you fight.

## Core Loop
- Start classless — the early game acts as a natural tutorial
- Gain a class mid-run by landing on class-specific hexagons (forge = Blacksmith, alchemy lab = Chemist, etc.)
- Class defines your playstyle across both exploration and combat

## Three-Layer Deck Building
1. **Starting class deck** — small and weak, but defines your identity. Wizard starts with potions, Executioner with heavy hits, Blacksmith with armor cards.
2. **Exploration builds it** — Solo/Team cards collected from hexagons are added to your deck. How you explore shapes how you fight. The map IS your deck builder.
3. **Shop hexagons refine it** — spend gold to upgrade cards, remove weak ones, or buy class-specific cards.

No two runs feel the same: starting deck differs by class, mid-run deck differs by exploration path, late-run deck differs by what you could afford.

## Hexagon Types
- **Solo Hexagon** — affects only the activating player
- **Team Hexagon** — affects all players
- **Trap Hexagon** — card can be held and played on any turn (great for ambushes)
- **Battle Hexagon** — triggers card combat against an AI enemy
- **Shop Hexagon** — buy/upgrade cards and equipment; owned by the Merchant if one is playing
- **Teleportation Hexagon** — 2 exist per map; stepping on one teleports you to the other
- **Key Hexagon** — the win objective; find it, then reach the dungeon exit

## Classes (art already exists)

### Original Classes
- **Blacksmith** — equip 2 armor pieces at once; starts with armor-heavy deck (defense economy)
- **Bard** — skip a battle hexagon once per 2 rotations (mobility/avoidance)
- **Baker** — obtain 1 random food item per battle hexagon (sustain economy)
- **Chemist** — obtain 1 potion per team card completed (combo economy)
- **Trickster** — once per rotation, copy a teammate's class skill (mirror/adaptive; powerful in coop)

### New Classes
- **Wizard** — potions drank during a battle hexagon grant +1 damage modifier for that battle; potion timing becomes a skill expression
- **Executioner** — starts with an additional D20 usable in battle (dice mechanic within card combat); limited to 3 battle hexagons — high risk, high reward glass cannon
- **Merchant** — the idle class. Your shop hexagon restocks automatically as the dungeon is explored; each new hexagon revealed adds 1 item to your shop pool. Generate +1 gold per rotation passively. Weak combat stats (low attack, defense, speed) but the richest player by endgame. In coop, serves as the team's economy engine — hangs back, accumulates gold, and makes everyone else stronger.

## Coop Design Notes
- Singleplayer or 2-player coop against AI enemies (no PvP)
- In coop, one player can spec into battle cards while the other focuses on exploration cards
- Merchant creates natural role dependency — weak alone, invaluable to the team
- Trickster borrowing a coop partner's class skill creates emergent combos

## Win Condition
Find the Key Hexagon, then reach the dungeon exit. All players must survive to win in coop.

## AI Design Notes
- Each class has its own AI "personality" mirroring its passive
- Trickster AI is the most complex — must evaluate all teammates' class skills in real time to decide which to copy
- Executioner AI has a risk timer (limited to 3 battles)

## Comparable Games
Slay the Spire meets Catan

## Status
Early concept — not yet in active development
