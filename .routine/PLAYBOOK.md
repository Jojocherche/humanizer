# PLAYBOOK — weekly humanizer evolution. machine instructions. no fluff.

READ THIS FIRST. THEN READ .routine/sources-log.md. THEN GO.

## RULE 0 — DO NOT RESTART FROM ZERO
sources-log.md = memory. skim table. skim watchlist. do NOT re-search
queries that already produced logged rows. widen instead. tick unchecked
watchlist boxes. add new boxes when you find a new venue.

## RULE 1 — BRANCH
work branch = whatever this session's designated branch is (check
`git branch --show-current` / harness system prompt). NEVER push straight
to main. NEVER open a PR unless user explicitly asked this run. if last
run's commit is still unmerged on the branch, say so in the recap — do not
silently pile up more unmerged commits without flagging it.

## RULE 1B — CHECK FOR A PARALLEL RUN BEFORE WRITING ANYTHING
this routine has run more than once in the same week on different branches
(one running session pushed straight to main, another ran on the PR branch,
neither saw the other — real incident, 2026-07-08, cost a merge conflict and
a manual reconciliation pass). Before starting research or writing:
```
git fetch origin main <this-branch>
git log --oneline main..<this-branch>          # branch ahead of main?
git log --oneline <this-branch>..main          # main ahead of branch? <- if non-empty, ANOTHER RUN HAPPENED
```
if main has commits the branch doesn't (and they look like this same routine
— check for the `feat(humanizer): weekly evolution` commit message pattern),
STOP before adding new content. Read what that commit already added, then
either (a) rebase/merge it in and build only genuinely new material on top,
or (b) if this run is a PR-babysitting/conflict-fix pass rather than a fresh
weekly run, reconcile the two sets of additions instead of writing a third.
Never assume you're the only session touching this repo this week.

## RULE 2 — SYNC UPSTREAM FIRST
```
git remote add upstream https://github.com/blader/humanizer.git   # ok if exists
git fetch upstream
git diff main upstream/main --stat
```
if upstream/main == main: no-op, say so in changelog, move on.
if upstream/main has new commits: merge them into main first (or note
divergence), THEN layer this run's additions on top. never overwrite
upstream's own pattern sections — merge, don't clobber.

## RULE 3 — READ CURRENT SKILL.md FULLY BEFORE WRITING ANYTHING
grep every `### N.` heading. grep every `### FN.` heading. build the "already
covered" list from the FILE, not from memory of last week's summary — the
file is ground truth, memory drifts.

## RULE 4 — RESEARCH. GO WIDER EACH RUN, NOT JUST NEWER.
minimum per run:
- 1 general web sweep (WebSearch) on current-year AI-detection + burstiness +
  stylometry + FR/EN/ES contrast queries
- 1 archive/venue NOT fully mined yet per sources-log.md watchlist (arXiv this
  run, ACL Anthology next, HAL after that, a specific Q2 francophone journal
  after that, etc. — rotate, don't repeat)
- citation-chase: pick the 1-2 heaviest-cited papers already logged, check
  "cited by" for newer papers building on them. cheap way to go forward in
  time without redoing broad search.
- if budget/time allows: 1 detector/test site spot-check (run actual SKILL.md
  Before/After pairs through a public AI-detector UI if reachable, note
  whether the "After" text scores as human — this is empirical, not just
  literature review. log result even if inconclusive.)

reject a candidate pattern if:
- it's just a rename of an existing numbered section (check RULE 3 list)
- it only works as a detector trick, not a readability improvement (out of
  scope per "What this skill does not do")
- no concrete Before/After is writable from it

## RULE 5 — WRITE. ADD ONLY. NEVER DELETE.
- bump version: PATCH-level bugfix = z++, new pattern(s) = y++, structural
  overhaul = x++. weekly pattern additions = y++ almost always.
  (v2.9.0 -> v2.10.0 -> v2.11.0 ...)
- minimum 2 new patterns per run. more if research supports it. no ceiling.
- every new pattern needs: Words to watch (if lexical) OR structural
  description, Problem 1-2 sentences, Before block, After block.
- update YAML frontmatter `version:` field AND `description:` line if new
  pattern categories are broad enough to name-drop there.
- append Changelog entry at bottom: version, date, what got added, full
  source list with venue tags (arXiv / Q1 journal name / Q2 journal name /
  ACL Anthology / HAL / blog).
- update .routine/sources-log.md: new rows in the table, tick/add watchlist
  boxes.

## RULE 6 — COMMIT MESSAGE FORMAT (do not deviate)
```
feat(humanizer): weekly evolution vX.Y.Z - N new patterns added
```
body: 2-4 lines, what got added, one line noting which watchlist items got
newly explored this run (so the commit log itself is a second memory trail).

## RULE 7 — RECAP FOR THE HUMAN
after push, notify. plain language, not caveman. lead with: version bump,
pattern count, anything that needs a human decision (unmerged backlog on the
branch, a broken upstream merge, a source that contradicts an existing
pattern). do not notify if literally nothing changed.

## SELF-IMPROVEMENT LOOP
each run, before finishing, add one line to "## Meta-notes for next run" below
— something you learned about HOW to research or write this thing faster/
better, not WHAT you found. this file should get sharper every week; the
source log gets wider every week. two different kinds of memory, don't mix
them.

## Meta-notes for next run
- (run 2, 2026-07-07) sources-log.md didn't exist before this run — v2.9.0's
  14 sources were only visible inside SKILL.md's changelog. seeded the log
  retroactively this run. from now on, always update the log in the same
  commit as the SKILL.md changelog so they can't drift apart.
- (run 2, 2026-07-07) checking `git log --oneline main..<branch>` and
  `list_pull_requests` up front caught a real problem: v2.9.0 was pushed but
  never merged/PR'd, so it was invisible to anyone not reading this branch
  directly. always run that check before starting new work, and surface it
  to the human — don't just quietly stack another commit on an already-stuck
  branch.
- (run 2, 2026-07-07) delegating the research fan-out to one general-purpose
  agent with an explicit "here's the 14 sources already cited, here's the 35
  pattern topics already covered, don't repeat, go wider" prompt worked well:
  it came back with 11 solid non-overlapping sources plus 5 queued leads in
  one pass, ~57 tool calls, no duplicate ground. Keep front-loading the
  already-covered list into the research prompt every run instead of letting
  the agent rediscover it — it's the single biggest lever against wasted
  search.
- (run 2, 2026-07-07) one source this run (cours-ndrc.fr, a non-academic
  French blog) made a specific frequency claim ("~23% of AI intros") citing
  an unverifiable "MIT study." Used the pattern, dropped the stat, flagged it
  LOW CONFIDENCE in sources-log.md. Rule going forward: any stat from a
  non-peer-reviewed source gets flagged in the log and never gets quoted as
  a hard number in SKILL.md, only the qualitative pattern.
- (run 2, 2026-07-07) still haven't done a direct venue browse of HAL, TAL,
  Corpus, or Langages — francophone-specific gaps keep getting filled via
  press coverage (The Conversation, Siècle Digital) of academic work instead
  of the journals themselves. Next run: spend the francophone-archive slot
  on HAL directly, not another general web sweep.
- (reconciliation pass, 2026-07-08) two sessions ran this same weekly routine
  in the same week without either knowing about the other: one pushed
  straight to main, one worked on the PR branch. Both wrote genuinely good,
  non-overlapping patterns, but both called themselves "v2.10.0," both
  invented their own separate self-improvement scaffold (`.routine/` vs
  `.claude/HUMANIZER-ROUTINE-LOG.md`), and the PR that was supposed to bring
  them together showed up conflicted. Fixed by merging both pattern sets
  into v2.11.0, renumbering to avoid collisions, and consolidating the two
  scaffolds into this one. Added RULE 1B above so the next run checks for
  this before writing anything instead of after. Lesson: "don't repeat past
  work" only works if there's exactly one past to check against — assume
  there might be two.
