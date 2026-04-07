# MAX-Custom
# PROJECT_CONTEXT.md

**Project: MIDI Captain MAX Custom (MAX) — Custom Firmware**

**Current active version:** `MAX Custom_v1.8.0-1.py`  
**Last updated:** April 05, 2026  
**Project status:** Stage 1 completed, Stage 2 completed, Stage 3 completed

## 1. Project Goals

The main goal is to create a convenient, flexible, and reliable custom firmware for the **Paint Audio MIDI Captain MAX**, based on the official MAX firmware while preserving maximum compatibility.

**Key Principles:**
- Add new modes (`one_shot`, `select` / radio, `long_shot`, etc.) **modularly**, without breaking existing code.
- `one_shot` mode must work for **any** button.
- `select` (radio) mode must work **only** for PC buttons (`type: "pc"`), as an addition to existing behavior.
- When a new official MAX version is released, our patches should be easy to re-apply.
- Never modify stable versions without explicit agreement.

## 2. Files and Versions

**Active versions:**
- `MAX Custom_v1.8.0-1.py` — current main version (fork of MAX_v1.8.0 + our modifications)
- `config02.json` — active configuration file

**Frozen / Reference versions:**
- `MAX_v1.8.0.py` — clean official version from Max Cascone
- `MAX Custom_v1.8.0-1.py` — stable version with `one_shot` and `select` modes (Stages 1–3)

**Supporting materials:**
- `.msl` scripts, original Helmut firmware, etc.

## 3. Completed Stages

### Stage 1 — Adding universal `one_shot` mode
**Status:** Completed  
**Date:** March 31, 2026  
**Base:** `MAX_v1.7.0.py` (clean)  
**Result:** `MAX Custom_v1.7.0-1.py`

**Achievements:**
- Added `"one_shot"` mode for any button
- Sends value only on press, no release (0) message
- LED and display state change **only** via host feedback

### Stage 2 — Adding `select` (radio) mode for PC buttons
**Status:** Completed  
**Date:** April 05, 2026  
**Base:** `MAX Custom_v1.7.0-1.py`

**Goal:**
- Add mode `"mode": "select"` **only** for buttons with `type: "pc"`
- When pressed, the button stays lit permanently; all other buttons in the same group turn off
- Do not break existing `toggle` and flash behavior for PC buttons
- Keep changes modular (add functions, minimal replacements)

### Stage 3 — Porting `one_shot` and `select` to MAX_v1.8.0 platform
**Status:** Completed  
**Date:** April 06, 2026  
**Base:** `MAX_v1.8.0.py`  
**Result:** `MAX Custom_v1.8.0-1.py`

## 4. Future Plans

### Stage 4 — `long_shot` mode (long press)
**Status:** Planned

**Goals:**
- New mode that triggers after holding a button for 500 ms
- Can be combined with other modes (`one_shot`, `toggle`, `select`, etc.)
- Must be added modularly without breaking core logic

## 5. Known Issues / Deferred Tasks
- Automatic LED reset when DAW is closed (non-critical)
- Song name from Fender Studio Show Page is not yet transmitted via MIDI

## 6. Working Rules

1. At every stage, refer to this `PROJECT_CONTEXT.md` file and update it.
2. **Do not modify** stable versions without explicit agreement (`MAX Custom_v1.7.0-2.py`, `MAX Custom_v1.8.0-1.py`, etc.).
3. New features should be added **by extending** the code whenever possible (add functions, avoid large replacements).

