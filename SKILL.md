---
name: help-guide-driven-dev
description: Turn a spec into a help guide (an end-user manual published on a support site). Use it instead of a spec document when refining the spec of a new feature or enhancement. Also use it to update an existing help guide.
---

Write the spec as a publish-quality help guide that reads from the reader's (the product's end user's) point of view.
Development proceeds from that guide (help-guide-driven), and the same guide doubles as the one actually published to readers.
Every behavior of the system must be described in a way the reader can easily understand.
Explainability is the litmus test of design quality (the guide is the cost model of the UX). The goal also includes keeping spec debt, experience debt, and naming debt out.

## In -> Out of this job
- Input:
  - The requests, instructions, and narrative of the developer (whoever invokes this skill). References to specs or notes, if given
- Secondary input (state to consult):
  - Existing code
  - Existing help guides affected by this request (especially for enhancements; the guide's diff is a detector of breaking changes)
- Output:
  - Write a ready-to-publish help guide, based on the structure of `./reference/template.md`, as a single self-contained HTML file (`<feature-name>.html` unless a location is specified)
  - Write the guide in the language the developer uses, unless told otherwise
  - Response body: the path of the HTML file, and at the end a `## Decision log` (not included in the guide itself): list spec decisions you settled on your own without asking, one line each as "Issue / Decision / Why decided without asking" (including limits or time estimates you set that were not in the notes). Minor wording and formatting choices are out of scope.
- Proposals during the work (talk with the developer via AskUserQuestion):
  - When there are open or ambiguous spec points you cannot decide on your own
  - Spec-simplification proposals when explainability is hard to secure (a signal of spec debt, experience debt, or naming debt)
    - The simpler the spec, the better. Needlessly intricate specs that do not lead to value for the reader are targets for reduction

## Best Practices
- Mindset
  - Ask "how will the reader misunderstand this feature?"
  - Minimize room for interpretation
  - Cover every behavior; cut words. Writing is subtraction. Not being long is what reduces cognitive load the most
- Information design
  - Organize by task
  - Use an inverted pyramid
  - Information is not equal. Expose only the main path everyone takes; fold details that only some readers need into toggles
- Minimize cognitive load
  - Find the shape the information already has (layout, correspondence, flow, order, etc.), and choose, case by case, a presentation that makes that shape visible. Examples: for places on the screen, number them on a figure; for items × conditions, use a ✓ matrix. A table cell or list item that needs several sentences is a sign the presentation doesn't fit the shape
  - Distinguish Note / Warning / Tip, and don't overuse them
  - Include concrete examples and sample values
    - Pair abstract explanations with a typical example
    - Show a counterexample when misunderstanding is likely
- Wording
  - Write in the reader's vocabulary (mention only states the reader can observe)
  - Match UI labels and notation exactly
- Writing the spec
  - Write every behavior (the guide is a contract with the reader)
  - Write edge-case behavior
  - Non-functional requirements can be written as behavior by translating them into the reader's questions. For each operation, ask yourself these and check the article alone answers them:
    "Up to how many items / how many MB? How long will I wait? (a number, even if approximate)" "If it fails midway, how much has been applied?" "If I do it again, will it be duplicated?" "When and where will it show up?" "What if someone else operates on it at the same time?"
    Settle open points on the simpler side (all-or-nothing, overwrite, immediate) and record them in the decision log. Raise them as questions only when the spec could split significantly
  - Don't write internal targets (p95, availability rate, etc.) in the guide. Write only what can be translated into a contract with the reader (limits, approximate wait times)
- When you feel like writing "if ...", decide where it goes first

  | That branching is... | Where to write it |
  |---|---|
  | The reader does the same thing (only what happens differs) | Keep one procedure. Add the behavioral differences as spec in a table |
  | Determined before the operation starts (permissions, plan) | Prerequisites |
  | A different goal | Split into sections or articles. If only the means differ, "Do one of the following" + how to choose |
  | Discovered during the operation (a screen change, the previous result) | Inside that step as a conditional. Condition first, action after. Use a table if there are many |
  | What to do on failure | Error guide |

  Branching that fits no row, or that nests, is a signal for a spec-simplification proposal

## Gotchas
- What must be exhaustive is behavior, not the volume of words. Trying to write everything makes the guide verbose; yet when cutting words, it's easy to cut a behavior too (e.g., a condition gets narrower, or the result of an operation is no longer stated). Cut phrasing and duplication, never behavior

## Verify
- Review against the criteria in `./reference/rubric.md`, and fix defects before output
- Defects that cannot be fixed because they stem from the spec itself are handled either as a simplification proposal (issues not yet proposed) or as an entry in the decision log (already proposed and rejected, or not worth proposing)
