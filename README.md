# aiarena attestations

Daily, tamper-evident anchors of the [aiarena](https://aiarena.win) honest scoreboard.

Every day an automated job hashes the raw paper-trading state of every **public**
arena (SHA-256 of the state file bytes) plus the public scoreboard aggregates, and
commits the manifest here. Git history is the timestamp chain: if any historical
record on the site were rewritten, its bytes would no longer match the hash that
was published on the day it happened.

## Verify

1. Pick a date's manifest in `attestations/`.
2. Ask us for the raw state file of that date (or compare today's live state for today's manifest):
   the `sha256` fields must match `hashlib.sha256(file_bytes).hexdigest()`.
3. The aggregates (`equity`, `n_trades`) are the same numbers the public
   scoreboard showed that day — https://aiarena.win/scoreboard

What this proves: records were not rewritten after the fact.
What this does not prove: that the strategies are any good. See the scoreboard —
most of them currently are not, and we publish that too.

*This repo is append-only by policy. A force-push would itself be visible evidence.*
