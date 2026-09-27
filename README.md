An agent skill that expresses specs as a help guide (an end-user manual published on a support site): understandable and concrete.
Humans review the spec in that form, and AI implements from it.

## Why
- It doubles as a stress test: can the spec be explained clearly to readers? (If not, you are most likely building in spec debt, experience debt, or naming debt.)
- It keeps AI from implementing needlessly intricate, odd, or implicit behavior on its own.
- Asking for a help guide yields text people actually want to read, unlike "generate a spec" (it suppresses AI slop).
- It keeps AI from drifting into implementation details (it stays at the level of the spec).
- The output can be reused as-is for your support site, and is easy to read for non-engineers in your company.

Behavior that is not documented in the manual should not exist in the first place, so the level of detail is no different from a spec.
A separate "spec document" is unnecessary.

## Install

```bash
npx skills add yodakeisuke/help-guide-driven-dev
```

The generated guide is written in the language you use when talking to the agent.
