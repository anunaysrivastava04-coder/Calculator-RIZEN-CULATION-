# Features (with code)

The examples below are taken or adapted from the supplied HTML source.

## 1. Scientific expression input

The keypad inserts tokens into the expression string.

```javascript
function insertText(txt) {
  playClickSound();
  if (!state.powerOn) return;

  if (state.expr === '0' && !['.', '+', '-', '*', '/', '^'].includes(txt)) {
    state.expr = txt;
  } else {
    state.expr += txt;
  }
  updateLcd();
}
```

## 2. Degree-mode trigonometry and expression preparation

```javascript
.replace(/sin\(/g, state.angleMode === 'DEG'
  ? 'Math.sin((Math.PI/180)*'
  : 'Math.sin(')
.replace(/cos\(/g, state.angleMode === 'DEG'
  ? 'Math.cos((Math.PI/180)*'
  : 'Math.cos(')
.replace(/tan\(/g, state.angleMode === 'DEG'
  ? 'Math.tan((Math.PI/180)*'
  : 'Math.tan(')
```

The supplied code converts degree input to radians for the JavaScript trigonometric functions when DEG mode is selected. RAD and GRA are present as UI state options, but the GRA conversion is not implemented in this expression transformation.

## 3. Alternate result formats

The result display includes fraction approximation, DMS, scientific notation, and integer HEX/BIN representations.

```javascript
fmtF = toFractionString(resVal);
fmtD = toDmsString(resVal);
fmtE = resVal.toExponential(4);
fmtHB = `HEX:${Math.round(resVal).toString(16).toUpperCase()} | BIN:${Math.round(resVal).toString(2)}`;
```

HEX and BIN are based on the rounded integer part of the result, not a fractional floating-point encoding.

## 4. Matrix addition and multiplication

```javascript
function matAdd(A, B, sign = 1) {
  return A.map((row, r) => row.map((v, c) => v + sign * B[r][c]));
}

function matMultiply(A, B) {
  const rA = A.length, cA = A[0].length, cB = B[0].length;
  const C = Array.from({ length: rA }, () => Array(cB).fill(0));

  for (let i = 0; i < rA; i++) {
    for (let j = 0; j < cB; j++) {
      let sum = 0;
      for (let k = 0; k < cA; k++) sum += A[i][k] * B[k][j];
      C[i][j] = Math.abs(sum) < 1e-12 ? 0 : sum;
    }
  }
  return C;
}
```

## 5. Determinant and inverse helpers

```javascript
function matDet(M) {
  const n = M.length;
  if (n === 1) return M[0][0];
  if (n === 2) return M[0][0] * M[1][1] - M[0][1] * M[1][0];

  if (n === 3) {
    return (
      M[0][0] * (M[1][1] * M[2][2] - M[1][2] * M[2][1]) -
      M[0][1] * (M[1][0] * M[2][2] - M[1][2] * M[2][0]) +
      M[0][2] * (M[1][0] * M[2][1] - M[1][1] * M[2][0])
    );
  }
  return 0;
}
```

The inverse helper uses the determinant and adjugate and rejects near-singular matrices.

## 6. Sound feedback

```javascript
function toggleSoundFeedback() {
  state.soundEnabled = !state.soundEnabled;
  const btn = document.getElementById('soundToggleBtn');
  btn.textContent = state.soundEnabled ? '🔊 Sound: ON' : '🔇 Sound: OFF';
}
```

## Important security note

The supplied implementation evaluates prepared expressions using `Function()`. This is unsafe for arbitrary untrusted input. Use a purpose-built math parser with an explicit allowlist of operators and functions before deploying publicly.
