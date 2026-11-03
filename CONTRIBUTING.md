# Contributing

Thanks for your interest in improving NEWSROOM-PM. The prompt is the product, so changes are judged by what they do to the output, not by how they read.

## Proposing a change

1. **Open an issue first** for anything beyond a typo, describing the failure you observed (which host, which rule, what the brief got wrong) and the fix you propose.
2. **Edit `prompts/NEWSROOM.md` only.** Files under `prompts/archive/` are frozen snapshots and are not updated.
3. **Keep the handoff contract intact.** Station 2 must never gain access to anything but the Fact Packets, and every number in the brief must still trace to a claim ID.
4. **Prefer rules that produce evidence.** A good rule changes what the model prints (a label, a count, a Gaps entry) so a reader can audit it. A rule that only asks the model to "be careful" is unlikely to be accepted.

## Testing a change

Run the modified prompt on at least two hosts (for example Claude and ChatGPT) on the same day with the same input (`go`), then check:

- All six asset classes produce a packet.
- The Checkpoint line reports a score, and any `DEGRADED` item is explained in the footer.
- Every `Confirmed by N` claim names N sources that are tagged `original` or `primary` in the Sources list.
- Every sentence in the Desk Brief carries claim IDs, and the cited claims contain the fact used.
- Word count is within the limit for the mode.
- No figure from Gaps appears as fact in the brief.

Attach the resulting briefs to the pull request under `examples/<YYYY-MM-DD>/` using the naming pattern `desk-brief_<host>.pdf`.

## Versioning

When a change alters the output structure, the verification rules, or the asset-class coverage:

1. Copy the current `prompts/NEWSROOM.md` to `prompts/archive/NEWSROOM_v<N>.md`.
2. Apply the change to `prompts/NEWSROOM.md`.
3. Add an entry at the top of `CHANGELOG.md` and update the version table in `README.md`.

Smaller clarifications that do not change behaviour can go straight into the live prompt with a changelog line.
