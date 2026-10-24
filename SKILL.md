---
name: projected-singing-speech
description: Generates exhaustive Projected vs Speech reports modeling the acoustic, aerodynamic, and resonant transformations between conversational speech, projected public oratory, and singing/chanting (vibrato rate, singer's formant cluster, subglottal pressure scaling). Trigger with 'projected vs speech for', 'singing voice profile of', 'model vocal projection for', or '/projected-singing-speech'.
disable-model-invocation: true
---

# Projected Versus Speech (Singing / Oratory)

## Purpose & Scope

This skill documents and models the **acoustic and physiological transformations that occur when a speaker transitions from conversational speech into high-projection oratory or singing**. High-volume projection and singing are not simply "louder speech"—they involve radical physiological recalibration: dramatic increases in subglottal pressure ($P_{	ext{sub}}$), expansion of the pharyngeal resonator, elevation or stabilization of the larynx, emergence of the **Singer's/Speaker's Formant Cluster (2.8–3.5 kHz)**, vowel modification at register transitions, and sinusoidal pitch vibrato.

This skill owns:
- Conversational vs. Projected vs. Singing acoustic comparison matrix
- Subglottal pressure ($P_{	ext{sub}}$ in $	ext{cm H}_2	ext{O}$) scaling and glottal efficiency
- Speaker's/Singer's Formant Cluster energy boost in the 2.8–3.5 kHz zone (dB)
- Vibrato dynamics: rate (Hz), extent ($\pm	ext{semitones}$), and onset delay (ms)
- Vowel modification (covering / passagio) adjustments at higher pitch targets
- Phonation mode transitions (chest/modal $	o$ mixed $	o$ falsetto/head voice)

This skill does **not** model conversational baseline prosody (owned by `prosodic-grammar-intonation-os`).

---

## Activation Triggers

Activate automatically when:
- User asks how a speaker sounds when shouting, singing, or projecting in an arena (e.g., *"how does [speaker] sing or chant?"*, *"projected vs conversational profile for [subject]"*).
- User triggers `/projected-singing-speech [subject]`.
- Synthesizing vocal performance, theatrical monologues, chants, or musical vocal tracks.
- Modeling stage oratory in acoustic spaces where projection mechanisms dominate.

---

## Mandatory Report Schema & Structure

### 1. Operational Mode Taxonomy
- **Conversational Baseline (60–68 dBA at 1m):** Standard vocal effort, modal phonation, relaxed vocal tract.
- **Projected Oratory (75–88 dBA at 1m):** Sustained high-volume declamation, expanded pharynx, heightened respiratory drive.
- **Sustained Phonation / Singing (80–95+ dBA):** Pitch-locked melodious phonation, vibrato integration, formal register navigation.

### 2. Aerodynamic & Source Recalibration
- **Subglottal Pressure ($P_{	ext{sub}}$):** Baseline ($5	ext{--}8	ext{ cm H}_2	ext{O}$) scaling up to $15	ext{--}30+	ext{ cm H}_2	ext{O}$ in projected/singing modes.
- **Glottal Closed Quotient (CQ):** Rise from 0.50 modal baseline to 0.65–0.75 in projected speech.
- **Glottal Flow Pulse Derivative ($	ext{d}U/	ext{d}t$):** Maximum flow declination rate (MFDR) increase producing punchy acoustic attacks.

### 3. Speaker's / Singer's Formant Cluster (2.8–3.5 kHz)
- **Spectral Energy Boost:** Magnitude of spectral clustering between F3, F4, and F5 (dB gain above baseline).
- **Anatomical Mechanism:** Epilaryngeal constriction combined with expanded lower pharyngeal volume (1:6 area ratio).
- **Auditory Saliency:** Ability to cut through ambient crowd noise or musical accompaniment.

### 4. Vibrato Mechanics (Singing & Sustained Notes)
- **Vibrato Rate:** Modulation frequency in cycles per second (typically 4.8–6.5 Hz).
- **Vibrato Extent:** Pitch excursion depth in semitones ($\pm 0.3	ext{ to }\pm 1.2	ext{ st}$).
- **Vibrato Onset Latency:** Delay from note initiation to vibrato bloom (ms).

### 5. Vowel Modification & Passaggio Realization
- **Vowel Modification Rules:** Lowering and backing adjustments on high pitches to maintain acoustic impedance matching (e.g., /i/ $	o$ [ɪ], /æ/ $	o$ [ɑ]).
- **Register Transition Points:** Break frequency (Hz) where transition from chest to head/falsetto occurs.

---

## Machine Output Block

```json
{
  "$schema": "https://json-schemas.voice/projected-singing.v1.json",
  "speaker_id": "SPEAKER_ID",
  "projection_matrix": {
    "conversational": {
      "spl_dba": 66.0,
      "psub_cm_h2o": 6.5,
      "speakers_formant_boost_db": 0.0,
      "closed_quotient": 0.52
    },
    "projected_oratory": {
      "spl_dba": 82.5,
      "psub_cm_h2o": 18.0,
      "speakers_formant_boost_db": 7.8,
      "closed_quotient": 0.68,
      "laryngeal_height_mm": 2.5
    },
    "singing_performance": {
      "spl_dba": 88.0,
      "psub_cm_h2o": 24.0,
      "speakers_formant_boost_db": 11.5,
      "closed_quotient": 0.72,
      "vibrato": {
        "active": true,
        "rate_hz": 5.4,
        "extent_semitones": 0.65,
        "onset_latency_ms": 320
      }
    }
  },
  "passaggio_thresholds_hz": {
    "primo_passaggio": 196,
    "secondo_passaggio": 294,
    "falsetto_break": 370
  }
}
```

---

## Biometric & Personality Crosswalk

| Projection Parameter | Core Biometric Section | Personality Profile Section | Synthesis Compiler Target |
| :--- | :--- | :--- | :--- |
| Speaker's Formant Boost | §3 LTAS & Spectral Peaks | §1 Executive Summary | Formant Filter Gain (F3/F4) |
| $P_{	ext{sub}}$ Scaling | §7 Respiratory Support & Pressure | §2.3 Enthusiasm & Positivity | Overall RMS Amplitude Scalar |
| Vibrato Rate & Depth | §1 F0 Stability & Variation | §6 Narrative & Storytelling | LFO Pitch Modulator |
| Vowel Modification | §6 Vowel Features & Shifts | §4.2 Emotional Expression | High-Pitch Formant Re-mapping |

---

## Calibration Reference Example: Queens Orator Projected Arena State

- **Speaker's Formant Peak:** In large arena settings, a strong spectral resonance cluster emerges between 2.9 and 3.4 kHz (+8.2 dB boost), allowing high intelligibility over cheering crowds.
- **Subglottal Loading:** Aerodynamic pressure escalates to estimated $19	ext{--}22	ext{ cm H}_2	ext{O}$, forcing vocal fold closed quotient to 0.70 with prominent pressed gruffness.
- **Chanting / Rhythmic Declination:** Periodic 3-note repetitive cadence with flat level pitch plateaus; zero musical vibrato (vibrato suppressed in favor of raw declamatory impact).

---

## Generation Rules

1. Define projection modes using explicit sound pressure level (dBA) and subglottal pressure estimates ($	ext{cm H}_2	ext{O}$).
2. Specify exact frequency and gain of the speaker's/singer's formant cluster.
3. Every profile must output the machine-readable `projection_singing_profile.json` block.
