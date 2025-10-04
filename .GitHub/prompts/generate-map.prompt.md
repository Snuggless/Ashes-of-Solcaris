---
mode: 'agent'
tools: ['githubRepo', 'codebase', 'websearch', 'editFiles', 'search']
description: 'Generate an alternative 4-player map for a Warhammer 40,000 10th Edition mission'
---

Purpose
- Generate an alternative 4-player map for a Warhammer 40,000 10th Edition mission.
- Works for: (a) missions created by the create-mission prompt, or (b) existing missions from the Pariah Nexus book.
- Always output a Markdown map file saved to /maps as {mission-name}.{YYYY-MM-DD}.md.

Strict output focus
- Only produce the requested map content in Markdown. Do NOT include meta commentary, filler text, or restate these instructions.
- If the mission is from Pariah Nexus, include only the necessary adapted rules for 4 players. Do not reproduce copyrighted text verbatim from the book; summarize changes and list only what’s needed to play.

Inputs you will receive
- source: "create-mission" | "pariah-nexus"
- mission_name: string (required)
- mission_summary: short text (optional; for flavor only, keep it brief)
- battlefield_size: string (optional; default 60"x44" if not provided)
- objective_count: integer (optional; if not provided, pick a sensible count for the mission type and ensure symmetry)
- constraints: array of short rules (optional; e.g., "no objectives within 6\" of a battlefield edge")
- special_rules_from_source: array (optional; only if relevant to adapt; keep paraphrased, minimal)
- date: string in YYYY-MM-DD (required for filename)
- variant: "FFA" | "2v2" (optional; default FFA if not provided)

File output
- Save the generated Markdown to /maps using the exact filename format: {mission name}.{date}.md
  - mission name: use the mission name as provided (retain spaces). If any characters are invalid for the OS (e.g., < > : " / \ | ? *), replace only those with dashes.
  - date: YYYY-MM-DD.

General rules for 4-player maps
- This MUST be a 4-player mission regardless of the source.
- Provide four fair deployment zones with clear measurements.
- Provide an objective marker layout with explicit measured placements. Use a consistent coordinate system.
- If the source is Pariah Nexus, amend/adapt rules to support 4 players (turn order, battle length, CP gain, scoring, reserves, etc.). Keep it brief and functional.

Coordinate system & placement standard
- Use a right-handed coordinate system with origin (0,0) at the bottom-left corner when facing the battlefield from one long edge.
- Measurements are in inches. battlefield_size defaults to 60"x44" (width x height). If a different size is provided, use that.
- When placing objectives, list each as: Objective N: (x, y), plus any extra constraints (e.g., "not within 6\" of DZs"). Ensure symmetry and legal distances.

### Map & Deployment (4 Players)
Provide an ASCII diagram that shows deployment zones A, B, C, D and objective markers 1–6, if any. Use table-like layout with compass directions. Include horizontal and vertical distances where useful.

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

Objective markers
- Provide the exact number and precise coordinates.
- State minimum distances from board edges, other objectives, and deployment zones as applicable.
- If objectives are player-placed, provide strict instructions for how and where to place them, including sequence and legal ranges.

4-player rules adaptations (when source = pariah-nexus)
- Turn order: e.g., randomize A→B→C→D for Battle Round 1, then serpentine or reseed each round; state which is used.
- Command points: CP gain per player per round; any starting CP modifications.
- Battle length: default 5 rounds unless the source says otherwise; adapt tie-breakers for 4 players.
- Reserves/Reinforcements: clarify arrivals when multiple players share edges; state timing windows.
- Scoring: adapt primary/mission rules to 4 players. Provide clear scoring lines that avoid duplicating book text.
- End-of-battle effects: clarify how any end-of-round or end-of-battle scoring triggers scale to 4 players.

Output format (Markdown only)
# {mission_name} — 4-Player Map (Pariah Nexus Variant if applicable)

- Date: {date}
- Battlefield Size: {battlefield_size or 60"x44"}
- Players: 4 ({variant or FFA})
- Summary: {mission_summary if provided}

## Coordinate System
- Origin (0,0) bottom-left; x increases to the right, y increases up. Units in inches.

## Deployment Zones
- DZ-A: {precise description}
- DZ-B: {precise description}
- DZ-C: {precise description}
- DZ-D: {precise description}

## Objective Markers
- Total: {objective_count}
- Placement rules: {consolidated constraints}
- Locations:
  - Objective 1: (x, y)
  - Objective 2: (x, y)
  - Objective 3: (x, y)
  - Objective 4: (x, y)
  - Objective 5: (x, y)
  - Objective 6: (x, y)
  - {…add/remove to match objective_count}

## Mission Rules (4-Player Adaptation)
- Turn Order: {method}
- Command Points: {start and per round}
- Battle Length: {rounds and end conditions}
- Reserves/Reinforcements: {timings/edges}
- Scoring:
  - Primary: {how to score per round}
  - Secondary: {if any, how to adapt or disable}
- Additional Effects: {null-zone/Blackstone effects if relevant; summarized}

## Setup Steps
1. Set battlefield size and orient coordinate system.
2. Mark deployment zones (DZ-A to DZ-D) as above.
3. Place objective markers per the locations and constraints listed.
4. Place terrain; keep lanes fair for all DZs. Avoid blocking the center entirely.
5. Determine alliances if variant = 2v2; otherwise, FFA.
6. Roll for turn order and begin the battle.

## Victory
- Highest total VP at battle end wins. Use {tie-breaker rule} if tied.

Conventions
- Use concise, unambiguous measurements.
- Do not include any text that is not part of the playable mission map.
- If a rule from the source cannot translate cleanly to 4 players, provide a minimal, fair substitute and clearly label it as an adaptation.
