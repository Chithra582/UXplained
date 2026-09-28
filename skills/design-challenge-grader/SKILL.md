---
name: design-challenge-grader
description: Grades student design challenge submissions against rubrics, awarding points and generating constructive 3-tier pedagogical feedback.
---

# Design Challenge Grader

## Overview
The `design-challenge-grader` skill evaluates learner submissions to UXplained GitHub issues. It applies multi-dimensional grading rubrics, calculates gamified challenge points, and generates structured, empathetic pedagogical feedback.

## Core Capabilities
- **Multi-Dimensional Rubric Evaluation**: Grades across Usability (30%), Accessibility (25%), Visual Hierarchy (25%), and Conceptual Rigor (20%).
- **Constructive 3-Tier Feedback Synthesis**:
  1. *What Works Well*: Positive reinforcement of effective design choices.
  2. *Critical Usability Gaps*: Concrete identification of cognitive friction points.
  3. *Actionable Next Steps*: Specific recommendations for portfolio refinement.
- **Gamified Progress Tracking**: Awards points, updates mastery badges, and records learning milestones.
- **Portfolio Case Study Generation**: Compiles polished case study summaries suitable for Behance and design resumes.

## Inputs
- `challenge_id`: GitHub issue or exercise identifier.
- `submission_data`: Design artifact metadata, rationale text, and layout tokens.
- `difficulty_tier`: Level (`beginner`, `intermediate`, `advanced`).

## Outputs
- `total_score`: Composite numerical score ($0 - 100$).
- `points_awarded`: Gamified points assigned to the learner.
- `feedback_markdown`: Formatted critique ready for GitHub issue comments.
