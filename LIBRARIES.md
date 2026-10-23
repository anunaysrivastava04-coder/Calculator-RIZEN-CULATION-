# Important Libraries and APIs

## Tailwind CSS (CDN)
Used throughout the HTML for utility classes covering layout, spacing, colors, typography, responsive breakpoints, borders, and visibility.

```html
<script src="https://cdn.tailwindcss.com"></script>
```

**Note:** The CDN approach is convenient for prototypes. For production, consider a pinned, compiled Tailwind CSS build.

## Browser Web Audio API
Used to generate a short synthesized click sound with an oscillator and gain node. This is a browser API, not an external package.

```javascript
const ctx = new (window.AudioContext || window.webkitAudioContext)();
const osc = ctx.createOscillator();
const gain = ctx.createGain();

osc.type = 'sine';
osc.frequency.setValueAtTime(600, ctx.currentTime);
gain.gain.setValueAtTime(0.03, ctx.currentTime);
gain.gain.exponentialRampToValueAtTime(0.0001, ctx.currentTime + 0.04);

osc.connect(gain);
gain.connect(ctx.destination);
osc.start();
osc.stop(ctx.currentTime + 0.04);
```

## Native JavaScript Math and DOM APIs
The project uses built-in features including `Math.sin`, `Math.cos`, `Math.sqrt`, `Math.log10`, `Math.PI`, arrays, regular expressions, and `document.getElementById`.

## No other external libraries identified
The supplied HTML does not show React, Vue, Angular, a matrix package, or a dedicated math-expression parser.
