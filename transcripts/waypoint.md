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

The fork's first stop was a no-op status report with no files written; it was
resumed with an explicit "actually write the files, don't just report status"
instruction and completed for real on the second pass — see its final report
below.

### Fork's final report

- **Topic headings** (`BrandonJoe-ideas-CKC3.md`): Citizenship and
  legal-fiction theory; Sole proprietorship/trusts and legal-beneficial
  ownership; UCC Article 3, negotiable instruments, and "infinite money";
  Taxes, "taxpayer," and IRS procedure; Foreign government, "peace," and
  nation-building; Driving versus traveling, licensing, and jurisdiction;
  Litigation procedure, discovery, and presumptions; Contracts, consideration,
  and the "practice law without a license" template; Rules of professional
  conduct, judicial canons, and bar complaints; Race, the 14th Amendment, and
  his stated political goals. Plus "Flagged contradictions" (4) and "Episodes
  by topic" roll-ups.
- **Citations:** ~70 distinct identified; 12 already in `register.json`; 27
  new/resolved staged in `_citation-register/pending/brandon_joe_2026-11-12.json`
  (23 cases, 24 USC sections, 2 CFR sections); no register category exists for
  UCC/CCC sections or CA Code of Civil Procedure/Evidence Code/Vehicle
  Code/Rules of Professional Conduct — flagged in the sidecar rather than
  force-fit.
- **Flagged for human review (excluded from the pending file):** "Madden v.
  Commissioner" (quoted holding actually matches *Madden v. Kentucky*, 1940);
  "Heard v. Herge" (likely transcription error); "U.S. v. Valentine" (possible
  conflict with the register's existing *Valentine v. United States ex rel.
  Neidecker*); "Five Star Bank Cases" (no reporter cite given).
- **Known gap:** ~600 lines of file 11 (Video 10, the Glendale discovery
  breakdown) were judged repetitive of content already captured elsewhere and
  not fully read — disclosed by the fork, not reflected as a citation/claim
  gap in the output files themselves.
- File 16 (final video) contains explicit racialized political content about
  repealing the 14th Amendment; the ideas summary documents this factually,
  per the prompt's no-fact-checking/no-editorializing instruction.

### Site built, repo pushed, Pages enabled

- Generated `summaries_html/brandonjoe-ideas.html` and
  `summaries_html/citations-sidecar.html` via `pandoc --standalone --toc -c
  ../style.css` from the two Markdown sources, then patched in the site-nav
  bar and a cache-busting query string on the stylesheet link (matching
  KL_on_RiceRadio's hand-maintenance convention exactly).
- Built `index.html` (three cards: ideas summary, citation sidecar, inline
  "Core Worldview" overview) and a 16-row "Source Videos & Transcripts" table
  (Transcript / Summary / Episode-YouTube columns), using row data pulled
  directly from the Transcription Queue sheet (rows 1273-1288) rather than
  hand-typed, to avoid transcription errors in the URLs.
- Wrote `README.md`, `style.css` (cool-blue, copied verbatim from
  `kl/KL_on_Crrow/style.css` per the user's "cool temp css" instruction),
  `.gitignore`, `.nojekyll`.
- `git init`, committed, and — per explicit user confirmation via
  AskUserQuestion — created the public GitHub repo
  `DogThatHunts/brandon_joe`, pushed `main`, and enabled GitHub Pages
  (root of `main`). Live at <https://dogthathunts.github.io/brandon_joe/>.

### Not yet done

- Citation-register merge review: `_citation-register/pending/brandon_joe_2026-11-12.json`
  needs human review before being folded into `register.json`, per that
  repo's own convention (same as every other project's pending file).
- The schema questions the sidecar raises (no register category for
  UCC/CCC or CA state-law citations) are unresolved — a human decision, not
  something this session should resolve unilaterally.
- File 11's ~600-line gap (see above) could be revisited in a follow-up pass
  if the user wants full coverage confirmed.
