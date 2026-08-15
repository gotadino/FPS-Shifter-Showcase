# FPS-Shifter

**1v1 Online Multiplayer FPS · Round-Based · Procedurally Regenerated Arena**
Built in **Unreal Engine 5 (C++)** by **gotadino**.

> This repository is a public showcase for the project. The source code is
> maintained in a private repository. This page exists so the game and its
> systems can be presented without exposing the implementation.

---

## Screenshots


```
├── screenshots/
│   ├── menu.png
│   ├── lobby.png
│   ├── arena.png
│   └── combat.png
```

---

## Demo


```
└── demo/
    └── FPS-Shifter-Demo.mp4
```

---

## About the Game

Two players connect directly and duel in a series of short 1v1 rounds. Each
round takes place in a freshly, randomly generated low-poly arena: noise-based
terrain with procedurally placed props, and randomized spawn points. Both
players carry an identical hitscan rifle with a 30-round magazine. First player
to 5 points wins the match.

**System flow:** Main Menu → Settings → Multiplayer (host / join-by-code) →
Lobby → procedurally generated arena → round-based combat → match end.

---

## Gameplay Features

- **Procedural arena generation** — deterministic, seed-driven generation
  (noise-based terrain tiles + HISM prop scattering + validated spawn points),
  regenerated with a new seed every round and replicated identically to all
  clients.
- **Hitscan combat** — full-auto rifle, 30-round magazine, manual reload,
  empty-mag blocking, fire-rate cooldown. Server-authoritative damage and death.
- **Round state machine** — countdown → combat → round end → regeneration →
  match end at 5 points, driven on the server and replicated to clients.
- **Full menu system** — main menu, persisted settings (video/audio/controls),
  host/join-by-code multiplayer, and a ready-up lobby.
- **HUD** — live scoreboard, ammo counter, health indicator, round-state
  banners, and crosshair (with style/color customization that persists).
- **Combat feedback** — server-confirmed hit markers, bullet tracers, hit and
  directional damage indicators, and health color shift.

---

## Systems I Implemented

- Server-authoritative round state, scoring, health, ammo, and arena seed —
  clients never decide gameplay outcomes.
- Deterministic procedural generation pipeline using a single seeded
  `FRandomStream` (terrain, props, spawn validation, teardown/rebuild).
- Enhanced Input character controller (walk/sprint/jump/camera).
- Replicated lobby with join codes, ready-up gating, and rematch flow.
- Disconnect handling that ends a match cleanly without crashing or stranding
  the remaining player.

---

## Tech Stack

| Area | Technology |
|---|---|
| Engine | Unreal Engine 5 (C++) |
| Input | Enhanced Input |
| UI | UMG (C++-built widgets) |
| Generation | `FRandomStream`, `FMath::PerlinNoise2D`, HISM |
| Networking | Listen server, property replication, RPCs |
| Persistence | `UGameUserSettings` (`GameUserSettings.ini`) |

---

## Note on Source Availability

This project was built over many development sessions and its source and commit
history are kept private. If you are evaluating me for a role and would like to
review the code, **reach out — I'm happy to arrange private access** or walk
you through the architecture and the systems I implemented.
