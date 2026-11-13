# Prompt: Summarize Brandon Joe's ideas across the CKC 3.0 transcripts

You are reading transcripts from Brandon Joe's "Civilian Knowledge Course 3.0"
(CKC 3.0) video series, plus two related "City of Glendale Round 3" case-breakdown
videos. Each transcript uses timestamps in the form `[0.0s - 11.0s]` followed by
spoken text. There are no explicit speaker tags and (unlike the KL projects) no
host — this is Brandon Joe speaking solo to camera throughout. Your job is to
extract and summarize **only Brandon Joe's legal ideas** — not banter, audience
asides, or show logistics (sign-up pitches, course-version housekeeping, etc.),
except where needed as minimal context.

## Input

All `.txt` files in `transcripts/TXT/` (16 transcripts total):

1. `01_20260806_CKC 3.0 Post Course Video 1 - Practising Law Without a License and First Amended_0bec3cba.txt`
2. `02_20260806_CKC 3.0 - Video 1 - Citizenship for Men_ Women and Children _not legal fictions__84335cec.txt`
3. `03_20260806_CKC 3.0 - Video 2 - Legal Fictions and the Sole Proprietorship_f75ddbab.txt`
4. `04_20260806_CKC 3.0 - Video 3 - Foreign Government_ Peace and Nation Building_267c419d.txt`
5. `05_20260806_CKC 3.0 - Video 4 - UCC Article 3 - Money and Negotiable Instruments_5e25ad83.txt`
6. `06_20260806_CKC 3.0 - Video 5 - Taxes_ Definitions_ Forms_ and IRS Tactics_289300b9.txt`
7. `07_20260806_CKC 3.0 - Video 6 - Contracts_ Consideration_ and Trust Basics_0f44cef8.txt`
8. `08_20260806_CKC 3.0 - Video 7 - Driving Versus Traveling_72664d37.txt`
9. `09_20260806_CKC 3.0 - Video 8 - Enforcement and Litigation Introduction and Flowchart_81771878.txt`
10. `10_20260806_City of Glendale Round 3 - State Case Negotiable Instrument Complaint Breakdown _Vid 9 of CKC 3.0__8b74a13b.txt`
11. `11_20260806_City of Glendale Round 3 - First Discovery Packet Breakdown _Vid 10 of CKC 3.0__7b052aac.txt`
12. `12_20260806_CKC 3.0 - Video 11 - California Civil Procedure_ Code Overview and Discovery_c03e4b61.txt`
13. `13_20260806_CKC 3.0 - Video 12 - California Evidence Code Rules and Presumptions_41cbe397.txt`
14. `14_20260806_CKC 3.0 - Video 13 - Rules of Professional Conduct _BAR Card Slave Code__3a61ab9c.txt`
15. `15_20260806_CKC 3.0 - Video 14 - Judicial Canons_ Local Rules_ Appellate Rules_53a4934c.txt`
16. `16_20260807_CKC 3.0 - Video 15 - Final Thoughts_ Important Info and Goodbye_991a78e2.txt`

## What to produce

A structured summary of Brandon Joe's legal claims, arguments, and positions —
organized by topic, not chronologically, not per-episode. For each idea:

- **Claim** — one or two sentences stating what Brandon Joe argues, in his own
  terms (not softened or hedged unless he hedges it).
- **Support** — how he supports it (legal citation, procedural example, logical
  argument, etc.) — one line. Do not resolve or verify citations here (see below).
- **Source** — a Markdown link back to the transcript file the idea comes from,
  e.g. `[03](../TXT/03_20260806_CKC 3.0 - Video 2 - Legal Fictions and the Sole Proprietorship_f75ddbab.txt)`,
  immediately followed by a short locating quote (5-15 words, verbatim from the
  transcript) so a reader can Ctrl+F to the spot. If the same idea recurs across
  multiple episodes, give one link+quote per episode it appears in.

Group related ideas under topic headings inferred from what Brandon Joe actually
discusses (e.g. "Citizenship and legal-fiction theory", "Sole proprietorship and
the strawman", "UCC Article 3 and negotiable instruments", "Tax/IRS arguments",
"Driving vs. traveling", "Court procedure and the Glendale case litigation",
"Civil procedure and discovery", "Evidence code and presumptions", "Professional
conduct / BAR critique", "Judicial canons and appellate rules"). Do not force
topics that aren't present.

## Contradictions and inconsistencies

Call these out **inline, at the point of discovery** — not only in a final
appendix. When an idea contradicts or sits in tension with something Brandon Joe
said elsewhere (in an earlier or later episode, or earlier in the same one), add
a `> **Contradiction:**` blockquote directly under the entry, stating the two
positions and linking+quoting both sides the same way as above. Still include a
short roll-up list of all flagged contradictions at the end of the document for
quick scanning, but the primary flag belongs where the idea is presented.

## What to exclude

- Course-sales pitches, sign-up/ad-spend asides, show logistics.
- Small talk, banter, profanity-laden asides with no legal content.
- Restating a claim Brandon Joe repeats verbatim across episodes as a full new
  entry — note it once and list every episode it recurs in (each with its own
  link+quote), rather than duplicating the full write-up.

## Output

**One single monolithic Markdown file** —
`transcripts/summaries/BrandonJoe-ideas-CKC3.md` — covering all 16 transcripts,
organized by topic per "What to produce" above, with:

- A short intro noting the scope and source of the transcripts.
- The topic sections with claims, links/quotes, and inline contradiction flags.
- A final "Flagged contradictions" roll-up section.
- A final "Episodes by topic" cross-reference section.

## Notes

- Do not fact-check or editorialize on whether Brandon Joe's legal claims are
  correct — this is a summary of what he said, not a legal assessment.
- This pass is independent of citation extraction — do not attempt to resolve or
  verify legal citations here. Just capture what he cites (case names, statute
  numbers, etc.) as plain text in the **Support** line; the follow-up pass
  (`prompts/extract_citations.md`) is what resolves/links/registers those.
- Videos 10-11 (the two "City of Glendale Round 3" case breakdowns) are
  litigation-specific — expect concrete procedural claims and document
  references rather than general worldview claims; still topic-group them
  rather than treating them as a separate chronological aside.
