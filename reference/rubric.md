# Help guide rubric

The reader is stuck, anxious, and scanning rather than reading. Manuals are not read in
advance; they are opened when someone gets stuck. Definition of success: the reader solves
it themselves and no ticket is created.
Next best: a support agent can close the inquiry in one round trip using only this article.

The article is the full extent of the behavior: every rule and behavior of the feature can be
derived from the article, and anything not written means "cannot be done / does not happen".

Criteria that don't apply to the task may be skipped. But "applies and isn't written" is an omission.

## Critical defects (any one of these fails the article, however good the rest is)

- A consequence on the level of irreversible, data loss, billing, or publishing to / notifying
  others is not stated before the operation that causes it
- The main task cannot be completed from the article alone (skipped steps, unexplained decisions)

## Criteria

1. The introduction answers the reader's situation. From the title and lead, the reader can
   judge in seconds "does this concern me?" and "when and for what do I use it, and what do I
   get?", and the scope (required permissions, prerequisite settings, etc.) is clear up front.
   It does not open with a self-introduction of the feature or a list of benefits.

2. Behavior is written as prediction. It is written as "under this condition, if you do this,
   this happens", results are observable (screen changes, notifications, outputs), and
   constraints, limits, and the time processing or propagation takes are given as numbers
   (approximate numbers are fine).
   Test: can "what happens if I ...?" be answered from this article alone without guessing?
   "Automatically" without a condition, "will be reflected" without a result, and "many" or
   "a certain period" without a number are defects.

3. No late reveal of consequences. Common prerequisites (permissions, settings, preparation)
   come before the procedure, and the consequences of each operation (whether it can be undone,
   who can see it / gets notified, impact on existing data) come before that operation. The more
   serious the consequence, the earlier and more prominent. The number and strength of emphasis
   is proportional to the severity of the consequence, and content that is merely supplementary
   does not take the form of a warning and bury the real warnings.

4. Steps map to goals and completion is verifiable. Each step corresponds to one goal, with no
   unexplained decisions in between. The branching condition comes before the branch. Terms match
   the screen labels, one name per concept. The end of the procedure says how to confirm success.

5. Choices come with how to choose. When modes or multiple ways appear, not only the procedure
   but "in what situation to choose which, and what changes when you choose it" is written.

6. Stumbles have exits. Failures that naturally occur with this feature (no permission, invalid
   input, limit exceeded, failure midway) have clues findable from the symptom (the displayed
   wording), the cause, and recovery steps. For operations that can fail midway, it is clear how
   much was applied and what happens on retry, and the next action when self-resolution is
   impossible is shown.

7. Nothing missing, nothing extra. Every statement contributes to solving the reader's task,
   with no promotion or padding. The reader's natural next questions (can I edit it, delete it,
   redo it?) are answered, stated as "cannot", or referred to the article that covers them.
   Intricate information is shown in a presentation that fits its shape (not only tables). It fails
   if the reader has to assemble a layout, correspondence, or flow in their head from prose, or if a
   table cell or list item needs several sentences.

8. Details are folded. Only the main path everyone takes is exposed; details that only some
   readers need are folded into toggles, and their contents are predictable from the summary
   alone. A serious consequence that can only be noticed by opening a toggle is a defect.
