---
mode: 'agent'
tools: ['githubRepo', 'codebase', 'websearch', 'editFiles', 'search']
description: 'Generate a Warhammer 40,000 Crusade Mission (Ashes of Solcaris)'
---

# Prompt: Generate a Warhammer 40,000 Crusade Mission (Ashes of Solcaris)

## Task
You will generate a complete, ready-to-play Warhammer 40,000 10th Edition Crusade mission for 4 players as a single Markdown file. Produce only the mission file content. Stay strictly on task: a clear, polished mission that looks and reads like an official publication without copying proprietary text.

- Campaign: Ashes of Solcaris (Forge-world setting on Solcaris Prime)
- Ruleset: Pariah Nexus (Blackstone, Null-zone themes)
- Edition: 10th
- Players: Exactly 4
- Output path convention: `./missions/{mission-slug}/mission.md` (you only output the file contents; the path is for context)

## Guardrails
- Do not copy or paraphrase any specific Games Workshop mission text. Write original content that fits the tone and structure.
- Don’t include book-only rules or points. Refer to core concepts (objectives, actions, scoring) at a high level with your own wording.
- Keep all mechanics self-contained in the mission (no external references required to play, beyond the core rules).
- Assume standard 60"x44" battlefield unless otherwise specified; provide scaling for other sizes.

## Inputs (fill these via reasonable assumptions if not provided)
- Mission title and evocative subtitle
- Mission theme hook (e.g., Blackstone surge, ash storm, vault breach)
- Recommended battle size (Incursion/Strike Force) and points per player
- Battlefield size and terrain tags (Industrial, Ruins, Ash Waste)
- Deployment layout for 4 players (zones A–D)
- Number and placement of Objective Markers (e.g., 6 total)
- Primary scoring method and cap per battle round and/or endgame
- 3–5 bespoke Secondary Objectives (or pick-2-of-4)
- Mission Rules (Pariah Nexus-flavored: Null-zone, Blackstone flux, Ash storms, Salvage, Actions)
- Actions any unit can perform (name, when, restrictions, success effect)
- Crusade rewards and risks (XP, Requisition suggestions, Relics/Artifacts hooks, Battle Scars triggers)
- Setup steps checklist and tie-breakers

## Output format
Produce a single Markdown document with this structure, including the YAML front matter and all headings. Make it concise, unambiguous, and table-ready.

```markdown
---
id: <mission-slug-kebab-case>
title: <Mission Title>
subtitle: <Evocative Subtitle>
edition: "10th"
ruleset: "Pariah Nexus"
playerCount: 4
battleSize: <Incursion | Strike Force>
recommendedPointsPerPlayer: <e.g., 1000 | 1500>
battlefieldSize: <e.g., 60x44>
setting: "Solcaris Prime"
tags: [Crusade, 4-Player, Pariah-Nexus, Solcaris]
# Optional switches to flavor the rules
options:
	blackstoneFlux: true
	nullZoneEffects: true
	ashStorms: true
	salvageArcheotech: true
---

# <Mission Title>

> <Short punchy 1–2 sentence intro tying the situation to Solcaris Prime and the Blackstone vault.>

## Mission Briefing
A clear, original 3–6 sentence narrative that sets stakes and the immediate tactical situation for four forces converging.

## The Battlefield
- Size: <60"x44" by default> (include scaling for 44"x30" if helpful)
- Terrain: <keywords such as Industrial, Ruins, Mechanicus, Ash>
- Objective Markers: <count and physical placement guidance>

### Map & Deployment (4 Players)
Provide an ASCII diagram that shows deployment zones A, B, C, D and objective markers 1–6. Use table-like layout with compass directions. Include horizontal and vertical distances where useful.

```
	N
W +------------------------------+ E
	|         O1        O2         |
	|   A    -----DZ A-----    B   |
	|         O3        O4         |
	|   C    -----DZ C-----    D   |
	|         O5        O6         |
S +------------------------------+ N
```

- Deployment: Each player picks/assigns a unique zone (A–D). Roll-off for order; ties re-roll.
- First Battle Round: <who has first turn selection rules for 4 players>
- Reserves/Deep Strike: <any special allowances or bans>

## Primary Mission: <Name>
State clearly how VP are scored, and when (end of each player turn, battle round, or endgame). Include a per-round cap if relevant and a total victory target.

- Example skeleton:
	- Hold 1 / Hold 2 / Hold More (or a 4-player variant)
	- Control Key Site(s): O2 and O5 are worth additional VP
	- Endgame Bonus: Control the Vault Core (center) for bonus VP

## Secondary Objectives (Choose 2)
Provide 4–5 bespoke secondaries with short, precise scoring clauses. Keep to simple trigger checks to avoid ambiguity.

1. <Secondary Name> — <scoring condition>
2. <Secondary Name> — <scoring condition>
3. <Secondary Name> — <scoring condition>
4. <Secondary Name> — <scoring condition>
5. <Optional Fifth> — <scoring condition>

## Mission Rules
List original, punchy rules that fit Pariah Nexus and Solcaris. Keep them self-contained and balanced. Examples:

- Blackstone Flux: <a per-round aura or random pulse that alters actions/psychic/null effects>
- Null-Zone Pockets: <zones that limit abilities, invulnerables, or stratagems>
- Ash Storms: <line-of-sight/weather rule with simple timing>
- Salvage Archeotech (Action): <unit action details and rewards>
- Vault Feedback: <risk element causing mortal wounds or movement penalties>

## options
Lists the optional flavour rules enabled for this mission. Any, all or none of the extra rules can be included. For a list of the optional flavour rules see [flavour-rules.md](../../rules/flavour-rules.md). Do not include the optional rules text here, just the names of the rules that are included in this mission, if any.

### Actions
Define any special mission actions any unit can perform. For each action provide:
- Name (Action)
- When (your Movement phase, end of phase, etc.)
- Who (unit type restrictions, not Battle-shocked, etc.)
- Time (how many models/turns needed)
- Success (exact effect or VP)

## Agendas (Crusade)
Offer 3–4 agendas appropriate to this mission and setting for Crusade progress. Each should provide clear XP triggers and an evocative name.

- <Agenda Name> — <how units earn XP>
- <Agenda Name> — <how units earn XP>
- <Agenda Name> — <how units earn XP>

## Rewards & Risks (Crusade)
- Mission Bonus: <1–2 thematic boon options for the victor>
- Requisition Hooks: <suggested RQ the victor or all players might take next>
- Archeotech Cache: <optional Relic/upgrade unlock with rarity gate>
- Battle Scars: <clear trigger for a scar check or risk after specific events>

## Setup Steps (Checklist)
1. Agree battle size, points per player, and battlefield size.
2. Place terrain matching Industrial/Ash Wastes with at least 2 LOS blockers.
3. Place objective markers as shown on the map.
4. Determine attacker/defender or seating order for zones A–D.
5. Declare Reserves and reveal any pre-game abilities.
6. Deploy in order; then begin the first battle round.

## Battle Length & Victory
- Battle Length: <fixed 5 rounds or variable; specify>
- Victory: Highest total VP; ties break by <priority: Primary VP > Secondaries > Destroyed Points > roll-off>.
- Sportsmanship/Time: <reminder to keep pace and call last round>

## Designer Notes (Optional)
Concise intent and suggested variations (e.g., fewer objectives, asymmetric scoring, escalation variant for 6 players).
```

## Style and tone
- Crisp, unambiguous rules text. Avoid fluff bloat in rules sections.
- Narrative flavor at the top; mechanics below should be bullet-led and concise.
- Match the structure and clarity of official publications without copying phrases.

## Validation before returning
Run a quick self-check and silently fix before outputting:
- [ ] All required sections present and filled
- [ ] 4-player deployment and scoring are clear
- [ ] Primary/secondary scoring adds up sensibly and is conflict-free
- [ ] Actions include timing, restrictions, and outcomes
- [ ] Crusade rewards/risks are present and non-exploitable
- [ ] No copyrighted text copied; all wording is original
- [ ] Output is a single, complete Markdown document ready for `./missions/{mission-slug}/mission.md`