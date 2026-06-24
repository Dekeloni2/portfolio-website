# Devlog #1 — Where Did This Game Come From?

Before this was a video game, it was a board game.

A while back I was prototyping something called **Trials of the Dungeon** — a 4-player hex exploration game where you and a teammate work together to find a key and escape a dungeon before the other team does. You'd place hexagon tiles to build the map as you went, flip them to reveal traps or rewards, and when two players met on the same tile, they'd roll dice to fight.

It never got made. But I kept the assets — character art for five classes, a hex map mockup, card designs, even a rules document. It just sat there.

Recently I started thinking about what it would take to actually build it, and somewhere in that process the question shifted from *"how do I build this board game?"* to *"what would make this genuinely interesting as a video game?"*

The answer that kept coming back: **not the dice.**

Dice combat was always the weakest part of the design. Roll, compare, subtract HP. It works for a board game where you want something fast and physical, but in a video game it's just a random number generator with extra steps. There's no skill, no decision-making, nothing that makes the classes feel different in a fight.

So I replaced it with a card/deck-building battle system. Now when you step on a battle hexagon, you fight an AI enemy using a deck of cards you've been building throughout the run. That one change made everything else click.

---

## What the game actually is

It's a singleplayer (or 2-player coop) hex exploration game with two layers:

**Exploration** — You're navigating a procedurally generated hex map, placing dormant tiles, triggering events, finding the Key Hexagon, and trying to reach the exit. Different hexagon types do different things: some affect only you, some affect the whole team, some are traps you can hold and spring on enemies later.

**Combat** — When you hit a battle hexagon, you drop into a card duel against an AI enemy. The deck you bring into that fight is one you've been building the whole run.

The deck building itself has three sources: you start with a small class-specific deck, you add cards by exploring hexagons, and you upgrade at shop hexagons. So the map you explore literally shapes how you fight. Two players with the same class can end up with completely different decks depending on where they went.

---

## The classes

One thing I didn't change from the original prototype is the class roster. The art already existed, and more importantly, the classes are interesting — not because they're powerful, but because they're all *non-combat specialists*.

A Blacksmith. A Bard. A Baker. A Chemist. A Trickster. A Wizard. An Executioner. A Merchant.

None of these are warriors. That's the point. Each one brings a different kind of economy to the game — sustain, defense, utility, gold — and the card battle system is where those economies pay off.

The one I redesigned most heavily is the **Merchant**. In the original board game, the Merchant owned the shop hexagon — when another player landed on it, they'd buy from you. I wanted to keep that ownership feeling in the video game, but make it more dynamic.

The new version: the Merchant's shop hexagon restocks automatically as the dungeon is explored. Every new hexagon revealed adds potential items to the shop pool. The Merchant generates gold passively each rotation. They're weak at everything else — low attack, low defense, low speed — but by the end of the run they're the richest player on the map with the best-stocked shop in the dungeon.

In coop, this creates a natural role split. One player pushes the map and fights. The Merchant hangs back, accumulates gold, and makes sure the team can afford upgrades when it counts.

---

## What's next

Right now this is still a concept. I haven't written a line of code or opened Unity. What I have is a clear enough design that I know what the first prototype needs to test:

- Does the hex map feel interesting to explore before combat is even involved?
- Does the card battle system hold up in isolation?
- Do the two layers actually feed each other, or do they feel disconnected?

Those are the questions the first playable needs to answer. When I have something running, that'll be Devlog #2.

---

*This is part of an ongoing development diary for an untitled hex card game. I'm documenting the process from concept to (hopefully) finished game as part of my portfolio.*
