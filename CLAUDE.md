# esb-data

Append-only journal of ESB Networks outage data, written by a machine. There is
no code here and nothing to run.

- **Never hand-edit `raw/*.jsonl`.** These files are the only copy of this data
  that exists — ESB's API shows current outages only and purges each one a few
  hours after restoration, so nothing here can be re-fetched or backfilled.
- `esb.db` is gitignored and fully rebuildable from `raw/`. Delete it freely.
- Lines are written with sorted keys so two machines' logs merge with `sort -u`.
- Commits are made by the collector on a daily timer; a push with no new data is
  normal and deliberate.

The code, the documentation and the schema notes live in the sibling repository
[`baz8080/esb`](https://github.com/baz8080/esb), usually checked out at
`../esb`. Start with its `CLAUDE.md` — in particular the data-shape traps, which
are not guessable from looking at the JSON.

```bash
python -m esb_outages --data-dir . rebuild   # from ../esb
python -m esb_outages --data-dir . stats
```
