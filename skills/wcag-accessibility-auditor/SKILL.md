---
name: wcag-accessibility-auditor
description: Audits color contrast ratios, typography scale, touch-target dimensions, and screen-reader hierarchy against WCAG 2.1 AA/AAA benchmarks.
---

# WCAG Accessibility Auditor

## Overview
The `wcag-accessibility-auditor` skill verifies interface accessibility against internationally recognized Web Content Accessibility Guidelines (WCAG 2.1). It evaluates text contrast, interactive element sizes, and semantic structure to guarantee universal usability.

## Core Capabilities
- **Relative Luminance Calculation**: Computes exact contrast ratios between foreground text and background surface tokens.
- **WCAG AA / AAA Compliance Verification**: Flags text failing $4.5:1$ (body text) or $3.0:1$ (large display text) contrast baselines.
- **Touch-Target Sizing Check**: Enforces minimum $44 \times 44\text{ pt}$ bounding box requirements for interactive buttons and links.
- **Focus Order & Readability Auditing**: Evaluates optical weight and typography scales to prevent eye fatigue.

## Inputs
- `foreground_color_hex`: Hex color of text or icon.
- `background_color_hex`: Hex color of underlying background surface.
- `font_size_pt`: Typography size in points.
- `touch_target_dimensions`: Width and height of interactive element.

## Outputs
- `contrast_ratio`: Exact calculated ratio ($1.0 - 21.0$).
- `wcag_aa_compliant`: Boolean flag for AA compliance.
- `wcag_aaa_compliant`: Boolean flag for AAA compliance.
- `touch_target_compliant`: Boolean flag for minimum touch area.
