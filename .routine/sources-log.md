# Humanizer weekly-evolution: source registry

Machine-readable-ish log of every academic/web source already mined by the
weekly routine, so future runs search FORWARD instead of re-finding the same
14-20 links every time. Append only. Never delete a row — mark it `stale` in
notes if a link dies, don't remove the record (it still proves the ground was
covered).

## How to use this file (future run)

1. Before searching, skim the URLs already in this table. Do not re-run the
   same query phrasing that already produced them.
2. After searching, add one row per NEW source actually cited in that week's
   SKILL.md changelog.
3. Bump the "Journals/archives watchlist" checklist below: tick what you
   checked this run even if it produced nothing new (so next run doesn't
   re-check a dry well too soon), and add any new archive/journal/detector
   site you discovered mid-search.
4. Widen, don't repeat: each run should hit at least one source TYPE not hit
   last run (e.g. run 1 = arXiv + general web; run 2 = add ACL Anthology +
   HAL; run 3 = add a specific Q2 francophone journal; etc).

## Sources cited so far

| Run (version) | Date | Source | Venue/type | Topic |
|---|---|---|---|---|
| v2.9.0 | 2026-06-30 | StyloAI: Distinguishing AI-Generated Content with Stylometric Analysis — arxiv.org/html/2405.10129v1 | arXiv | stylometric features |
| v2.9.0 | 2026-06-30 | Distinguishing AI-Generated and Human-Written Text Through Psycholinguistic Analysis — arxiv.org/html/2505.01800v1 | arXiv | psycholinguistics |
| v2.9.0 | 2026-06-30 | Stylometric detection of AI-generated texts — academic.oup.com/dsh/.../fqag064 | Digital Scholarship in the Humanities (Q1, Oxford) | stylometry |
| v2.9.0 | 2026-06-30 | Stylometry can reveal AI authorship, but humans struggle — journals.plos.org/plosone/.../pone.0335369 | PLOS ONE (Q1) | stylometry / human judgment |
| v2.9.0 | 2026-06-30 | Stylometric comparisons of human vs AI-generated creative writing — nature.com/articles/s41599-025-05986-3 | Nature HSSC (Q1) | creative writing stylometry |
| v2.9.0 | 2026-06-30 | Stylometry recognizes human and LLM-generated texts in short samples — sciencedirect.com/.../S0957417425026181 | ScienceDirect / Expert Systems w/ Applications (Q1) | short-sample detection |
| v2.9.0 | 2026-06-30 | Text Authorship Attribution: Stylometric Insights — dl.acm.org/doi/10.1145/3703323.3703712 | ACM CODS-COMOD 2025 | authorship attribution |
| v2.9.0 | 2026-06-30 | What Is Burstiness in AI Detection? — thehumanizeai.pro | industry blog | burstiness explainer |
| v2.9.0 | 2026-06-30 | How AI Detectors Work: Perplexity & Burstiness Explained — gptzero.me | industry blog | perplexity/burstiness |
| v2.9.0 | 2026-06-30 | Comparative linguistic analysis framework of human-written vs. machine-generated text — tandfonline.com/.../09540091.2025.2507183 | Tandfonline (Q2) | comparative linguistics |
| v2.9.0 | 2026-06-30 | Detector-Evasive LLM Paraphrasing via Constrained Policy Optimization — arxiv.org/pdf/2606.00392 | arXiv | detector evasion (scope note only) |
| v2.9.0 | 2026-06-30 | MASH: Evading Black-Box AI-Generated Text Detectors via Style Humanization — arxiv.org/pdf/2601.08564 | arXiv | detector evasion (scope note only) |
| v2.9.0 | 2026-06-30 | Differences between French and English — human.libretexts.org | textbook | FR/EN contrast |
| v2.9.0 | 2026-06-30 | Written English Vs. Written French: A Comparison — italki.com | blog | FR/EN contrast |

<!-- v2.10.0 rows appended below by this run -->

## Journals / archives watchlist (tick as explored, add new ones as found)

Academic archives:
- [x] arXiv cs.CL (general search) — run 1, run 2
- [ ] ACL Anthology (aclanthology.org) — direct venue browse, not just Google-surfaced arXiv preprints
- [ ] HAL (hal.science) — francophone open archive
- [ ] Semantic Scholar API/browse for citation-forward search from the papers above (who cited StyloAI, MASH, etc. — citation chaining finds newer work fast)
- [ ] Google Scholar "cited by" chase on the 3 most load-bearing papers already logged

Q1/Q2 journals not yet directly browsed (only reached via general search so far):
- [ ] Computational Linguistics (MIT Press, Q1)
- [ ] Language Resources and Evaluation (Springer, Q1/Q2)
- [ ] Journal of Quantitative Linguistics (Q2)
- [ ] Corpus (francophone, Q2) — French corpus linguistics
- [ ] TAL — Traitement Automatique des Langues (francophone, ATALA)
- [ ] Langages (francophone, Q2, linguistics)
- [ ] Digital Scholarship in the Humanities — mined once (v2.9.0), re-check for newer issues each quarter, not every week

Detector/test sites worth spot-checking behavior on (not academic, but useful ground truth):
- [ ] GPTZero (mined for explainer content only so far, not tested against skill output)
- [ ] Originality.ai blog/research page
- [ ] Pangram Labs research page (academic-leaning AI detection startup, publishes methodology notes)
- [ ] Binoculars / DetectGPT paper lineage (zero-shot detection methods — useful for "what detectors actually measure" grounding)
