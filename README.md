# signalk-bosun

> **Placeholder.** No code here yet.
> This README just describes intent and tentative approach

A bosun inspects the hull, the rigging and the gear, reports what needs
attention, and commands nothing. The skipper decides. That relationship — sees
everything, advises plainly, holds no authority — is the one this project is
named for.

## What Bosun is not

[signalk-lint](https://github.com/mark-brannan/signalk-lint) answers a narrow
question well: *given a snapshot of this installation, which deterministic
rules fire?* It is pure, offline, testable, and free of any dependency on a
model.

## What Bosun is
Bosun complements the linter: Triage, explanation, correlation,
prioritisation, conversation — the parts that involve judgement rather than logic.

The form is TBD:

- An MCP server, so an agent can reason about a boat's state and configuration.
- An embedded model that triages and narrates findings on the boat itself.
- An admin-UI panel that explains findings in context.
- A notification publisher, mirroring findings into `notifications.*` so alarm
  panels surface them alongside everything else.
- Something else


## Tenets

**Read-only.** Bosun observes and advises. Every change to a vessel is made by
a human making a judgement call. 

**A Signal K plugin.** Bosun runs in process on the boat.  The plugin contract is thin enough that this can evolve to take whatever shape makes sense

**Deterministic checks belong in singalk-lint, not here.** If a check can be a pure
function over a snapshot, it is a rule and it lives in the linter where it can
be tested. Bosun is for heuristics, advice, opinions and to aid in decision making.

## License

Apache-2.0
