# Projected Versus Speech (Singing / Oratory)

> **Tri-Platform Agent Skill** for Claude Desktop / Code, Grok CLI, and Google Antigravity / Gemini.  
> Singing-to-Speech Formant and Dynamic Mapping — Models the acoustic, aerodynamic, and resonant transformations between conversational speech, projected public oratory, and singing/chanting.

---

## Overview

`projected-singing-speech` provides standardized capabilities across conversational AI platforms:
- Three-tier vocal mode taxonomy (Conversational Speech, Public Oratory, Singing).
- Singer's Formant cluster (2.8 kHz - 3.2 kHz) spectral resonance modeling.
- Vibrato rate (5-7 Hz) and extent (+/- 50-100 cents) parameterization.
- Subglottal pressure (Ps) and sound pressure level scaling equations.
- Standardized projected_vocal_mode.json schema for synthesis engines.
- Tri-platform NTFS junctions connecting Claude, Grok, and Antigravity.
- Standard documentation suite: SKILL.md, HOW_TO_USE.txt, IMPLEMENTATION_PLAN.md, and README.md.

---

## Tri-Platform Architecture

Zero duplicate code across platforms. Canonical source resides in `.agents`:
- **Canonical Source**: `C:\Users\<you>\.agents\skills\projected-singing-speech`
- **Claude**: `C:\Users\<you>\.claude\skills\projected-singing-speech` (NTFS Junction)
- **Grok**: `C:\Users\<you>\.grok\skills\projected-singing-speech` (NTFS Junction)
- **Antigravity**: `C:\Users\<you>\.gemini\config\skills\projected-singing-speech` (NTFS Junction)

---

## Documentation Suite

- [`HOW_TO_USE.txt`](HOW_TO_USE.txt): Standardized user guide and prompt templates.
- [`IMPLEMENTATION_PLAN.md`](IMPLEMENTATION_PLAN.md): Feature checklist and roadmap.
- [`App Changes Tracker.html`](App%20Changes%20Tracker.html): Interactive visual version log.
- [`SKILL.md`](SKILL.md): Agent system instructions and triggers.
