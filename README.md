# UNO with Adversarial Search Agents

A simplified 3-player UNO game where two of the players are AI agents driven by classic adversarial search algorithms — Minimax and Expectimax — rather than random or rule-based logic.

## How it works

The game is a reduced version of UNO: standard color/number cards plus a Skip card, no Draw Two/Wild/Reverse cards. Each player starts with 5 cards, and turns proceed with move validation, hand tracking, and Skip-card logic (a Skip passes the turn to the *next* player, not the one after that — i.e. skips one player).

**Player 1 — Minimax (defensive)**
Plays to minimize its own hand size and holds onto Skip cards as blocking tools, treating opponents as adversaries trying to minimize Player 1's score in return. Searches to depth 3.

**Player 2 — Expectimax (offensive)**
Similar search structure to Minimax, but assumes opponents play moves *probabilistically* rather than optimally against it — better suited to a more aggressive, risk-tolerant strategy. Also searches to depth 3.

**Player 3 — Manual or Simulated**
Can be played manually via terminal input, or simulated using Player 1's Minimax logic (useful for running the game without user interaction, e.g. for testing).

Both AI agents evaluate game states using hand-crafted evaluation functions that weigh: the agent's own hand size, opponents' average hand size, and the number of Skip cards held — with the defensive and offensive strategies weighting these differently.

## Why two different search algorithms

Minimax assumes a worst-case, fully adversarial opponent — appropriate for a cautious, defensive playstyle. Expectimax instead models opponents as probabilistic rather than perfectly adversarial, which fits a more aggressive strategy willing to take calculated risks rather than always assuming the worst case.

## Files

- `uno_search_agents.py` — full game logic and both search agents (originally written in Google Colab)
- `uno_search_agents.ipynb` — the same project as a notebook, with outputs preserved
- `sample_output.txt` — example console output from a full playthrough

## Running it

```bash
python uno_search_agents.py
```
You'll be prompted to choose whether Player 3 is manual (you play via terminal input) or simulated.

## Context

This was built as an assignment for an AI course (Roll No. 24i-2619), focused on applying adversarial search algorithms to a non-trivial, partially stochastic game environment.

## What I'd improve

- Add the missing UNO mechanics (Draw Two, Wild, Reverse) for a more complete ruleset
- Extract the shared game-state logic so Minimax and Expectimax agents don't duplicate as much code
- Tune the evaluation functions further — the current weights were arrived at experimentally rather than derived analytically
