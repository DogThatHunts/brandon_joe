# Waypoint: brandon_joe

## What was done (2026-11-12 session)

### Project scaffolded from the KL_on_RiceRadio model

Built out `brandon_joe/` as a sibling project to `kl/KL_on_RiceRadio/` and
`kl/KL_on_Crrow/`, same layout:

```
transcripts/
  TXT/          # 16 raw transcripts
  prompts/      # the two independent analysis passes (see below)
  summaries/    # outputs of the passes above
summaries_html/
index.html
style.css       # cool-blue palette, copied from kl/KL_on_Crrow/style.css
```

Source: rows 1273-1288 (16 rows) of the "Queue" tab in the user's Transcription
Queue Google Sheet
(`1gws-Nmp5YFnMWK6oZgcEDkVL8SPMwhVWmBf_xZcaS9w`) — Brandon Joe's "Civilian
Knowledge Course 3.0" (CKC 3.0) series: one "Post Course Video 1" plus Videos
1-15, numbered into `transcripts/TXT/` as files `01`-`16` in sheet-row order.
Raw transcript text pulled from each row's `transcript_drive_link` (Google
Drive, plain-text export, timestamped `[0.0s - 11.0s]` lines, no speaker tags —
Brandon Joe is the sole speaker throughout, unlike the KL projects which have a
host).

Two videos (rows 10-11 / files `10`-`11`) are litigation-specific case
breakdowns ("City of Glendale Round 3") rather than general course content —
kept in the same numbered sequence, flagged for the ideas-summary pass to
topic-group rather than treat as a chronological aside.

### Citations target

Same shared, private register as `dave_champion`, `KL_on_Crrow`, and
`KL_on_RiceRadio`, now at `_citation-register/` (renamed from
`citation-register/` earlier this session) — `register.json` /
`SCHEMA.md`. New citations staged at
`_citation-register/pending/brandon_joe_2026-11-12.json`, not merged directly.

### Fork dispatched: ideas summary + citation extraction

One fork launched (agent id not recorded here — see session's Agent-tool
output if it needs resuming) to do the actual transcript reading and produce:

1. `transcripts/summaries/BrandonJoe-ideas-CKC3.md`
2. `transcripts/summaries/citations-sidecar.md`
3. `_citation-register/pending/brandon_joe_2026-11-12.json`

It was told to follow `transcripts/prompts/summarize_ideas.md` and
`transcripts/prompts/extract_citations.md` exactly (both already written in
full — see those files for the complete spec: input file list, topic/claim/
support/source structure, contradiction-flagging convention, citation
categories, resolver usage, pending-file shape). Verbatim fork prompt:

> Do NOT re-derive anything about the broader task — just execute this
> content-authoring work directly, using your own tools (Read, Write, Bash,
> Grep). This is not a research question, it's an authoring task: read the 16
> real transcript files and actually write the two real output documents
> described below, following the two prompt files to the letter. Do not stub,
> summarize-the-prompt-back, or produce placeholder content — these documents
> must reflect the actual transcript content.
>
> Context: I'm building out
> `/Users/edward/Projects/law_sovereignty/brandon_joe/` as a sibling project to
> `/Users/edward/Projects/law_sovereignty/kl/KL_on_RiceRadio/`, which is the
> model this is based on. The transcripts are already in place at
> `/Users/edward/Projects/law_sovereignty/brandon_joe/transcripts/TXT/` (16
> files, numbered 01-16). I already wrote two prompt files there:
>
> - `/Users/edward/Projects/law_sovereignty/brandon_joe/transcripts/prompts/summarize_ideas.md`
> - `/Users/edward/Projects/law_sovereignty/brandon_joe/transcripts/prompts/extract_citations.md`
>
> Your job: follow BOTH prompt files exactly as written (they are complete,
> detailed specs — read them first, they tell you the input files, what to
> extract, how to organize it, and the exact output paths). Produce all of
> these real, fully-written output files:
>
> 1. `/Users/edward/Projects/law_sovereignty/brandon_joe/transcripts/summaries/BrandonJoe-ideas-CKC3.md`
>    — per `summarize_ideas.md`'s spec (topic-organized legal-claims summary of
>    all 16 transcripts, with inline contradiction flags and the two roll-up
>    sections at the end).
> 2. `/Users/edward/Projects/law_sovereignty/brandon_joe/transcripts/summaries/citations-sidecar.md`
>    — per `extract_citations.md`'s spec (every legal/tax/UCC/CA-statute
>    citation found, grouped by category, with locating quotes and
>    resolved/unresolved status).
> 3. A pending file for the shared citation register at
>    `/Users/edward/Projects/law_sovereignty/_citation-register/pending/brandon_joe_2026-11-12.json`
>    — only NEW citations not already in
>    `/Users/edward/Projects/law_sovereignty/_citation-register/register.json`
>    (read that file first — check its `resolvers` block and existing records
>    so you don't duplicate what's already there), in the register's
>    per-category record shape per that repo's `SCHEMA.md`. Do NOT edit
>    `register.json` directly.
>
> Important specifics to get right:
> - Brandon Joe is the sole speaker in all 16 transcripts (no host, unlike the
>   KL projects these prompts are adapted from) — there is no
>   speaker-attribution ambiguity to resolve.
> - Read every transcript file fully — they are real, substantive content
>   (timestamped spoken-word transcripts of a legal self-help/"sovereign
>   citizen"-adjacent course called "Civilian Knowledge Course 3.0"), not
>   filler.
> - Follow the exact exclusions in the prompts (course-sales pitches, banter,
>   profanity-laden asides with no legal content) and exact inclusions (his
>   actual legal claims/arguments/citations).
> - Use the resolver templates in `_citation-register/register.json`'s
>   `resolvers` block to build URLs for USC/CFR/UCC/Treasury-Decision cites;
>   never fabricate a URL for anything else — leave `url: null` and flag
>   `[UNRESOLVED — needs manual verification]` in the sidecar if there's no
>   resolver and no existing register match.
> - When done, report back: a short list of the topic headings you used in the
>   ideas summary, how many citations total / how many were new (in the
>   pending file) vs already-in-register, and any notable contradictions or
>   unresolved/ambiguous citations a human should look at (mirroring how
>   KL_on_RiceRadio's README documents its TBD items) — I'll use that to write
>   this project's README and waypoint doc, so be concrete and complete, not
>   just "done."

Fork was still running as of this waypoint entry — not yet merged/reviewed.

### Not yet done

- Site HTML (`index.html`, `summaries_html/*.html`) — pending the fork's
  summary/citation output.
- README.md, top-level `.gitignore` entry for `brandon_joe/` (parent repo's
  `.gitignore` doesn't yet list it — needs adding, same pattern as the other
  independent-repo projects).
- `git init` + GitHub remote + push (user explicitly approved this setup
  style).
- Citation-register merge review (new pending file needs human review before
  being folded into `register.json`, per that repo's own convention).
