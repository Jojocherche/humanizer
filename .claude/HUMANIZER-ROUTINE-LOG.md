> CONSOLIDATED 2026-07-08 (v2.11.0 reconciliation): this file and `.routine/` were created independently by two parallel runs the same week and collided in a merge conflict. Going forward, `.routine/PLAYBOOK.md` + `.routine/sources-log.md` are canonical - this file's unique content (frontiers, rejected candidates, burned queries) has been copied into `.routine/sources-log.md`. Kept here, unmodified, for history. Do not add new rows here; add them to `.routine/` instead.

# ROUTINE STATE. WEEKLY HUMANIZER SKILL EVOLUTION. READ FIRST. APPEND ONLY. NEVER DELETE ROWS.

PURPOSE. this file = memory across weekly runs. goal: each run go DEEPER, not repeat old ground. read RUN LOG + COVERED + FRONTIERS before searching anything.

## RUN LOG (newest first)

- 2026-07-07 v2.10.0. upstream sync: 0 new commits (already current from last run). added #36 paragraph-cohesion uniformity, #37 syntactic/dependency uniformity, #38 redundant restatement. added SPANISH section (S1-S3, evidence weaker than French, flagged honestly). strengthened "what not to flag" with detector false-positive bias research (non-native speakers, neurodivergent writers). added Detector Landscape reference note (RAID, Pangram, tool list). REJECTED "round number bias" pattern candidate = no direct study found, do not re-add unless new evidence surfaces. discourse-coherence pattern = too weak (1 study, modest effect), NOT added, logged as frontier below. 4 parallel research agents used this run, ~180k tokens total.

- 2026-07-07 v2.9.0. added #34 hapax legomena/lexical diversity, #35 sentence burstiness. added FRENCH section (F1-F3). sources: StyloAI, PLOS One, Nature HSSC, ScienceDirect, ACM CODS-COMOD, Oxford DSH, arXiv evasion papers (2606.00392, 2601.08564).

## COVERED TOPICS (don't re-research from scratch — only extend or deepen)

- sentence-length burstiness (score 0.65-0.85 human, <0.30 AI), hapax legomena/lexical diversity
- em dash/en dash cut, rule of three, English AI-vocab list (delve/tapestry/testament/etc), copula avoidance, passive voice/subjectless fragments, elegant variation, false ranges, filler phrases, hedging, hyphenated-compound overuse, persuasive authority tropes, signposting openers, fragmented headers, diff-anchored writing, manufactured punchlines/staccato drama, aphorism formulas, conversational rhetorical openers (Honestly?/Look/Here's the thing)
- paragraph-level cohesion/architecture uniformity (#36) — source: arXiv 2603.21228
- syntactic/dependency-tree uniformity, right-branching sameness (#37) — sources: arXiv 2308.09067, arXiv 2412.10271, iScience 2026 (Cell Press)
- redundant restatement, idea repeated in different words later in doc (#38) — sources: arXiv 2210.08145, 2311.06440, 2403.00553, 2504.14218 (all on lexical/n-gram repetition, NOT semantic restatement — that specific angle is still under-studied, said so honestly in skill text)
- FRENCH: typography (guillemets, nbsp), AI vocab, anglicized calques/register
- SPANISH: typography (¿¡, «»  — WEAK evidence, inferred by analogy not confirmed), AI vocab (MODERATE — tech journalism only: genbeta.com, ecosistemastartup.com), calques (STRONGEST — general anglicism linguistics, not AI-specific: aplicar/soportar/realizar)
- detector landscape: GPTZero, Originality.ai, Copyleaks, Pangram, Winston AI, Turnitin, Sapling, ZeroGPT, Grammarly detector. RAID benchmark (arXiv 2405.07940, ACL 2024). Pangram tech report (arXiv 2402.14873, verified by U Chicago Booth, FP rate 0.01-0.1%).
- detector false-positive bias: non-native English writers (Liang et al arXiv 2304.02819 / PMC10382961, up to 61% flagged), neurodivergent/autistic writers (ResearchGate 394678751, U Nebraska-Lincoln)

## FRONTIERS NOT YET DONE (pick up next run, go deeper here first before finding brand new topics)

- discourse coherence / entity-grid AI vs human: only 1 weak source found (PMC11998594, Frontiers in Psychology 2025, modest effect). dig ACL Anthology + entity-grid detection papers specifically. do NOT add to skill until 2+ solid sources agree.
- round-number / numeric-vagueness bias ("over 50%" vs "53.7%"): UNCONFIRMED, no direct study. either find a real study that tests this exact claim, or drop the idea permanently — don't keep re-testing the same weak hypothesis every run.
- cross-lingual AI lexical shift paper, arXiv 2605.25358 ("AI-Associated Lexical Shifts Across 34 Languages"): hit 403 twice. try semantic scholar mirror, google cache, or author's personal site next run. could upgrade Spanish AND unlock German/Italian/Portuguese sections if readable.
- AuTexTification/IberLEF Spanish benchmark (arXiv 2309.11285) + MULTITuDE (arXiv 2310.13606): hit 403 on full text. retry via arxiv abstract page + semantic scholar. goal: extract concrete Spanish lexical-feature list to upgrade S2 from "moderate" to "strong" evidence.
- German, Italian, Portuguese sections: ZERO research done yet. natural next expansion after Spanish evidence is solid. same 3-part structure (typography, AI vocab, calques) probably transfers.
- formal paragraph-burstiness metric: no published metric name exists yet (unlike sentence burstiness which has a named 0.65-0.85 human range). either find one or note explicitly the skill's paragraph-uniformity heuristic is qualitative, not a named score.
- detector false-positive research: only 2 groups covered (non-native speakers, neurodivergent writers). check for dialect-specific bias (AAVE, regional English variants) and age-related bias (older/younger writers) in Q1 journals next.
- journal coverage still English-search-engine-biased (mostly arXiv + big English aggregators). next run: search SEPLN/Procesamiento del Lenguaje Natural directly for Spanish, and French Q1/Q2 linguistics journals directly (Langages, Journal of French Language Studies, Lidil) instead of relying on arXiv/English aggregators picking them up.
- test/benchmark SITES not yet deep-dived: only read ABOUT these tools (GPTZero, Originality.ai, Pangram etc), never actually ran text through them to sanity-check the skill's own Before/After examples. could add a manual verification step: run 2-3 skill Before/After pairs through 1-2 public detector free tiers, log the score delta, as a lightweight sanity check (NOT for evasion-tuning, just as a rough validity check on the skill's own claims).

## SEARCH QUERIES ALREADY BURNED (vary phrasing next run, don't rerun verbatim — waste of a search)

paragraph length burstiness AI detection 2025 2026 / syntactic complexity AI generated text stylometry / discourse coherence AI human text detection research / dependency parse AI text vs human text linguistics study / AI detector accuracy benchmark study 2026 / GPTZero Originality.ai Copyleaks academic evaluation / AI text detector false positive non-native speakers research / stylometric humanization LLM output 2026 arXiv / Pangram Winston AI detector research paper / AI generated Spanish text tells linguistics 2026 / ChatGPT Spanish overused vocabulary stylometric / anglicismos calcos IA texto generado español / revista Q1 Q2 español procesamiento lenguaje natural detección texto generado IA 2025 2026 / AI generated text round numbers bias linguistics / LLM numeric hedging vagueness text generation research 2025 2026 / LLM text redundancy repetition n-gram self-similarity detection research / AI generated text redundant restatement stylometric study 2025 2026

## RULE FOR NEXT RUN

1. git fetch upstream, merge if new commits (don't skip even if last 3 runs had 0 new commits — check anyway, it's cheap).
2. read this file fully before searching anything.
3. pick 1-2 items from FRONTIERS above to push deeper, PLUS 1 genuinely new angle not listed anywhere in COVERED or FRONTIERS.
4. minimum 2 new numbered patterns in SKILL.md, evidence-graded honestly (say when evidence is weak, don't pad with invented claims).
5. update THIS file: add new RUN LOG row, extend COVERED, extend/trim FRONTIERS, append burned queries. never delete old rows.
6. bump SKILL.md version by +0.1.0, changelog with date + full source list + explicit note on any candidate pattern REJECTED and why.
7. commit msg: feat(humanizer): weekly evolution vX.Y.Z - N new patterns added
