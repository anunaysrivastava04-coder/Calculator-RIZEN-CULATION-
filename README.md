# RIZEN-CULATION

A browser-based scientific calculator with a hardware-inspired interface and a mathematics workbench featuring editable 2×2 and 3×3 matrices.

## Overview

RIZEN-CULATION is built as a single-page HTML application. The interface uses a dark theme, an LCD-style result screen, calculator buttons, and a separate workbench view.

## Features

- Basic arithmetic and selected scientific expressions
- Trigonometric functions with angle-mode controls
- Powers, square roots, logarithms, factorial helper, and previous-answer value
- Alternate result displays: fraction approximation, DMS, scientific notation, HEX, and BIN
- Matrix A, B, and C editors for 2×2 and 3×3 matrices
- Matrix addition, subtraction, multiplication, and determinant actions in the visible workstation
- Matrix helper functions for transpose, identity, adjugate, and inverse
- Calculation history navigation
- Optional synthesized button-click sound
- Responsive layout using Tailwind CSS utilities

> **Implementation status:** The interface lists 15 math suites, but the supplied source currently renders a generic status panel for most suites. Some keypad tokens, including integral and constants-related tokens, are not fully implemented by the basic parser. Check `FEATURES.md` for details.

## Getting started

1. Download or clone this repository.
2. Open `rizen_culation_scientific_calculator.html` in a modern browser.
3. Use the calculator keypad or switch to **15 Math Suites & Matrix Hub** to access the matrix workstation.

An internet connection is required for Tailwind CSS styling to load from its CDN. No package installation or build command is shown in the supplied source.

## Technology stack

- HTML5
- CSS3
- JavaScript (vanilla)
- Tailwind CSS via CDN
- Browser Web Audio API for click sound

## Safety note

The current expression evaluator uses JavaScript's `Function()` constructor after transforming the input expression. For a public-facing application, replace this with a restricted math-expression parser and validate every supported token.

## Repository files

- `brain.md` — project context, architecture, implementation notes, and roadmap
- `DESCRIPTION.md` — short project description
- `USES.md` — intended use cases
- `FEATURES.md` — feature inventory and code examples
- `LANGUAGES.md` — programming languages used
- `LIBRARIES.md` — libraries and browser APIs

## License

No license was specified in the supplied source. Add a license file before publishing if you want to define reuse and distribution terms.
