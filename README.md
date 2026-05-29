<div align="center">

# 🌽 Kangnengui's School Conquest (강냉이의 학교정복기)

**A 2D turn-based RPG set in a university campus, built from scratch with Python + Tkinter + Pygame.**

[![Language](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![GUI](https://img.shields.io/badge/GUI-Tkinter-FFD43B?logo=python&logoColor=black)](https://docs.python.org/3/library/tkinter.html)
[![Audio](https://img.shields.io/badge/Audio-Pygame-000000?logo=pygame)](https://www.pygame.org/)
[![Award](https://img.shields.io/badge/🏆_Kangnam_Univ-Outstanding_Work-success)](https://sae.kangnam.ac.kr)

🇰🇷 [한국어 README](./README.ko.md) · 📚 [Documentation](./docs) · ▶️ [Demo Video](https://youtu.be/bvAGlPi2S08)

</div>

> ℹ️ **Mirror repository.** This is a mirror of the canonical repo
> **[`python-project`](https://github.com/JaylenHan/python-project)** (the original final submission, Dec 2023).
> The game code (`Kangnam_University.py`) is identical. For the authoritative source and history, use the canonical repo.

---

## Overview

**Kangnengui's School Conquest** is a 2D turn-based RPG developed as the final project for the
*Applied Python* course at Kangnam University (Dept. of ICT Convergence Engineering, VR major).
Inspired by the adventure-and-growth loop of *Pokémon* and *MapleStory*, the game reimagines real
campus life as a fantasy world: pick one of four classmates, explore the campus map, clear three
escalating boss battles (Student Council → Professor → President), earn coins in arcade-style
mini-games, and spend them at the shop.

The project was selected as an **Outstanding Work** by the department.

> Built end-to-end by a team of four ("지민아 뭐라도 좀 해봐") in a single Python module of ~2,100 lines,
> using only the standard `tkinter` canvas for rendering and `pygame.mixer` for audio.

## Highlights

- 🎮 **4 playable characters**, each with unique stats (HP / Power / Gauge) and art sets
- ⚔️ **Turn-based battle system** — basic attacks, gauge-charged special skills, items, and escape
- 👹 **3 escalating boss fights** with pre/post-battle dialogue branches (win / lose paths)
- 🕹️ **3 built-in mini-games** to farm coins (target shooting, Pac-Man style chase, credit dodge)
- 🛒 **Shop & item economy** — buy HP / MP / energy potions and stat boosts with earned coins
- 🗺️ **Grid-based map exploration** across 7 campus locations with interaction tiles & random chests
- 🔊 **Full audio** — looping BGM per area, dedicated boss themes, and attack SFX via `pygame.mixer`
- 📖 **Story mode** — a 6-panel intro comic and a dialogue system driving the campaign

## Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.x |
| Rendering / UI | `tkinter` (Canvas, Toplevel, widgets) |
| Audio | `pygame.mixer` (channels + `Sound`) |
| Std lib | `time`, `random` |
| Tooling | Visual Studio Code, GitHub, Notion, Discord, Google Drive |

## Gameplay at a Glance

### Playable Characters

| Character | HP | Power | Gauge | Vibe |
|---|---:|---:|---:|---|
| King 승헌 | 200 | 20 | 2 | Tanky leader |
| Clown 지민 | 150 | 30 | 2 | Glass-cannon |
| Baby 민서 | 170 | 25 | 2 | Balanced |
| Oldest 병찬 | 100 | 50 | 2 | High-risk, high-damage |

### Bosses (in order)

| Boss | HP | Attack range |
|---|---:|---|
| 학생회 (Student Council) | 300 | 10–15 |
| 교수님 (Professor) | 600 | 15–20 |
| 총장님 (President) | 1,200 | 20–30 |

### Mini-games

| In-game title | Class | Author | Mechanic |
|---|---|---|---|
| 과녁 맞히기 (Target Shooting) | `Targetgame` | 민서 | Hit timed targets for points |
| 팩맨 / "King-man" | `PackMan` | 승헌 | Pac-Man style chase to grab items/coins |
| 대학 학점 먹기 (Credit Game) | `CollegeGame` | 지민 | Collect credits & coins under pressure |

See [docs/02-gameplay/GAME_DESIGN.md](./docs/02-gameplay/GAME_DESIGN.md) for the full design breakdown.

## Getting Started

> ⚠️ **Important:** the game loads every asset by *bare filename* (e.g. `PhotoImage(file="start_screen.png")`),
> but the assets in this repo are organized into sub-folders. You must stage the assets into the
> working directory before running. See the full guide for the one-liner.

```bash
# 1. Install the only third-party dependency
pip install pygame

# 2. Stage assets next to the script (assets are stored in sub-folders in the repo)
#    macOS / Linux:
cp Character_Image/* Map_Etc_Image/* Skill_Image/* Sound/* .

# 3. Run
python Kangnam_University.py
```

Full setup, troubleshooting, and the asset-path explanation: [docs/03-guides/GETTING_STARTED.md](./docs/03-guides/GETTING_STARTED.md).

## Project Structure

```
python_project/
├── Kangnam_University.py   # Entire game (~2,100 lines, single module)
├── Character_Image/        # 42 sprites — 4 players + 3 bosses (idle/move/battle/chat/skill)
├── Map_Etc_Image/          # 44 images — maps, UI, cursors, story panels, events
├── Skill_Image/            # 16 images — skill & attack motion frames
├── Sound/                  # 10 audio files — BGM, boss themes, attack SFX (.ogg)
└── docs/                   # Project documentation (this set)
```

The codebase is a single module organized into five classes —
`GameCharacter`, `Targetgame`, `PackMan`, `CollegeGame`, `Store` — plus a flat set of game-flow
functions driven by global state. Architecture details:
[docs/01-architecture/SYSTEM_ARCHITECTURE.md](./docs/01-architecture/SYSTEM_ARCHITECTURE.md).

## Documentation

| Doc | What's inside |
|---|---|
| [00 · Project Brief](./docs/00-overview/PROJECT_BRIEF.md) | Goals, team, roles, award, scope |
| [01 · System Architecture](./docs/01-architecture/SYSTEM_ARCHITECTURE.md) | Module layout, classes, state model, render/audio loop |
| [02 · Game Design](./docs/02-gameplay/GAME_DESIGN.md) | Characters, bosses, maps, battle, mini-games, shop |
| [03 · Getting Started](./docs/03-guides/GETTING_STARTED.md) | Install, asset staging, run, troubleshooting |
| [04 · Retrospective & Roadmap](./docs/04-devlog/RETROSPECTIVE.md) | Lessons learned, known limits, future direction |

## Roadmap

Ideas captured during development (not yet implemented):

- Character customization (hair, outfits, accessories)
- More mini-game types and shop items
- Multiplayer co-op / PvP battles
- Expanded story & quest lines

## Credits

**Team "지민아 뭐라도 좀 해봐"** — Kangnam University, Applied Python (final project).

**한승헌 (Jaylen Han)** — Team lead · planning · core & mini-game development · optimization · presentation.

- 🏆 Selected as an Outstanding Work by the Dept. of ICT Convergence Engineering (VR major)
- ▶️ [Final demo video](https://youtu.be/bvAGlPi2S08)
- 📦 Canonical repo: [`python-project`](https://github.com/JaylenHan/python-project)

## License

Educational project. No formal license is currently attached; please contact the author before reuse.
