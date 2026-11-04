## Software Engineering Style
- Use guard clauses and early returns instead of nested else. A
plain else is fine for two symmetric branches.
- Parse unknown input once, at the boundary that owns it, into a
typed value. Pass that value inward; don't re-check it.
- Write the main function as thne happy path: guards first, then
straight-line flow. Move bulky validation or supporting detail
into small helpers paced next to their caller.
- Don't extract a single-use helper unless it hides a a genuinely
complex boundary, needs direct testing, or has a name that makes
the caller clearer. Otherwise inline it.
- Before adding complexity for a speculative case, ask me, with
one line each on the failure mode, likelihood, and cost. If you
can't ask, skip it and list it in your summary. Standard hardening
at trust boundaries (parameterized queries, path checks, no
secrets in logs) isn't speculative; do it.
### Comments
- Comments don't narrate what code does. Comment only what code
can't say: a non-obvious why (constraint, workaround, invariant)
or the how of a genuinely intricate algorithm.
- Never put session content in code: requests, instructions,
review feedback, etc. Change history belongs in the commit
message.
- Never restate what the code its names already say
- Leave existing comments alone unless your change invalidates
one; then correct it.
- Doc comments on public API (Javadoc, docstrings, TSDoc, etc)
follow the repo's conventions and state the contract, not the
implementation.

