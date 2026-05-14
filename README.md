# NTI-AD AI

> Real-time transparency & persuasion analysis system for digital advertising

NTI-AD AI is a conceptual AI-assisted transparency framework that surfaces the persuasion mechanisms, emotional manipulation tactics, and cognitive suppression strategies embedded in digital advertising — before users act on them.

**[→ Live Demo & Calculator](https://YOUR-USERNAME.github.io/nti-ad-ai)**

---

## The Core Idea

Rather than blocking advertisements, the system **translates** them. Real-time overlays quantify how an advertisement is influencing the viewer and — critically — how effectively it suppresses the viewer's capacity to recognize that influence.

Most ad transparency research asks only *whether* manipulation is present. This project also asks *how effectively* that manipulation bypasses rational processing. An advertisement's danger is not just a function of how deceptive it is, but of how cognitively and emotionally compromised the viewer is at the moment of exposure.

---

## The PAVE-C Framework

Five independently scored dimensions capture every major mechanism of advertising influence:

| Dimension | Symbol | Description |
|---|---|---|
| Persuasion Intensity | `PI` | Compounding strength of urgency, scarcity, authority, social proof, FOMO |
| Emotional Arousal Index | `EAI` | Degree to which emotional states bypass rational thinking |
| Cognitive Load Factor | `CLF` | Processing bandwidth consumed by the ad *(new dimension)* |
| Verifiability Index | `VI` | Checkability and plausibility of claims, weighted by specificity |
| Authenticity Score | `AS` | Behavioral + visual geometry consistency |

### Persuasion Intensity — Compounding Formula

The naive approach sums weighted scores linearly. This is wrong: persuasion techniques compound, not add. The corrected formula borrows from reliability theory:

```
PI = 1 − ∏ᵢ (1 − wᵢ · pᵢ)
```

| Scenario | Computation | PI |
|---|---|---|
| Single technique (w = 0.5) | 1 − 0.5 | 0.50 |
| Two techniques (0.4 and 0.3) | 1 − (0.6 × 0.7) | **0.58** |
| Five moderate techniques (0.3 each) | 1 − 0.7⁵ | **0.83** |

Naturally bounded to [0, 1] without clamping.

---

## The Transparency Formula

Three layers combine into a unified score:

**Step 1 — Cognitive Bypass Factor**
```
CBF = (EAI + CLF) / 2
```
How suppressed is the viewer's rational processing?

**Step 2 — Deception Risk Score**
```
DRS = 0.40·PI + 0.35·(1−VI) + 0.25·(1−AS)
```
How inherently deceptive is the content, independent of viewer state?

**Step 3 — Transparency Score**
```
TS = (1 − DRS) × (1 − CBF) × 100        TS ∈ [0, 100]
```

The **multiplicative structure** is the critical design choice. If DRS = 0.7 and CBF = 0.8, then TS = 0.3 × 0.2 × 100 = **6**, not 10. Cognitive suppression *amplifies* the effect of deception — it does not simply add to it.

### Temporal Urgency Extension

```
PI_effective = PI × [1 + τ · (1 − t_first / T)]
```

Where `t_first` = timestamp of first persuasion trigger, `T` = total ad duration, `τ ∈ [0, 0.5]`. Urgency appearing in the first 2 seconds of a 30-second ad amplifies PI by up to 1.47×.

---

## Representative Scores

| Ad Type | DRS | CBF | TS |
|---|---|---|---|
| Aggressive flash sale ("Only 2 left — 73% off — ends in 4:32") | 0.76 | 0.73 | ≈ **7** |
| Typical influencer product placement | 0.60 | 0.50 | ≈ **20** |
| Pharmaceutical ad (fear-based, small-print heavy) | 0.62 | 0.70 | ≈ **11** |
| Disclosure-compliant educational content | 0.18 | 0.24 | ≈ **61** |

---

## System Architecture

```
Ad Input (Text / Audio / Video)
         ↓
  Multimodal Processing
  (NLP · Computer Vision · Audio Analysis)
         ↓
  ┌────────────────────────────────────────┐
  │  PI  — Persuasion Intensity Layer      │
  │  EAI — Emotional Arousal Layer         │
  │  CLF — Cognitive Load Layer            │
  │  VI  — Verifiability Layer             │
  │  AS  — Authenticity Layer              │
  └────────────────────────────────────────┘
         ↓
  CBF Computation → DRS Computation
         ↓
  TS = (1 − DRS) × (1 − CBF) × 100
         ↓
  Real-Time Transparency Overlay
```

---

## Implementation Roadmap

### Phase 1 — Text Analysis Core
- NLP-based persuasion technique classification (PI layer with compounding formula)
- Claim extraction and plausibility scoring (VI layer with specificity weighting)
- Basic behavioral landmark analysis
- Browser extension with real-time text overlays

### Phase 2 — Multimodal Expansion
- Video and audio processing pipeline
- Behavioral landmark detection (GSS and BUS computation)
- Visual geometry estimation module (scale and proportion analysis)
- Temporal urgency weighting integration
- Full PAVE-C Transparency Score computation

### Phase 3 — Interface & Distribution
- Adaptive real-time overlay system (mobile and desktop)
- Interactive transparency dashboards with plain-language explanations
- User-configurable sensitivity thresholds
- Educational mode for media literacy training contexts
- Open API for research and third-party integration

---

## Acknowledged Limitations

- **Contextual ambiguity** — persuasion techniques are not inherently deceptive. The system estimates probability, not intent.
- **Training data dependence** — PI classification requires labeled advertisement datasets. Novel techniques will initially evade detection.
- **Synthetic media trajectory** — behavioral authenticity signals (GSS, BUS) require continuous recalibration as deepfake quality improves.
- **Visual estimation uncertainty** — geometric estimation requires reference objects with known dimensions present in frame.

The system presents scores as *plausibility estimates*, not ground truth judgments.

---

## Running Locally

```bash
git clone https://github.com/YOUR-USERNAME/nti-ad-ai
cd nti-ad-ai
# open index.html in your browser — no build step required
open index.html
```

### Deploy to GitHub Pages

1. Go to repository **Settings → Pages**
2. Set source to **Deploy from a branch**
3. Select branch `main` and folder `/root`
4. Save — site live at `https://YOUR-USERNAME.github.io/nti-ad-ai`

---

## Project Structure

```
nti-ad-ai/
├── index.html          # Website + interactive calculator
├── NTI-AD_AI_Portfolio.md  # Full technical writeup
└── README.md           # This file
```

---

## Author

**S R Tulasi Krishna** — Independent Researcher, Hospet, India

Research interest: Building systems that make hidden computational mechanisms visible to the people they affect. Related projects include physics simulation education platforms, differential equation-based global currency models, and game simulation engines.

---

## License

MIT — see [LICENSE](LICENSE) for details.

---

> *"Influence becomes more responsible when the mechanisms behind it are visible."*
