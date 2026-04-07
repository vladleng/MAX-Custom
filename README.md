# MAX-Custom
# MIDI Captain MAX Custom Firmware

**Enhanced bidirectional MIDI firmware for Paint Audio MIDI Captain MAX (and other variants)**

This is a custom, community-driven firmware based on the official MIDI Captain MAX by Max Cascone. It adds powerful new modes while keeping full compatibility with the original behavior.

---

## ✨ Features

- **Fully config-driven** via `config.json` — no code changes needed for most customizations
- **Bidirectional MIDI** — host (DAW/software) can control LEDs and display in real time
- **Multiple button modes**:
  - `toggle` (default)
  - `momentary`
  - `one_shot` — sends value only on press (no release message)
  - `select` (radio group) — **only for PC buttons** (`type: "pc"`). One button stays lit, others in group turn off
- Support for **PC**, **CC**, **Note**, **PC Inc/Dec**
- **Keytimes** support — multi-state buttons with different colors/labels per state
- **Encoder** with optional stepped mode and push button
- **Expression pedals** with auto-calibration and hysteresis
- **Multi-device support**: STD10, Mini6, Nano4, Duo2, One1 (auto-detection)
- Beautiful color TFT display with customizable fonts and layout
- 5-pin DIN MIDI + USB MIDI with transparent thru
- NeoPixel LED control with dim/off modes

### New in this Custom Fork

- **one_shot** mode (universal for any button)
- **select** radio mode for Program Change buttons
- Modular architecture — easy to add new modes (e.g. upcoming `long_shot`)
- Clean separation of core logic and custom extensions

---

## 📁 Project Structure

- `MAX Custom_v1.8.0-1.py` — **current stable custom firmware**
- `MAX_v1.8.0.py` — clean official base version
- `PROJECT_CONTEXT.md` — detailed project roadmap and rules
- `config02.json` — example configuration
- `core/` — reusable modules (colors, config, button logic)
- `devices/` — hardware definitions for different MIDI Captain models

---

## 🚀 Getting Started

1. Download the latest `MAX Custom_v1.8.0-1.py`
2. Put it on your MIDI Captain in USB drive mode (hold button 1 while powering on)
3. Edit `config.json` to match your needs
4. Reboot the device

See `PROJECT_CONTEXT.md` for full development history and contribution guidelines.

---

## Supported Devices

- **MIDI Captain STD10** (10 switches + encoder + 2 expression)
- **Mini6**, **Nano4**, **Duo2**, **One1**

Automatic hardware detection included.

---

## Configuration Example

```json
{
  "buttons": [
    {
      "label": "Play",
      "type": "note",
      "mode": "toggle",
      "note": 94,
      "color": "green"
    },
    {
      "label": "Var 1",
      "type": "pc",
      "mode": "select",
      "program": 0,
      "color": "orange"
    },
    {
      "label": "Reset",
      "mode": "one_shot",
      "cc": 117,
      "color": "magenta"
    }
  ]
}
