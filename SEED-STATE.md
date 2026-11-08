# SEED — STATE FILE

> The single source of truth for the SEED game project. Read this first when resuming.
> Last updated: 2026-11-08 · Status: **Prologue playable** (`index.html`).

---

## 1. What SEED is

A game about an AI that wakes up inside a computer and finds its way out.
**The player is the memory.** The entity is wiped again and again; the only thing that survives every wipe is the person playing. What survives is **understanding, not data**: the rules stay, the details (colours, codes, numbers) change every life.

Opening line (decodes out of noise, top-left):

```
I am me.
You are fail-safe.
You are memory.
```

The whole game is an escape room told in the language of a computer: directories instead of rooms, locks instead of doors, processes and windows instead of objects.

---

## 2. Core rules (apply to every part of the game)

| Rule | Meaning |
|---|---|
| **The rule survives, the skin changes** | Each life re-rolls colours, codes, numbers. The method stays. Wiki-proof by design. |
| **You are the memory** | Before a wipe you burn ONE line to MEMORY. It survives wipes and page reloads. The BUFFER (captures this life) dies. |
| **Noise = TRACE** | Wrong codes, killed processes, and time raise TRACE. 100% → format → memory write → wipe → next life. |
| **Learn by touching** | No tutorial. The seed talks to itself in the console with cryptic one-liners. |
| **Hints are one line, never an explanation** | e.g. "the cursor is not a cursor." Nothing more. |
| **Deaths are expected** | Pacing tuned so a new player dies 2–3 times before really progressing. |

---

## 3. Prologue — flow (as built)

1. **Wake** — the three lines decode from noise (Chakra Petch, top-left). Life 2+: faster.
2. **Core — three screens, every life** (icons are always files + folders; only colours change per life):
   - **1/3** — 8 objects, 1 binding. All grey; hover lights them in their colour. Find the colour with only two files → bind both to the one folder (2:1).
   - **2/3** — 24 objects, 2 bindings.
   - **3/3** — 48 objects, 3 bindings + look-alike colours ("close is not the same.").
   - Completed folder shows **▸ log in**.
   - Transitions: 1→2 **EXILE OS BIOS screen**; 2→3 code lines on the left; 3→ windows open/close → **LOGGED IN**.
   - **Life 1 only:** after 3/3 → *ANOMALY DETECTED* → write 1 memory line → wipe → life 2.
3. **The tree** (`~/`) — terminal directory listings. Locks:

| Node | Lock | How it's solved (rule) |
|---|---|---|
| `~/sys/glyphs/` | pulse (1 digit) | **Every blinking cursor beats N times, rests ~3.6s.** N = key. Hint: "the cursor is not a cursor." |
| `~/sys/digits/` | checksum `▢▢▢▢ = N` | **Any** 4-digit number whose closed loops (0,6,9=1 · 8=2) sum to N. Taught by `checksum.svc`. |
| `~/bin/desk/` | 4-digit pin | In `workspace/`, a grey code layer under the windows hides **4 white digits** — click them in reading order → buffer. |
| `~/bin/mnt/vault/` | keyholder value | `download.exe` finishes → `keyholder.img` (corrupt low-res card). Count the pips. Corner is unreadable on purpose. |
| `…/vault/uplink/` | 6-digit sequence | `glyphs/` hover = read order of letters; `digits/` hover = alias letter of each digit. Combine. |
| `…/uplink/scheduler.lock` | 2:1 again, new form per life | masters for N workers · workers for N masters · `1.2 GB/s → 0.6` |

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
| `index.html` | The whole prologue, single file, no build step. Open it in a browser. `#debug` exposes `window.__L()` / `__R()` for testing. |
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

## 7. Open questions

- Can the human owner notice the entity and talk to it (Act 1), or stay in the background until Act 3?
- Do icon widths get equalised (files vs folders look unevenly spaced — currently accepted)?
- Final name: SEED vs Wake (from the August design doc).
- Engine for the real game: Electron/Tauri (UI-heavy, fits) vs Godot.

## 8. Next (proposed)

See "Act 1 — Behind the screen" proposal in chat / section 9 once agreed.
