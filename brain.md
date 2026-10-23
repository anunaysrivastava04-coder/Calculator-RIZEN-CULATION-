# RIZEN-CULATION — Project Brain

## Project identity
- **Name:** RIZEN-CULATION
- **Type:** Browser-based scientific calculator and mathematics workbench
- **Primary entry point:** `rizen_culation_scientific_calculator.html`
- **Architecture:** Single-page HTML application with embedded CSS and JavaScript
- **Runtime:** Modern web browser; no build step is shown in the supplied source

## Purpose
RIZEN-CULATION provides a calculator-style interface for scientific expressions and a separate workbench interface for matrix operations. It aims to combine a hardware-calculator-inspired experience with a dark, responsive UI.

## Main areas
1. **Hardware Calculator** — keypad, LCD-style expression/result display, angle-mode indicator, answer/memory state, calculation history navigation, and alternate result formats.
2. **Math Suites & Matrix Hub** — 15 named suite tabs and a matrix workstation. In the supplied code, the matrix suite has concrete matrix UI and operations; the other suite tabs display placeholder/status content rather than fully implemented suite-specific tools.
3. **Feedback controls** — sound toggle and a short synthesized click sound using the Web Audio API.

## Implemented capabilities visible in source
- Basic arithmetic expression evaluation
- Trigonometric functions (`sin`, `cos`, `tan`) with degree-mode conversion; angle-mode state also cycles through radians and gradians
- Square roots, powers, logarithms, factorial helper, and previous-answer substitution
- Approximate fraction, degrees-minutes-seconds, scientific-notation, hexadecimal, and binary display conversions
- Matrix A/B/C editing in 2×2 or 3×3 dimensions
- Matrix addition, subtraction, multiplication, determinant, transpose, identity, adjugate, and inverse helper functions
- Matrix expression handling for determinant, inverse, and binary operations
- Demo-expression buttons and responsive layouts styled with Tailwind CSS utilities

## Important implementation notes
- The app is a single HTML file and loads Tailwind CSS from its CDN.
- JavaScript state is held in in-memory objects; persistent storage is not implemented in the supplied source.
- Some labels advertise more functionality than the visible implementation provides. For example, the 15 math-suite tabs are listed, but most currently render a generic status panel.
- The visible keypad inserts some tokens (such as integrals, constants, and engineering notation) that are not fully handled by the basic expression parser in the supplied code.
- The calculator evaluates parsed expressions using JavaScript's `Function` constructor. Do not expose this to untrusted input in a public or multi-user environment without replacing it with a safe expression parser.
- The supplied source references `setMatrixDimension`, `runMatrixWorkbenchOp`, and other matrix helpers; verify all advertised operations against the actual UI before describing them as fully supported.

## Suggested repository structure
```text
rizen-culation/
├── rizen_culation_scientific_calculator.html
├── README.md
├── brain.md
├── DESCRIPTION.md
├── USES.md
├── FEATURES.md
├── LANGUAGES.md
└── LIBRARIES.md
```

## Development priorities
1. Replace `Function()` evaluation with a safe expression parser.
2. Validate syntax and domain errors clearly (division by zero, invalid logarithms, invalid factorials, malformed expressions).
3. Make angle-mode behavior consistent across DEG, RAD, and GRA.
4. Implement or accurately relabel the currently placeholder math suites.
5. Add automated tests for arithmetic, trigonometry, conversions, and matrix operations.
6. Improve keyboard accessibility and semantic labels.
7. Consider splitting HTML, CSS, and JavaScript into separate files as the project grows.
