# Learnings

## Week 1, Monday

`contrastRatio` checks the contrast between two colors by first finding which one is lighter and which is darker, so swapping the two colors never changes the result. The ratio is not rounded because WCAG says it shouldn't be: a ratio of 4.497 would display as 4.50 but should still fail. Primitive tokens hold the raw values, while semantic tokens (like primary, secondary, disabled) say when to use them and point to a primitive; UI components only ever use semantic tokens, so in dark mode a semantic token can switch to a different primitive while its name stays the same. `CLAUDE.md` sets the rules for working in this project, with its description, naming, token and accessibility rules, and the agent reads it before every task. JavaScript surprised me by how similar it is to C++ while feeling more dynamic and flexible, for example declaring variables with `let` without stating a type.
