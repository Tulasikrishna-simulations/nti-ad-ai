# NTI-AD AI
## Real-Time Transparency & Persuasion Analysis System for Digital Advertising
*A Conceptual AI-Assisted Transparency & Behavioral Verification Framework*
**By: S R Tulasi Krishna**

---

## Overview

NTI-AD AI is a conceptual AI-assisted transparency system designed to surface the mechanisms behind digital advertising — in real time, without blocking a single ad.

Modern advertising systems are engineered for one objective: to convert attention into action before the viewer can critically evaluate what they are seeing. They achieve this through stacked persuasion techniques, emotional state manipulation, high cognitive load environments, and visually fabricated authenticity signals. Each mechanism, individually, is manageable. Together, they create conditions where impulsive reaction replaces reflective decision-making — and users currently have no equivalent counter-system.

NTI-AD AI proposes one.

Rather than filtering content, the system translates it — providing real-time overlays that make persuasion techniques, claim plausibility, and behavioral authenticity signals legible to the viewer. The intervention is minimal and deliberate: not removing influence, but making it visible. That small shift, from passive exposure to informed awareness, is the system's entire purpose.

---

## Core Research Question

> *"How can AI systems help users understand both the persuasive intent and plausibility of digital advertisements in real time — and quantify the degree to which those advertisements suppress the viewer's capacity for critical evaluation?"*

The second clause is intentional. Most ad transparency research asks only whether manipulation is present. This project also asks how effectively that manipulation bypasses rational processing — a fundamentally different and more actionable question. An advertisement's danger is not just a function of how deceptive it is, but of how cognitively and emotionally compromised the viewer is at the moment of exposure.

---

## Personal Motivation

While observing social media, influencer marketing, and modern advertising ecosystems, I noticed something that bothered me: digital platforms are increasingly optimized for impulsive reactions, emotional engagement, urgency-driven behavior, and short attention cycles — especially among younger users. These are not incidental design choices. They are the product of years of behavioral optimization.

At the same time, users lack any equivalent tools. There is no counter-system. No real-time layer that says: *this is what this advertisement is trying to do to you, and here is how effectively it is working.*

This project emerged from a simple belief — that people are more capable of making good decisions when they understand the systems acting on them. NTI-AD AI is an attempt to build that understanding into the advertising environment itself, rather than asking users to develop it independently against increasingly sophisticated systems designed to defeat it.

---

## System Architecture

```
Advertisement Input
(Text / Audio / Video)
         ↓
  Multimodal Processing
         ↓
  ┌──────────────────────────────────────────┐
  │  PI — Persuasion Intensity               │
  │  EAI — Emotional Arousal Index           │
  │  CLF — Cognitive Load Factor             │
  │  VI  — Verifiability Index               │
  │  AS  — Authenticity Score                │
  └──────────────────────────────────────────┘
         ↓
  CBF = (EAI + CLF) / 2
  DRS = 0.40·PI + 0.35·(1−VI) + 0.25·(1−AS)
         ↓
  TS = (1 − DRS) × (1 − CBF) × 100
         ↓
  Real-Time Transparency Overlay
```

---

## The PAVE-C Framework: Five Input Dimensions

The system's analytical core is built around five independently scored dimensions, each mapped to a distinct mechanism of advertising influence. Together they form the PAVE-C model: Persuasion, Authenticity, Verifiability, Emotional Arousal, and Cognitive Load.

---

### 1. Persuasion Intensity (PI)

PI measures the aggregate strength of psychological persuasion techniques present in the advertisement — urgency, artificial scarcity, authority signaling, social proof, FOMO, and reciprocity triggers.

The naive formulation uses a simple weighted sum:

```
S = Σ wᵢ    [original — flawed]
```

This has two critical problems: the sum is unbounded (three techniques at 0.5 each gives 1.5), and it is linear, implying that techniques simply add. In reality, persuasion techniques compound — each additional technique makes the combined effect disproportionately stronger because they attack different psychological defenses simultaneously.

The corrected formulation borrows from reliability theory — specifically, the probability that at least one failure mode activates:

```
PI = 1 − ∏ᵢ (1 − wᵢ · pᵢ)
```

Where:
- `pᵢ` = activation score for persuasion technique i ∈ [0, 1]
- `wᵢ` = learned intensity weight for technique i, trained on labeled advertisement datasets

**Properties of this formulation:**

| Scenario | Computation | PI |
|---|---|---|
| Single technique (w = 0.5) | 1 − 0.5 | 0.50 |
| Two techniques (0.4 and 0.3) | 1 − (0.6 × 0.7) | 0.58 |
| Five moderate techniques (0.3 each) | 1 − 0.7⁵ | 0.83 |

PI ∈ [0, 1] always — bounded naturally, without clamping. The compounding correctly reflects the disproportionate power of stacked techniques.

---

### 2. Emotional Arousal Index (EAI)

EAI measures the degree to which the advertisement triggers emotional states designed to override rational processing.

Target emotional states include:
- **Fear** — health risk messaging, social exclusion, missing out
- **Desire** — aspirational lifestyle, sexual appeal, status signaling
- **Excitement** — sweepstakes, launches, limited releases
- **Guilt** — charity appeals, environmental messaging, parenting anxiety

EAI ∈ [0, 1], scored via multimodal sentiment analysis, facial expression recognition (in video), and emotional trigger classification on text and audio.

---

### 3. Cognitive Load Factor (CLF) *(new dimension)*

CLF measures how much of the viewer's processing bandwidth the advertisement actively consumes — reducing the cognitive resources available for critical evaluation of what they are seeing.

This dimension is absent from prior transparency frameworks. Its inclusion reflects an important finding from cognitive science: people in high cognitive load states are significantly more susceptible to persuasion because deliberate, analytical thinking requires available mental bandwidth, and advertising systems can deliberately deplete that bandwidth.

Contributing factors:
- Information density — simultaneous text, audio, and visual elements
- Edit pacing — cuts per second in video content
- Auditory intensity — volume, music tempo, sound design complexity
- Visual complexity — particle effects, transitions, overlapping elements, split screens

CLF ∈ [0, 1]. A slow, clearly structured informational video scores near 0. A typical fast-cut influencer reel with background music, simultaneous text overlays, and product comparison visuals scores 0.6–0.8.

---

### 4. Verifiability Index (VI)

VI measures the checkability and plausibility of claims made in the advertisement.

```
VI = (1/m) · Σᵢ [ tᵢ · specificity(cᵢ) ]
```

Where:
- `tᵢ ∈ [0, 1]` = estimated plausibility score for claim i
- `specificity(cᵢ)` = weight reflecting how falsifiable the claim is

**Why specificity matters:** *"Results in 7 days"* is a falsifiable prediction — either it produces results in 7 days or it does not. *"This changed my life"* is unfalsifiable opinion. The system weights specific, quantitative claims more heavily because they are the ones that can actually mislead through false precision. Vague claims are less dangerous precisely because they cannot be taken literally.

Example claim assessments:

| Claim | Specificity | Plausibility | VI contribution |
|---|---|---|---|
| "Only 3 items left" | High | Often false (artificial scarcity) | Low |
| "100% authentic" | Medium | Unverifiable | Low-Medium |
| "Clinically tested" | Medium | Technically true but misleading | Medium |
| "Ships in 24 hours" | High | Often accurate | High |

---

### 5. Authenticity Score (AS)

AS integrates the system's two visual and behavioral analysis sub-layers.

**Visual Geometry Layer**

Objects within the frame are identified, perspective and viewing angle are estimated, and relative scale is compared against known reference models. This allows the system to detect inconsistencies between presented visual claims and geometric reality — influencer height exaggeration, artificially scaled product demonstrations, or impossible spatial relationships.

The relative estimation relationship:

```
H_est = (P_obj / P_ref) × H_ref
```

Where `H_est` is the estimated height of the detected object, `P_obj` and `P_ref` are the pixel scales of the detected object and a known reference object, and `H_ref` is the real-world size of the reference. Significant divergence between `H_est` and expected real-world values flags a potential geometric inconsistency.

**Behavioral Authenticity Layer**

Natural human behavior is characterized by controlled entropy — neither perfectly regular nor randomly erratic. The system models two complementary signals:

*Geometric Stability Score (GSS):*

```
GSS = Var(θ(t))
```

Where `θ(t)` represents movement angles over time. Extremely low variance indicates artificial motion — AI-generated presenters or heavily post-processed video — while natural variance indicates human-like motion.

*Behavioral Uncertainty Score (BUS):*

```
BUS = −Σ p(x) log p(x)
```

Where `p(x)` is the probability distribution over behavioral states (blinking timing, expression transitions, micro-movements). Low entropy indicates artificial regularity; natural human behavior has predictable variability in its unpredictability.

The combined Authenticity Score:

```
AS = f(GSS, BUS, geometric_consistency)
```

AS ∈ [0, 1], where higher values indicate more authentic behavioral and visual signals.

---

## The PAVE-C Transparency Formula

The five dimensions combine into a unified Transparency Score through two intermediate computations.

### Intermediate 1: Cognitive Bypass Factor (CBF)

```
CBF = (EAI + CLF) / 2
```

CBF captures the degree to which the viewer's rational processing is suppressed at the moment they encounter the advertisement's persuasion content. High emotional arousal and high cognitive load together create a state where even detectable manipulation passes without conscious recognition. This is the mechanism that advertising systems most aggressively optimize for — not just making the manipulation stronger, but degrading the viewer's ability to detect it.

### Intermediate 2: Deception Risk Score (DRS)

```
DRS = 0.40 · PI + 0.35 · (1 − VI) + 0.25 · (1 − AS)
```

DRS measures how inherently deceptive the advertisement content is, independent of the viewer's mental state. The weights reflect the relative contribution of each dimension — persuasion intensity is the dominant factor (0.40), followed by unverifiable claims (0.35), and fabricated authenticity (0.25). These weights are initial estimates and are designed to be learned from labeled evaluation data over time.

DRS ∈ [0, 1].

### Final: Transparency Score (TS)

```
TS = (1 − DRS) × (1 − CBF) × 100
```

TS ∈ [0, 100].

**The multiplicative structure is the critical design choice.** A linear combination would imply that emotional suppression and content deception independently add to the transparency deficit. The multiplicative model correctly captures that cognitive bypass *amplifies* the effect of deception — a highly manipulative advertisement is significantly more dangerous encountered in a high cognitive load, high emotional arousal environment than the same advertisement encountered when the viewer is calm and focused.

**Representative scores:**

| Ad Type | DRS | CBF | TS |
|---|---|---|---|
| Aggressive flash sale ("Only 2 left — 73% off — ends in 4:32") | 0.76 | 0.73 | ≈ 7 |
| Typical influencer product placement | 0.60 | 0.50 | ≈ 20 |
| Pharmaceutical ad (fear-based, small-print heavy) | 0.62 | 0.70 | ≈ 11 |
| Disclosure-compliant educational content | 0.18 | 0.24 | ≈ 61 |

---

## Temporal Urgency Weighting (Extension)

Standard persuasion scoring treats all temporal positions within an advertisement equally. This is incorrect.

Persuasion techniques that appear before the viewer has formed any critical evaluative stance are significantly more effective than those appearing later, when the viewer has had time to orient themselves to the content. Early urgency framing anchors the viewer's interpretation of everything that follows. Late urgency, arriving after the viewer has processed the content, has less impact on immediate decision-making.

The temporal correction factor adjusts PI based on when the first high-intensity persuasion trigger is detected:

```
PI_effective = PI × [ 1 + τ · (1 − t_first / T) ]
```

Where:
- `t_first` = timestamp of first detected high-intensity persuasion trigger
- `T` = total advertisement duration  
- `τ ∈ [0, 0.5]` = tunable temporal sensitivity parameter

**Effect:** A countdown timer appearing in the first 2 seconds of a 30-second advertisement (`t_first/T ≈ 0.07`) amplifies PI by up to 1.47×. The same timer appearing at second 28 (`t_first/T ≈ 0.93`) produces almost no amplification. This reflects the established psychological finding that initial framing has outsized influence on subsequent information processing — a principle advertising systems already exploit and which transparency frameworks must account for.

---

## Educational & Social Focus

NTI-AD AI is designed as augmentation, not restriction. The system does not:

- Block or filter advertisement content
- Make purchasing or behavioral decisions for users
- Claim definitive truth detection capability
- Assign blame or intent to advertisers

The system does:

- Surface persuasion mechanisms operating beneath conscious awareness
- Quantify how effectively those mechanisms are bypassing critical evaluation
- Present findings in accessible, plain-language overlays
- Create a deliberate pause between exposure and reaction

That pause is the minimal viable intervention. The decision still belongs entirely to the user. NTI-AD AI only ensures they are making it with more information than the advertising system intended them to have.

---

## Acknowledged Limitations

**Contextual ambiguity.** Persuasion techniques are not inherently deceptive. An enthusiastic genuine recommendation uses the same signals as coordinated astroturfing. The system estimates probability of manipulation, not intent. All scores are presented as plausibility estimates with associated confidence intervals.

**Training data dependence.** PI classification accuracy depends on the quality and breadth of labeled advertisement datasets. Novel manipulation techniques will initially evade detection until sufficient examples are incorporated into the training corpus.

**Synthetic media trajectory.** Behavioral authenticity signals (GSS, BUS) are calibrated against current deepfake generation quality. As synthetic media becomes more sophisticated, detection thresholds will require continuous recalibration — an ongoing adversarial dynamic rather than a solvable problem.

**Visual estimation uncertainty.** Geometric scale estimation requires reference objects with known real-world dimensions present in frame. Cropped, abstract, or digitally composited compositions reduce estimation reliability.

The system is therefore a transparency *assistant*, not a truth arbiter.

---

## Implementation Roadmap

**Phase 1 — Text Analysis Core**
- NLP-based persuasion technique classification (PI layer with compounding formula)
- Claim extraction and plausibility scoring (VI layer with specificity weighting)
- Basic behavioral landmark analysis
- Browser extension delivering real-time text overlay explanations

**Phase 2 — Multimodal Expansion**
- Video and audio processing pipeline
- Behavioral landmark detection (GSS and BUS computation)
- Visual geometry estimation module (scale and proportion analysis)
- Temporal urgency weighting integration
- Full PAVE-C Transparency Score computation and overlay rendering

**Phase 3 — Interface & Distribution**
- Adaptive real-time overlay system for mobile and desktop
- Interactive transparency dashboards with plain-language explanations
- User-configurable sensitivity thresholds
- Educational mode for media literacy training contexts
- API for third-party integration and research access

---

## Connection to My Broader Interests

NTI-AD AI reflects a question I return to across all my technical work: what happens when complex systems operate on people, and those people have no tools to interpret what the system is doing to them?

This project approaches that question in the context of advertising. Other projects approach it through physics simulation (making hidden physical relationships directly visible through interactive environments), economic modeling (making emergent macroeconomic dynamics interpretable through differential equation-based visualization), and game engine design (making rule systems inspectable through real-time simulation tools). The surface domains differ. The underlying design conviction is the same.

People understand systems more effectively when they can see them operating — and they make better decisions in those systems when that visibility is available to them.

---

## Final Thought

> *"Influence becomes more responsible when the mechanisms behind it are visible."*
