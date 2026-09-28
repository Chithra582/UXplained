---
name: fitts-hicks-calculator
description: Calculates empirical decision times using Hick's Law and target acquisition difficulty indices using Fitts's Law.
---

# Fitts & Hicks Calculator

## Overview
The `fitts-hicks-calculator` skill performs mathematically rigorous ergonomic and cognitive latency calculations on interface elements. It provides empirical proof of interaction efficiency for buttons, links, and navigation menus.

## Core Capabilities
- **Hick's Decision Time Computation**: Evaluates stimulus choices $n$ and calculates projected cognitive reaction latency:
  $$T = b \cdot \log_2(n + 1)$$
- **Fitts's Index of Difficulty (ID)**: Quantifies target acquisition difficulty using target distance $D$ and width $W$:
  $$ID = \log_2\left(\frac{2D}{W}\right)$$
- **Thumb Zone Ergonomic Mapping**: Evaluates reachability zones (Natural, Stretch, Hard) on modern mobile viewports.
- **Micro-Target Warning**: Flags clickable elements smaller than minimum ergonomic thresholds.

## Inputs
- `choice_count`: Number of competing decision options on the active screen.
- `target_distance_px`: Distance from thumb/cursor origin to target center.
- `target_width_px`: Width or diameter of the interactive element.

## Outputs
- `hicks_decision_time_seconds`: Projected cognitive latency in seconds.
- `fitts_index_of_difficulty`: Numerical index of difficulty (bits).
- `ergonomic_verdict`: Rating (`optimal`, `acceptable`, `high_friction`).
