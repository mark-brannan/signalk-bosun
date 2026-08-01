# signalk-bosun

> **Status: a name holding an open slot.** There is no code here yet, and that
> is deliberate. This README describes what the slot is for and what has
> already been decided about it, so that whatever fills it does so on purpose.

A bosun inspects the hull, the rigging and the gear, reports what needs
attention, and commands nothing. The skipper decides. That relationship — sees
everything, advises plainly, holds no authority — is the one this project is
named for.

## The slot

[signalk-lint](https://github.com/mark-brannan/signalk-lint) answers a narrow
question well: *given a snapshot of this installation, which deterministic
rules fire?* It is pure, offline, testable, and free of any dependency on a
model. It should stay that way.

Bosun is for everything that isn't that. Triage, explanation, correlation,
prioritisation, conversation — the parts that need judgement rather than logic,
and which would destroy the linter if they were smuggled into it as rules.

**What form that takes is not yet decided.** Candidates, none committed:

- An MCP server, so an agent can reason about a boat's state and configuration.
- An embedded model that triages and narrates findings on the boat itself.
- An admin-UI panel that explains findings in context.
- A notification publisher, mirroring findings into `notifications.*` so alarm
  panels surface them alongside everything else.
- Something none of the above.

Picking now would be architecture by vibes. The shape will be decided when
there is enough experience with real findings on real boats to decide it well.

## What is already decided

**Read-only.** Bosun observes and advises. Every change to a vessel is made by
a human who decided to make it. This is not a limitation to be relaxed later
when the tooling feels trustworthy; it is the point.

**A Signal K plugin.** Which commits to *where* the code runs — in-process, on
the boat — but deliberately not to *what* it does. The plugin contract is thin
enough to host almost anything.

**Never on the critical path.** Whatever Bosun becomes, `signalk-lint` must
remain fully useful without it. A boat at anchor with no internet gets the
complete rule set; Bosun is strictly additive. Anything that inverts that
relationship is the wrong design.

**Deterministic checks belong in lint, not here.** If a check can be a pure
function over a snapshot, it is a rule and it lives in the linter where it can
be tested. Only genuine judgement belongs in Bosun. The day that boundary
blurs, the separation was theatre.

## Why a separate repo

Lint should be boring: stable, semver-disciplined, community-contributed,
plausibly upstreamable into Signal K itself one day. Bosun will chase a model
and protocol landscape that moves monthly. Coupling them would make the stable
thing inherit the unstable thing's release cadence.

There is also a constituency in the marine community that wants nothing to do
with AI on their boat, and they are entitled to the linter without an opinion
attached.

## License

Apache-2.0
