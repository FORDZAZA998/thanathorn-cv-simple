# Learning: Date-fns Format String Consistency (2026-03-01)

## Context
Debugging `floodboy-blockchain.html` where Chart.js failed to render due to an `unescaped latin alphabet character 'A'` in the version of `date-fns` used by the adapter.

## The Bug
The format string `hA` was used in `displayFormats` for the time scale.
```javascript
displayFormats: { hour: 'hA' } // Error: unescaped 'A'
```

## The Fix
Change to `ha` (lowercase 'a' for AM/PM) or escape the 'A' if literal text was intended. In this case, standard AM/PM format was the goal.
```javascript
displayFormats: { hour: 'ha' } // Correct
```

## Lesson
Always verify format string tokens against the specific version of the library. Tokens like `A`, `S`, `D` are often reserved and must be escaped (`\A`) if used as literals, or changed to their valid lowercase counterparts for functional formatting.
