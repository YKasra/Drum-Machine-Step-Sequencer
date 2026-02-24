# Digital Drum Machine with Step Sequencer — Pure Data

A BPM-driven drum machine built entirely in Pure Data (Pd). Features a 16-step sequencer, dedicated synthesis engines for each drum sound, genre presets, and WAV export. Built as a course project for BA Sound Technology at Azad University of Tehran.

![Drum Machine Patch](https://iili.io/qKgWNkl.md.png)

---

## What It Does

This isn't a sample-playback drum machine — every drum sound is **synthesized from scratch** using Pure Data's audio objects. The step sequencer drives a 16-step pattern at a user-defined BPM, triggering kick, snare, and hi-hat subpatches at precise intervals.

**Core features:**
- 16-step sequencer with visual array display
- BPM control (adjustable tempo)
- Synthesized kick, snare, and hi-hat (no samples — pure DSP)
- Combo step encoding: each step can trigger any combination of K/S/H
- Genre presets (Funky, House, Rock) via preset arrays
- Custom pattern creation
- WAV export of output

---

## Architecture

```
Final Machine (Patch).pd    ← Main patch: sequencer, UI, routing
    ├── Counter.pd           ← BPM-driven step counter (metro + modulo)
    ├── Kick.pd              ← Kick drum synthesis engine
    ├── Snare.pd             ← Snare drum synthesis engine
    └── Hhats.pd             ← Hi-hat synthesis engine
```

**Step encoding system:**
```
0 = kick       1 = snare      2 = hi-hat
3 = kick+snare  4 = kick+hat   5 = snare+hat  6 = all three
```

Each step in the 16-step array holds a value 0–6, determining which combination of drums fires on that beat.

---

## How to Run

1. Install [Pure Data](https://puredata.info/downloads) (Pd Vanilla or Purr Data)
2. Clone this repo:
   ```bash
   git clone https://github.com/YKasra/drum-machine-step-sequencer.git
   cd drum-machine-step-sequencer/patches
   ```
3. Open `Final Machine (Patch).pd` in Pure Data
4. Click the toggle to start the sequencer
5. Adjust BPM, switch presets, or create your own patterns

---

## Files

```
├── patches/
│   ├── Final Machine (Patch).pd   # Main sequencer patch
│   ├── Counter.pd                  # Step counter subpatch
│   ├── Kick.pd                     # Kick synthesis
│   ├── Snare.pd                    # Snare synthesis
│   └── Hhats.pd                    # Hi-hat synthesis
├── documentation.pdf               # Original project documentation
└── README.md
```

---

## Tech Stack

**Pure Data (Pd)** — Visual programming language for audio and multimedia

Key Pd concepts used: `metro`, `array`, `osc~`, `noise~`, `bp~`, `hip~`, `lop~`, `env~`, `vline~`, `dac~`, `writesf~`

---

## Author

**Kasra Yaraei** — BA Sound Technology, Azad University of Tehran

[LinkedIn](https://linkedin.com/in/kasrayaraei) · [GitHub](https://github.com/YKasra)
