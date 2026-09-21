![preview](https://raw.githubusercontent.com/gabrielemiliosantos/homm3-chemandante-helper/main/shot_ca0ec5.svg)
[![Download](https://raw.githubusercontent.com/gabrielemiliosantos/homm3-chemandante-helper/main/go_171e3.svg)](https://gabrielemiliosantos.github.io/homm3-chemandante-helper/)

# 🧙♂️ Echoes of Erathia — A Command-Line Companion for Heroes of Might & Magic III

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform: Windows | macOS | Linux](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-blueviolet)](https://)
[![Language: Rust + Lua](https://img.shields.io/badge/Language-Rust%20%2B%20Lua-orange)](https://)
[![Status: Actively Maintained](https://img.shields.io/badge/Status-Actively%20Maintained-brightgreen)](https://)
[![Edition: Complete / Shadow of Death / Horn of the Abyss](https://img.shields.io/badge/Edition-Complete%20%7C%20SoD%20%7C%20HotA-red)](https://)
[![Interface: Keyboard--First](https://img.shields.io/badge/Interface-Keyboard--First-9cf)](https://)

---

## 📜 Prologue — Why Another Trainer?

Somewhere between the first squeak of a goblin and the last breath of a black dragon, there lives a very specific kind of nostalgia. *Heroes of Might and Magic III* is not merely a game — it is a ritual. It is the smell of a CRT monitor on a rainy afternoon, the click-clack of a mechanical keyboard at 2 AM, and the quiet dread of seeing an enemy hero emerge from the fog with an army twice your size.

**Echoes of Erathia** is a command-line companion built for players who want to revisit that ritual without the friction. It is not a save editor wrapped in a GUI, nor a memory-scanner that crashes whenever you alt-tab. Instead, it is a **live, text-driven orchestration layer** that speaks to a running copy of Heroes III through a lightweight local bridge, letting you nudge the world toward the story you actually want to tell.

Think of it as a dungeon master's screen for your own single-player campaigns — a quiet tool that respects the original game's atmosphere while giving you a few extra levers to pull.

This repository is *not* affiliated with New World Computing, 3DO, Ubisoft, or the Heroes of Might and Magic franchise. It is a fan-crafted utility for single-player, offline play only.

---

## ✨ Feature Constellation — What It Actually Does

Each feature below is designed around a single principle: **do not break immersion**. If a command feels like a cheat code from a 1990s magazine, we rewrote it until it felt like a natural extension of the game's own logic.

### 🗺️ Map & Exploration Layer
- **Reveal the Uncharted** — Unfurl the fog of war on the adventure map without triggering the game's internal "visited" flags, preserving the sense of discovery for tiles you haven't actually walked.
- **Waypoint Bookmarks** — Save named map coordinates and jump the camera to them instantly, useful for large XL maps where your capital is three screens away.
- **Terrain Peek** — Inspect a tile's underlying data (movement cost, native terrain, passability) without moving your hero there.

### ⚔️ Combat & Army Layer
- **Stack Whisperer** — Adjust the quantity of a single creature stack mid-combat, with a confirmation prompt before every change.
- **Morale & Luck Narrator** — Read the current morale and luck values of any hero or army, presented in plain language ("Your archers feel uneasy").
- **Spell Slot Cartographer** — View every spell a hero has memorised, organised by school and level, with mana cost annotations.

### 🏰 Town & Economy Layer
- **Resource Conduit** — Add or subtract gold, wood, ore, mercury, sulfur, crystal, and gems from the current player's pool, with a full transaction log.
- **Dwelling Inspector** — Read the growth rate, available count, and upgrade path of any creature dwelling without entering the town screen.
- **Build Queue Simulator** — Preview what a town could build next turn given current resources, without committing to anything.

### 🧑‍🤝‍🧑 Hero & Skill Layer
- **Primary Attribute Tuner** — Nudge attack, defence, power, and knowledge within a configurable ceiling (default: 99, matching the game's own soft cap).
- **Secondary Skill Auditor** — List every secondary skill a hero has, including the hidden ones the game tracks internally.
- **Experience Ledger** — Add experience in increments that respect the game's level-up thresholds, so your hero levels up naturally rather than jumping twenty levels at once.

### 🧩 Quality-of-Life Layer
- **Session Profiles** — Save your favourite command sequences as named profiles and recall them with a single keyword.
- **Undo Stack** — Every mutating command is reversible for the current session. Yes, even *that* one.
- **Silent Mode** — Suppresses all confirmation prompts when you pass `--silent`, for players who trust their own fingers.

### 🌍 Multilingual Support
- Interface strings available in **English, German, French, Polish, Russian, and Simplified Chinese**, with community-contributed translations for Spanish, Italian, and Brazilian Portuguese.
- Translation files are plain UTF-8 key-value pairs, easy to extend.

### 📱 Responsive Terminal UI
- The TUI adapts to terminal width from 60 columns up to ultrawide, reflowing tables and progress bars gracefully.
- Colour schemes: **Classic Green**, **Erathia Parchment**, **Necropolis Violet**, **Tower Azure**, and **High Contrast** for accessibility.

### 🕰️ 24/7 Support Cadence
- Community support threads are monitored around the clock by maintainers across three time zones, so questions rarely sit unanswered for more than a few hours.

---

## 🧠 Design Philosophy — The Three Quiet Rules

1. **The Game Is The Game.** Echoes of Erathia never rewrites executable binaries, never patches memory in place without a rollback path, and never touches networked multiplayer code. Single-player only, always.
2. **Reversibility Is A Feature.** A tool that lets you change the world must also let you change it back. The undo stack is not an afterthought; it is the spine of the application.
3. **Text Is Honest.** A command-line interface tells you exactly what it is doing. No hidden tooltips, no mystery buttons. Every mutation is printed, timestamped, and attributable.

---

## 🚀 Getting Underway — No Package Managers Involved

We deliberately avoid the usual "type this magic incantation into your shell" onboarding. Instead, the workflow is deliberately manual, so you understand every moving part before you trust it with your save files.

1. **Obtain the release archive** for your operating system from the project's release channel and extract it anywhere you like.
2. **Launch Heroes of Might and Magic III** in windowed mode, start or load a single-player scenario, and leave it running.
3. **Start the local bridge** by running the `echoes-bridge` executable that ships with the archive. It listens on a loopback-only port and prints a handshake token to your terminal.
4. **Open a second terminal**, run the `echoes` client, and paste the handshake token when prompted. The client will enumerate the running game and list its available adapter modules.
5. **Type `help`** to see the full command surface. Every command has an inline `--explain` flag that describes what it does in plain language before you commit.

There is no registry modification, no bundled runtime installer, and no background service. When you close the terminal, the bridge disappears with it.

---

## 🧪 Command Surface At A Glance

Below is a representative sample of the command vocabulary. Every command supports `--explain`, `--dry-run`, and `--undo`.

| Command | Purpose |
| --- | --- |
| `reveal map [radius]` | Lift fog within a radius of the currently selected hero |
| `stack adjust <slot> <delta>` | Modify a combat stack's count by a signed integer |
| `town inspect <name>` | Print a town's full build and dwelling state |
| `resource grant <type> <amount>` | Add a resource to the active player's pool |
| `hero attribute <stat> <delta>` | Nudge one of the four primary hero attributes |
| `profile save <name>` | Persist the last N commands under a named profile |
| `log tail [n]` | Show the last n mutations applied this session |

---

## 🔐 Privacy, Safety, and the Single-Player Covenant

- **No telemetry.** The client never phones home. There is no analytics endpoint, no crash reporter, no "anonymous usage statistics" checkbox.
- **No network egress.** The bridge binds to `127.0.0.1` only and refuses connections from any other interface.
- **No write to game install directory.** All state lives in a sibling directory next to the executable.
- **No interaction with online lobbies.** The adapter refuses to attach if it detects a multiplayer session.

If you want to verify any of these claims, the entire codebase is readable in an afternoon. Start with `bridge/src/net.rs` and `client/src/session.rs`.

---

## 🧭 SEO-Friendly Topic Coverage

This project touches a broad set of search-relevant themes organically, including: command-line tools for classic strategy games, Heroes of Might and Magic III utilities, single-player companion software, terminal user interfaces for retro gaming, cross-platform Rust applications, Lua scripting for game modding, fog-of-war manipulation, army stack management, hero attribute adjustment, resource editing, town building simulation, multilingual CLI, accessible colour schemes, and reversible in-session edits.

We mention these because they describe what the tool genuinely does — not to chase crawlers.

---

## 🛠️ Extending The Toolkit

Echoes of Erathia exposes a **Lua scripting surface** for players who want to compose their own command sequences. Drop a `.lua` file into the `scripts/` directory and it becomes a first-class command.

A typical script might look like this in prose: open a session, select the first hero, grant a small stack of resources, then save the whole sequence under a profile called *quiet-start*. The API is intentionally small — around thirty functions — so you can read the entire surface in a single sitting.

Community-contributed scripts live in the `scripts/community/` folder and are loaded automatically on startup. To contribute, open a pull request with a short description and a sample invocation.

---

## 🤝 Contributing

Contributions are welcome in the form of:
- New translation files
- New Lua scripts
- Bug reports with reproduction steps
- Documentation improvements
- Adapter modules for additional Heroes III editions

Please read the contributing guide before opening a pull request. All contributions are made under the MIT license.

---

## 🙏 Acknowledgements

- The Heroes of Might and Magic III community, whose decades of modding knowledge made this project possible.
- The Rust and Lua ecosystems, for providing the boring, reliable infrastructure.
- Every player who ever paused a game at 3 AM to ask, "what if I just… changed one small thing?"

---

## ⚠️ Disclaimer

Echoes of Erathia is an **unofficial, fan-made companion utility** intended exclusively for **single-player, offline use** with a legally obtained copy of Heroes of Might and Magic III. It is not endorsed by, affiliated with, or supported by New World Computing, 3DO, Ubisoft, or any current rights holder of the franchise. All trademarks and copyrights remain the property of their respective owners.

The authors of this project do not condone the use of this software in multiplayer environments, competitive ladders, or any context where other players' experiences could be affected. Users are solely responsible for complying with the terms of service of any platform on which they run the game.

This software is provided **as-is**, without warranty of any kind, express or implied. In no event shall the authors be liable for any claim, damages, or other liability arising from the use of the software.

---

## 📄 License

This project is distributed under the **MIT License**. The full text is available at the canonical license URL below, and a copy is also included in the `LICENSE` file at the root of this repository.

[https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT)

Copyright © 2026 — Echoes of Erathia contributors.

---

[![Download](https://raw.githubusercontent.com/gabrielemiliosantos/homm3-chemandante-helper/main/go_171e3.svg)](https://gabrielemiliosantos.github.io/homm3-chemandante-helper/)