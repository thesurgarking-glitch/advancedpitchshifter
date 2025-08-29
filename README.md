# Advanced Pitch Shifter (JUCE, low CPU)

A lightweight granular **pitch shifter** (±12 semitones + cents) built with **JUCE** and **CMake**. No external deps. CI builds for macOS (VST3 + AU) via GitHub Actions.

## Features
- Low-CPU dual-head granular engine with Hann windowing
- Controls: Semitones, Cents, Window (ms), Crossfade (ms), Quality (Low/Med/High), Mix
- Latency auto-compensated (~0.5×Window)

## Quick Start (Local)
```bash
git clone https://github.com/<you>/AdvancedPitchShifter.git
cd AdvancedPitchShifter
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release --parallel
```
Artifacts appear in `build/` and are also auto-uploaded by CI.

## License
MIT
