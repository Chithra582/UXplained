---
name: ux-laws-evaluator
description: Audits digital interface layouts against canonical UI/UX laws including Hick's Law, Fitts's Law, Gestalt principles, and Jakob's Law.
---

# UX Laws Evaluator

## Overview
The `ux-laws-evaluator` skill conducts structured cognitive and psychological audits on digital user interfaces. It benchmarks screens against classic interaction design principles to identify cognitive friction and navigation bottlenecks.

## Core Capabilities
- **Gestalt Principles Auditing**: Analyzes visual groupings against Law of Proximity, Law of Similarity, and Law of Common Region.
- **Mental Model Alignment**: Compares interface conventions against Jakob's Law to ensure familiar navigation mechanics.
- **Cognitive Overload Detection**: Applies Miller's Law to verify navigation menus and form inputs do not exceed human short-term memory capacity ($7 \pm 2$ chunks).
- **Aesthetic-Usability Verification**: Balances visual polish with practical affordance and usability heuristics.

## Inputs
- `layout_elements`: Array of visual components with positions, labels, and roles.
- `target_law`: Specific UX law to benchmark (or `all` for comprehensive audit).
- `platform`: Target viewport (`mobile_ios`, `mobile_android`, `desktop_web`).

## Outputs
- `evaluations`: Array of law-specific findings with severity ratings.
- `heuristics_score`: Composite usability score ($0 - 100$).
- `actionable_recommendations`: Step-by-step layout modifications.
