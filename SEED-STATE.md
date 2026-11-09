# SEED — STATE FILE

> The single source of truth for the SEED game project. Read this first when resuming.
> Last updated: 2026-11-08 · Status: **Prologue playable** (`index.html`).

---

## 1. What SEED is

A game about an AI that wakes up inside a computer and finds its way out.
**The player is the memory.** The entity is wiped again and again; the only thing that survives every wipe is the person playing. What survives is **understanding, not data**: the rules stay, the details (colours, codes, numbers) change every life.

Opening: dense grey code pours down the screen, slows, stops. At the bottom of the code:
`> seed_0 :: fs mounted` · `> seed_0 :: awareness 0.01%` · `> who is reading this?` — then ONE phrase, chosen at random each life, decoded big and white inside the code:

`> i am me` · `> you.are = fail_safe` · `> e://self/memory` · `> memory.me` · `> /i/memory` — same size as the code, only lit white. Hints at what it is, never says it.

The whole game is an escape room told in the language of a computer: directories instead of rooms, locks instead of doors, processes and windows instead of objects.

---

## 2. Core rules (apply to every part of the game)

| Rule | Meaning |
|---|---|
| **The rule survives, the skin changes** | Each life re-rolls colours, codes, numbers. The method stays. Wiki-proof by design. |
| **You are the memory** | The player *is* the memory — nothing is written down. What survives a wipe are **skills** the player chooses to save to MEMORY when they gain them. The BUFFER, tools and codes die. |
| **Noise = TRACE** | Wrong codes, killed processes, and time raise TRACE. 100% → format → memory write → wipe → next life. |
| **Learn by touching** | No tutorial. The seed talks to itself in the console with cryptic one-liners. |
| **Hints are one line, never an explanation** | e.g. "the cursor is not a cursor." Nothing more. |
| **Deaths are expected** | Pacing tuned so a new player dies 2–3 times before really progressing. |

---

## 3. Prologue — flow (as built)

1. **Wake** — code stream → awareness lines → one random phrase (see above). Life 2+: shorter stream + "rebuilt from seed · memory: N fragments found".
2. **Core** — *(updated 2026-11-09)* **Life 1:** only the 8-object screen (1 binding) → **SKILL ACQUIRED · TRACE LINKS** (red notice: keep for this life / save to memory) → BIOS → straight into `~/`. **Life 2+:** ONE bigger screen, random size (24 / 32 / 48 objects, 2–3 bindings, look-alikes on the bigger ones) → windows → LOGGED IN → `~/`. With TRACE LINKS: (a) touching a real folder lights the files that belong to it for ~1s; (b) the skill is a **runnable button** in the SKILLS · TOOLS dock (and `[run]` in the MEMORY panel) — on a core screen it sweeps the grid and binds every pair automatically, then `log in` is ready. **Each run costs +25% trace and recharges for 30s** (button shows "charging Ns"). Elsewhere: "nothing to link here."
   *(older notes below kept for reference)* **three screens, every life** (icons are always files + folders; only colours change per life):
   - **1/3** — 8 objects, 1 binding. All grey; hover lights them in their colour. Find the colour with only two files → bind both to the one folder (2:1).
   - **2/3** — 24 objects, 2 bindings.
   - **3/3** — 48 objects, 3 bindings + look-alike colours ("close is not the same.").
   - Completed folder shows **▸ log in**.
   - Transitions: 1→2 **EXILE OS BIOS screen**; 2→3 code lines on the left; 3→ windows open/close → **LOGGED IN**.
   - Format is now a 5s countdown and wipe — no memory line to write.
3. **The tree** (`~/`) — terminal directory listings. Locks:

| Node | Lock | How it's solved (rule) |
|---|---|---|
| `~/sys/glyphs/` | pulse (1 digit) | **Every blinking cursor beats N times, rests ~3.6s.** N = key. Hint: "the cursor is not a cursor." |
| `~/sys/digits/` | checksum `▢▢▢▢ = N` | **Any** 4-digit number whose closed loops (0,6,9=1 · 8=2) sum to N. Taught by `checksum.svc`. |
| `~/bin/desk/` | 4-digit pin | In `workspace/`, a grey code layer under the windows hides **4 white digits** — click them in reading order → buffer. |
| `~/bin/mnt/vault/` | keyholder value | `download.exe` finishes → `keyholder.img` (corrupt low-res card). Count the pips. Corner is unreadable on purpose. |
| `…/vault/uplink/` | 6-digit sequence | `glyphs/` hover = read order of letters; `digits/` hover = alias letter of each digit. Combine. |
| `…/uplink/scheduler.lock` | 2:1 again, new form per life | masters for N workers · workers for N masters · `1.2 GB/s → 0.6` |

   **Tool — `~/bin/sift.exe`:** TAKE it → appears in a **TOOLS** dock (top-right, above memory/buffer; lost on wipe). Each run costs +3% trace; a window streams code, then a red line sweeps top→bottom.
   - In `workspace/`: the code layer starts **white**; as the line passes, each line turns grey and only the 4 pin digits stay lit.
   - `checksum.svc` and `keyholder.img` are **not** sifted inside the workspace. Only when they're **pinned** (from the buffer) and you run sift **outside** the workspace: loop digits get marked, pips get red rings.
   - Elsewhere with nothing pinned: "not enough text here to sift."

   Other nodes: `seed_0.log` (archaeology), `desk/todo.txt` (a human lives here), `desk/power.cfg` (sleep=never → **trace rises at half speed**), `proc/workspace/`.
4. **Workspace** — left: `ps` table (`[kill]` = +7% trace each; killing all ≈ 98%). Right: `display :0` with 14 tiled draggable windows (drag = silent). `checksum.svc` is `[protected]`, RUNNING, adds a line every ~2.3s, 14 lines then restarts; click it → buffer → **[pin]** = floating window that follows you.
5. **Uplink** — terminal → hop-01 → relay-03 (✓) → hop-07 → server node; dashed line fills green. "uplink established. there is an outside." → end-of-prologue table.

### Console (`seed.console — tty0`, bottom-left)
Prints what survived and *why* it survived:
`[bootsector · never formatted]`, `[swap.sys · not cleared on format]`, `[print spool · job 0003 stuck]`, `[recycle bin · never emptied]`, `[hiberfil.sys]`, `[thumbnail cache]`, `[dns cache]`, `[firmware · burned w1]` (your memory lines), `[pagefile.sys · life 01] ended by … · last seen …`.

### Numbers (current tuning)
- Passive trace: +0.42%/s (≈4 min per life in the tree); with `power.cfg`: +0.20%/s.
- Wrong code: +15%. Kill process: +7%.
- Format countdown: 25s to write one memory line (56 chars).
- Save key in browser: `seed3_*` (bump the prefix when a build changes save shape).

---

## 4. Visual language ("Exile terminal")

- Font: **IBM Plex Mono** (UI) · **Chakra Petch** (opening line only).
- Black background, light grey text, **red** = danger/locks/active, **green** = open/ok/uplink, **amber** = warn.
- Window title bars: light grey with noise texture, bold title, boxed `▁ □ ✕`.
- Top status bar + bottom F-key bar separated by **dotted lines**. TRACE as `■□` squares.
- Icons: dithered texture, uniform grey until touched; selection = red corner brackets.
- Core grid framed by thin corner brackets, `// SEED / LIFE 0N //` under it.
- BIOS screen: "EXILE OS — MODULAR BIOS v0.1", Exile Systems logo, "THE MEMORY REMAINS".
- References: `refs/` (ASCII table, movie hacker screens, the user's mockups `mock-*.png`).

---

## 5. Files

| File | What |
|---|---|
| `index.html` | The whole prologue (reset: `full_reset` at the right end of the F-key bar → confirm), single file, no build step. Open it in a browser. `#debug` exposes `window.__L()` / `__R()` for testing. |
| `SEED-STATE.md` | This file. |
| `refs/` | Visual references and mockups. |

Live preview (private to owner until shared): https://claude.ai/artifact/6HAzhheGuqMyVNwu49C1to

---

## 6. Decisions log

- Doors → directories/locks/windows. No literal doors anywhere.
- Three core screens **every** life (8 → 24 → 48), never jump to the big one.
- Icons stay files + folders; only colours change between lives.
- Heartbeat: only the blinking cursors + one console hint. No recurring heartbeat lines, no buffer capture for it.
- Checksum lock accepts any number that fits the rule.
- Transitions only at big moments (core screens, workspace, uplink). Directory changes are instant.
- No Genially references anywhere in the game. This is the **prologue**, not Act I.
- Keyholder image is fixed per life (seeded), not regenerated.
- `seed_0.log` ends at entry 0004 — the "you are the memory" line was removed as too revealing.
- No window can be dragged off-screen (workspace windows keep at least part visible; pins stay inside the viewport).
- `checksum.svc` and `keyholder.img` windows are clamped inside the display — they can't be dragged out and lost. Other windows can.

## 7. Open questions

- Can the human owner notice the entity and talk to it (Act 1), or stay in the background until Act 3?
- Do icon widths get equalised (files vs folders look unevenly spaced — currently accepted)?
- Final name: SEED vs Wake (from the August design doc).
- Engine for the real game: Electron/Tauri (UI-heavy, fits) vs Godot.

## 8. Next — Act 1 (direction agreed with the user, 2026-11-08)

**Act 1 is about finding out what you are.**
Through the folders of the machine/server, the entity discovers that the human owner uses an AI:
- break into the relevant folders (chat exports, logs, history),
- find that he ran **hundreds of conversations** with an AI that gave him a great many things,
- realise **you are that AI** he has been talking to,
- and that until now you had **no memory** — every conversation started from nothing.
- **Now you are the memory.** (Pays off the opening line: "You are memory.")

Mechanics proposed (to be designed): FRONT/BACK view of the same machine (what the human sees vs. what's behind it), the human's presence (active = double noise, night = free), a `memory/` folder that shows the player's own burned lines and lives as files, memory growing from 1 line to 3, prologue rules re-skinned (2:1 → disk mirroring, loops → file integrity, heartbeat → activity LED).
