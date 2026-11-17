# brandon_joe

Video-transcript summaries for Brandon Joe's "Civilian Knowledge Course 3.0"
(CKC 3.0) series — course videos 1–15 plus four "Post Course" videos — and two
related "City of Glendale Round 3" litigation case-breakdown videos. Modeled on `KL_on_RiceRadio` / `KL_on_Crrow`, but unlike
those two projects there is a single speaker throughout (Brandon Joe) — no
host, no speaker-attribution ambiguity.

## Layout

```
transcripts/
  TXT/          # 19 raw transcripts, timestamped, no speaker tags
  prompts/      # the two independent analysis passes run over TXT/
    summarize_ideas.md       # topic-organized summary of his legal claims
    extract_citations.md     # legal/tax citation extraction
  summaries/    # outputs of the passes above
    BrandonJoe-ideas-CKC3.md # his ideas by topic, with contradictions flagged
    citations-sidecar.md     # every citation found, with locating quotes
```

## Source

Rows 1273-1288 of the "Queue" tab in the project owner's Transcription Queue
Google Sheet (files `01`-`16`), plus rows 1537, 1568 and 6105 (files `17`-`19`,
Post Course Videos 2-4, added 2026-11-17) — source videos are YouTube uploads,
transcribed and summarized through that pipeline. File `01` is "CKC 3.0 Post
Course Video 1"; files `02`-`16` are CKC 3.0 Videos 1-15; files `17`-`19` are
Post Course Videos 2, 3 and 4. Files `10`-`11` are two litigation-specific
"City of Glendale Round 3" case-breakdown videos rather than general course
content, numbered into the same sequence.

File numbers are stable identifiers (the summaries and citation files refer to
videos by them) and do not match the order shown on the site: `index.html`
lists Videos 1-15 first (files 02-16), then the Post Course videos in order
(files 01, 17, 18, 19).

**Duplicate queue rows (to resolve later):** the sheet has several rows for the
same title — "Post Course Video 2" at rows 1375, 1492 and 1537 (this project
uses 1537), and "Post Course Video 1" at rows 1274 and 1540 (this project uses
the 1273/1274 row). Not yet reconciled; check whether the duplicates differ in
transcript or summary status before deleting any.

## Citations

This project's citations are extracted and merged into the shared, private
register at `~/Projects/law_sovereignty/_citation-register/` (`register.json`),
the single source of truth across `dave_champion`, `KL_on_Crrow`,
`KL_on_RiceRadio`, and this project. This project does not maintain its own
copy of citation data — `transcripts/summaries/citations-sidecar.md` is a
human-readable locating index (quotes + file references), not the data of
record.

**Merged 2026-11-17** into the shared register (commit `f6ba310` in `_citation-register`): the
2026-11-12 pending file (files 01-16), a 2026-11-17 supplement for files 17-19 (Post Course Videos 2-4),
and the sibling `KL_on_RiceRadio` pending file. Added 26 cases, 29 USC sections, 1 CFR section, 23 UCC
sections (the first records in the new `ucc_sections` category) and 3 Acts of Congress; the pending
files now live in `_citation-register/pending/merged/`. Case URLs were checked before merge (see that repo's
CHANGELOG). Items deliberately left out are tracked in that repo's `TBD_later.md` ("2026-11-17 brandon_joe
unresolved"):

- **"U.S. v. Valentine"** — *not* the register's *Valentine v. U.S. ex rel. Neidecker* (the quote is not in that opinion); likely a Puerto Rico case, unidentified. **TBD — do not forget.**
- **"Madden v. Commissioner"** — the quoted holding matches *Madden v. Kentucky* (1940); confirm before adding.
- **"Heard v. Herge"** — likely a transcription error.
- **"Five Star Bank Cases"**, three unnamed Corpus Juris Secundum cases, an unspecified IRM provision, the unnamed Fourth Circuit "sole proprietorship" case — no usable cite yet.
- No register category yet for the Federal Rules, California Code of Civil Procedure / Evidence Code / Vehicle Code / Rules of Professional Conduct, or local rules.

## Ideas summary

`transcripts/summaries/BrandonJoe-ideas-CKC3.md` is independent of the
citation pass — it summarizes Brandon Joe's legal claims and arguments by
topic, flags contradictions inline, and does not attempt to verify or resolve
any citation he mentions (that's the citation pass's job). It also does not
fact-check or editorialize on whether his claims are correct, consistent with
the other projects in this family. The final video's content includes
explicit, non-editorialized documentation of his stated 14th-Amendment-repeal
political goals and their racial framing — see that document's "Race, the 14th
Amendment, and his stated political goals" section.

## Website

Published via GitHub Pages at <https://dogthathunts.github.io/brandon_joe/>,
built from `index.html`, `style.css` (cool-blue palette, matching
`KL_on_Crrow`), and the HTML renders of the two summary docs in
`summaries_html/` (`brandonjoe-ideas.html`, `citations-sidecar.html`) —
generated from the Markdown sources via `pandoc --standalone --toc -c
../style.css`, then hand-patched with the site nav bar and a cache-busting
query string on the stylesheet link. These HTML files are not
auto-regenerated on every edit — any edit to a summary doc needs a matching
pandoc regeneration.

`index.html` has three cards (links to the ideas summary, the citation
sidecar, and an inline "Core Worldview" overview) plus a "Source Videos &
Transcripts" table with one row per episode (01-16) and three columns:

- **Transcript** — links to the raw `.txt` in this repo.
- **Summary** — links to that episode's page on the separate
  `transcript-summaries` site (`https://dogthathunts.github.io/transcript-summaries/`),
  sourced from the project owner's "Transcription Queue" Google Sheet (master
  "Queue" tab, column AA).
- **Episode (YouTube)** — links to the original upload.
