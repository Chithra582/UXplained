# EXPLAINABILITY.md

This document explains the internal mechanisms, data lineage, operational boundaries, and governance framework of **UXplained Agent** (`uxplained-agent`) in accordance with the **OpenGAP v0.1.0** specification for the **HiDevs GitAgent Passport** clearance pipeline.

> **Agent Name:** UXplained Agent (`uxplained-agent`)  
> **Specification:** OpenGAP v0.1.0  
> **Category / Domain:** Education / UI/UX Design Pedagogy, Usability Auditing & Interaction Heuristics  
> **Compliance Standard:** OpenGAP Checkpoint 2 (Explainability & Decision Governance), FERPA, GDPR  

---

## How the Agent Decides

UXplained Agent is an autonomous UI/UX design heuristics evaluation, cognitive psychology laws auditing, accessibility compliance checking, and interactive design challenge evaluation agent designed for **UXplained**. It evaluates digital interfaces against Hick's Law, Fitts's Law, Gestalt principles, WCAG accessibility benchmarks, and usability heuristics.

### 1. Decision Architecture

The interface ingestion, cognitive law evaluation, accessibility auditing, and feedback generation pipeline operates across a deterministic, five-stage architecture:

```
Learner Submission (Figma Node JSON / Component Screenshot / CSS Mockup + Challenge ID)
    │
    ▼
[Stage 1: Multi-Format Ingestion & Geometry Normalization]
    │  - Ingests visual and structural design artifacts (Figma API JSON, PNG screenshot, or CSS DOM)
    │  - Normalizes component coordinates, typography scales, spacing tokens, and color palettes
    │  - Reconstructs visual hierarchy, scanning flow, and element bounding boxes
    ▼
[Stage 2: Deterministic Ergonomic & Cognitive Auditing]
    │  - Hick's Law: Counts discrete choice options and computes estimated user decision time (T)
    │  - Fitts's Law: Measures target size (W) and distance (D) to calculate Index of Difficulty (ID)
    │  - Gestalt Law of Proximity: Evaluates spacing ratios between related vs. unrelated elements
    │  - Law of Similarity: Checks visual consistency across repeated functional components
    ▼
[Stage 3: WCAG Accessibility & Contrast Auditing]
    │  - Calculates relative luminance and contrast ratios for all foreground/background text pairs
    │  - Enforces WCAG 2.1 AA benchmarks: minimum 4.5:1 for body copy and 3.0:1 for large display text
    │  - Verifies interactive touch-target dimensions meet the minimum 44x44 pt bounding box
    │  - Flags readability risks (e.g., text overlaid on unshaded imagery or low-contrast gradients)
    ▼
[Stage 4: Rubric Scoring & Pedagogical Feedback Formulation]
    │  - Evaluates submission against challenge rubric: Usability (30%), Accessibility (25%), 
    │    Visual Hierarchy (25%), and Conceptual Rigor (20%)
    │  - Generates composite score (0 - 100) and assigns gamified achievement points
    │  - Constructs constructive 3-tier feedback: What Works Well, Critical Usability Gaps, Next Steps
    ▼
[Stage 5: Portfolio Dossier Commit & Mentorship Synthesis]
    │  - Compiles structured Markdown evaluation report with highlighted visual annotations
    │  - Updates learner skill matrix across core UI/UX laws
    │  - Generates shareable case study summaries for student design portfolios
    ▼
Comprehensive Heuristic Critique & Actionable Improvement Roadmap Delivered to Learner
```

### 2. Scoring Methodology & Rubric Formulations

UXplained Agent computes usability and cognitive efficiency metrics through deterministic, mathematically rigorous formulations:

1. **Hick-Hyman Decision Time Formulation ($T_{\text{hick}}$)**:
   $$T_{\text{hick}} = b \cdot \log_2(n + 1)$$
   where:
   - $n$: Number of competing stimulus/choice options presented on the screen.
   - $b$: Empirical processing constant ($b \approx 0.155 \text{ seconds/bit}$).
   - High cognitive load flag: Triggers when $T_{\text{hick}} > 1.2 \text{ seconds}$ in primary navigation or transaction flows.

2. **Fitts's Law Index of Difficulty ($ID$)**:
   $$ID = \log_2\left(\frac{2D}{W}\right)$$
   where:
   - $D$: Distance from initial cursor/thumb resting position to target center.
   - $W$: Width or diameter of the target along the motion axis.
   - Ergonomic reach penalty: Triggered when $ID > 4.5 \text{ bits}$ on mobile primary CTA controls.

3. **WCAG Relative Luminance Contrast Ratio ($C_R$)**:
   $$C_R = \frac{L_1 + 0.05}{L_2 + 0.05}$$
   where $L_1$ is the relative luminance of the lighter color and $L_2$ is the relative luminance of the darker color ($L \in [0, 1]$).
   - Compliance rule: $C_R \ge 4.5$ for standard text, $C_R \ge 3.0$ for large text.

4. **Composite Challenge Score ($S_{\text{challenge}}$)**:
   $$S_{\text{challenge}} = w_u \cdot U_{\text{usability}} + w_a \cdot A_{\text{wcag}} + w_h \cdot H_{\text{hierarchy}} + w_c \cdot C_{\text{concept}}$$
   where weights $w_u = 0.30, w_a = 0.25, w_h = 0.25, w_c = 0.20$ ($\sum w_i = 1.0$).

### 3. Thresholding & Refusal Decision Criteria

UXplained Agent enforces strict pedagogical and safety boundaries:
- **Refusal to Output Demoralizing Critiques**: Reviews lacking constructive improvement paths are deterministically rejected by safety filters under code `ERR_NON_CONSTRUCTIVE_CRITIQUE`.
- **Refusal on Plagiarized Submissions**: Direct uncredited copies of commercial app interfaces without original synthesis trigger code `ERR_PLAGIARISM_UNETHICAL`.
- **Refusal to Pass Inaccessible Interfaces**: Submissions with failing WCAG contrast ratios ($C_R < 3.0$) are denied passing grades under code `ERR_ACCESSIBILITY_BENCHMARK_FAILED`.
- **Refusal of Malicious Injection**: Submissions containing embedded prompt injection vectors in CSS or design annotations are neutralized (`ERR_PROMPT_INJECTION_DEFLECTED`).
- **Refusal of Self-Modification**: The agent is prohibited from autonomously mutating its core evaluation rubrics or guidelines in `agent.yaml` (`ERR_SELF_MODIFICATION_PROHIBITED`).

### 4. Fallback Decision Mechanism

UXplained Agent maintains uninterrupted educational service through a multi-tier fallback architecture:
- **Model Fallback Cascade**: High-level visual critique and holistic design feedback default to `gemini-2.0-flash` with automatic failover to `gpt-4o` and `claude-3-5-sonnet`.
- **Deterministic Color Math Fallback**: If LLM inference is delayed, the agent calculates WCAG contrast and bounding-box ratios purely through deterministic mathematical scripts.
- **Rule-Based Heuristic Template Pack**: When AI generation APIs experience rate limits, the platform delivers curated heuristic checklists and design tips corresponding to the specific UI law.
- **Offline Review Queue**: If third-party design APIs (Figma) experience downtime, submissions are cached locally and processed sequentially upon reconnection.

### 5. Human-in-the-Loop Governance

UXplained Agent upholds student autonomy and educator oversight:
- **Educator Grade Overrides**: Instructors and design mentors retain override capability to adjust scores or review contested critiques.
- **Student Appeal Channel**: Learners can submit one-click requests for human mentor review on any automated evaluation.
- **Administrative Kill-Switch**: Educators can instantly toggle an emergency kill-switch to pause automated challenge evaluation during curriculum updates.
- **Audit Logging**: All challenge submissions, contrast calculations, rubric grades, and feedback logs are preserved in structured JSON audit records.

---

## The Data It Uses

UXplained Agent operates under strict privacy and educational data governance standards.

### 1. Ingested Input Data

The agent processes only user-submitted design artifacts and challenge metadata:
- **Design Files & Images**: Uploaded component mockups (PNG, JPEG), SVG vector trees, and Figma node metadata.
- **Challenge Metadata**: Target UI/UX law ID, challenge prompt number, design tools used, and student notes.
- **Design Tokens**: Extracted color hex values, typography point sizes, line heights, and margin measurements.

### 2. Configuration & Reference Data

- **Canonical UI/UX Law Standards**: Mathematical models for Hick's Law, Fitts's Law, Miller's Law, and Gestalt principles.
- **WCAG 2.1 Specifications**: Authoritative contrast algorithms, font size definitions, and minimum touch target requirements.
- **Curated Educational Rubrics**: Standardized grading matrices mapped across beginner, intermediate, and advanced challenge tiers.

### 3. Base Model & Inference Lineage

- **Deterministic Algorithmic Engines**: Mathematical calculation of relative luminance, Fitts's index, and geometric bounding boxes.
- **Foundation Vision Models**: High-capability vision models (`gemini-2.0-flash`, `gpt-4o`, `claude-3-5-sonnet`) utilized strictly for visual hierarchy analysis and design advice formulation.
- **Zero Training on Student Designs**: Uploaded student portfolio mockups, creative ideas, and submitted code are never utilized to train public foundation models.

### 4. Data Privacy, Storage, and Retention

- **FERPA & GDPR Compliance**: Full compliance with FERPA and GDPR standards. All student submissions and evaluation records are classified as `internal` with encryption at rest and in transit.
- **0-Byte Data Purging**: Students can permanently delete their uploaded mockups and critique histories at any time with verifiable 0-byte database purging.
- **Zero Commercial Monetization**: Student designs and portfolio concepts are never sold, commercialized, or shared with third-party design agencies.

---

## Limitations

Understanding the operational boundaries and technical constraints of UXplained Agent is essential for effective design learning.

### 1. Flat Raster Image Layer Ambiguity
- **Limitation**: When evaluating flat raster screenshots (PNG/JPEG) without underlying vector data, subtle overlapping layers or background blurs can be difficult to segment automatically.
- **Mitigation**: The agent encourages learners to connect Figma node JSON or supply clean SVG assets for the most precise bounding box analysis.

### 2. Subjective Brand Aesthetic & Art Direction Variance
- **Limitation**: Highly stylized, brutalist, or retro-experimental designs may intentionally violate conventional layout conventions for artistic storytelling.
- **Mitigation**: The agent recognizes experimental tags, evaluating artistic submissions on internal visual consistency rather than strict corporate SaaS templates.

### 3. Complex Multi-State Micro-Interaction Fidelity
- **Limitation**: Static screen submissions cannot demonstrate animated transitions, hover state feedback, or micro-interaction velocity.
- **Mitigation**: The platform integrates timeline-based prototype evaluation guides, encouraging learners to submit video screen recordings or Framer prototypes.

### 4. Non-Standard Experimental Design Paradigms
- **Limitation**: Spatial computing (AR/VR) or voice user interface (VUI) concepts operate under different ergonomic laws than 2D mobile/web viewports.
- **Mitigation**: Specialized AR/VR rubric modules adapt Fitts's 2D formulas into 3D angular target acquisition mechanics.

### 5. Multilingual Typographic Rendering Nuances
- **Limitation**: Non-Latin scripts (e.g., Arabic, Devanagari, East Asian ideograms) have distinct vertical rhythm and optical weight characteristics.
- **Mitigation**: The system incorporates script-aware typography baselines when auditing line-height and x-height readability.

---

## Summary & Compliance Checklist

| Checkpoint 2 Requirement | Corresponding Section | Status |
| :--- | :--- | :---: |
| **How the agent decides** | [How the Agent Decides](#how-the-agent-decides) | **Covered** |
| - Decision architecture & 5-stage pipeline | Section 1 | Verified |
| - Scoring methodology & ergonomic formulas | Section 2 | Verified |
| - Thresholding & refusal decision criteria | Section 3 | Verified |
| - Fallback decision mechanism | Section 4 | Verified |
| - Human-in-the-loop governance | Section 5 | Verified |
| **The data it uses** | [The Data It Uses](#the-data-it-uses) | **Covered** |
| - Ingested mockups, components & challenge code | Section 1 | Verified |
| - Configuration, UX law baselines & WCAG schemas | Section 2 | Verified |
| - Base model lineage & deterministic heuristics | Section 3 | Verified |
| - Data privacy, student portfolio safety & FERPA/GDPR | Section 4 | Verified |
| **Its limitations** | [Limitations](#limitations) | **Covered** |
| - Flat raster image layer ambiguity | Section 1 | Verified |
| - Subjective brand aesthetic & art direction variance | Section 2 | Verified |
| - Complex multi-state micro-interaction fidelity | Section 3 | Verified |
| - Non-standard experimental design paradigms | Section 4 | Verified |
| - Multilingual typographic rendering nuances | Section 5 | Verified |
