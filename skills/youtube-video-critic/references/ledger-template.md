# YouTube video ledger template

This is a blank skeleton, not a finished ledger. Before an evaluation that touches the ledger (see Step 5 in SKILL.md for when that applies), check whether `references/youtube-critic-ledger.md` already exists in this skill's directory.

- **If it doesn't exist:** copy the header below, save it as `references/youtube-critic-ledger.md`, then append the first row for this evaluation. That file — not this template — is the running ledger.
- **If it already exists:** read it, then append one row per evaluation instead of recreating it from scratch.
- **If there's no filesystem available** (e.g. plain chat mode with no file tools): keep the same rows in conversation memory instead, using this structure as the row format, and tell the user the ledger won't persist past this conversation.

This file is git-ignored, so it won't be committed to the plugin's source repo by normal git operations (`git add -A`, etc.) — but that also means it isn't backed up anywhere. If this plugin is ever reinstalled from a fresh download rather than updated in place, the ledger may not survive. If the user wants to keep it across a fresh reinstall, tell them to back it up themselves.

---

## Skeleton to copy into `youtube-critic-ledger.md`

```markdown
# YouTube Video Critic — Ledger

| Date | Title | Link | Channel | Length | Verdict | Score | Reason |
|---|---|---|---|---|---|---|---|
```

## Row format notes

- Format `Date` as `YYYY-MM-DD`.
- Include the video's URL in `Link` — the unambiguous identifier, so `Title` can stay short and readable rather than needing to be the full title.
- Keep `Reason` to one short, precise sentence — no multi-clause summaries.
- Escape any literal `|` inside `Title`, `Channel`, or `Reason` as `\|` before writing the row. An unescaped pipe splits that row into extra columns and corrupts every row after it in rendered markdown.
- Format `Length` as `mm:ss` for videos under one hour, or zero-padded `h:mm:ss` at or above one hour (e.g. `47:12` vs `1:02:03`) — stay consistent within the file.
- Format `Verdict` as the exact verdict name from SKILL.md Step 3 (`Worth watching in full`, `Skim it`, or `Skip it, the summary is enough`) — not an abbreviation or paraphrase.
- Format `Score` as `X/10`, matching the value score from SKILL.md Step 3 exactly (e.g. `8/10`, not `8` or `8.5/10` unless the evaluation itself used a half-point).
