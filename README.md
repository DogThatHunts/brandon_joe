# brandon_joe

Video-transcript summaries for Brandon Joe's "Civilian Knowledge Course 3.0"
(CKC 3.0) series, plus two related "City of Glendale Round 3" litigation
case-breakdown videos. Modeled on `KL_on_RiceRadio` / `KL_on_Crrow`, but unlike
those two projects there is a single speaker throughout (Brandon Joe) — no
host, no speaker-attribution ambiguity.

## Layout

```
transcripts/
  TXT/          # 16 raw transcripts, timestamped, no speaker tags
  prompts/      # the two independent analysis passes run over TXT/
    summarize_ideas.md       # topic-organized summary of his legal claims
    extract_citations.md     # legal/tax citation extraction
  summaries/    # outputs of the passes above
    BrandonJoe-ideas-CKC3.md # his ideas by topic, with contradictions flagged
    citations-sidecar.md     # every citation found, with locating quotes
```

## Source

Rows 1273-1288 of the "Queue" tab in the project owner's Transcription Queue
Google Sheet — source videos are YouTube uploads, transcribed and summarized
through that pipeline. File `01` is "CKC 3.0 Post Course Video 1"; files
`02`-`16` are CKC 3.0 Videos 1-15. Files `10`-`11` are two litigation-specific
"City of Glendale Round 3" case-breakdown videos rather than general course
content, numbered into the same sequence.

## Citations

This project's citations are extracted and merged into the shared, private
register at `~/Projects/law_sovereignty/_citation-register/` (`register.json`),
the single source of truth across `dave_champion`, `KL_on_Crrow`,
`KL_on_RiceRadio`, and this project. This project does not maintain its own
copy of citation data — `transcripts/summaries/citations-sidecar.md` is a
human-readable locating index (quotes + file references), not the data of
record.

As of 2026-11-12, the citation scan is complete but **not yet merged**: ~70
distinct citations found; 12 already existed in `register.json`; 27 new,
resolved citations (mostly cases and USC/CFR sections) are staged in
`_citation-register/pending/brandon_joe_2026-11-12.json`, awaiting human
review per that repo's convention. A handful of ambiguous/unresolved
references were deliberately left out of the pending file rather than
guessed — see `citations-sidecar.md`'s "Summary counts" section:

- **"Madden v. Commissioner"** — the quoted holding actually matches *Madden
  v. Kentucky* (1940); name/holding mismatch, needs confirmation before merge.
- **"Heard v. Herge"** — unconfirmed, likely a transcription error.
- **"U.S. v. Valentine"** — possible conflict with the register's existing
  *Valentine v. United States ex rel. Neidecker*; flagged, not merged.
- **"Five Star Bank Cases"** — no reporter citation given in the transcript.
- Three unnamed cases cited via Corpus Juris Secundum, and an unspecified IRM
  provision re: endorsing IRS bills back to the agency.

The sidecar also flags that the shared register's schema has **no category**
for UCC/California Commercial Code sections, or for California Code of Civil
Procedure / Evidence Code / Vehicle Code / Rules of Professional Conduct —
all heavily cited across this series (UCC Article 3 especially, since Video 4
is dedicated to it) — for human decision on whether/how to extend the schema.

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
