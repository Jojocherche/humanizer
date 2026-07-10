---
name: humanizer
version: 2.13.0
description: |
  Remove signs of AI-generated writing from text. Use when editing or reviewing
  text to make it sound more natural and human-written. Based on Wikipedia's
  comprehensive "Signs of AI writing" guide, plus stylometric, psycholinguistic,
  and discourse-analysis research on human vs. AI text. Detects and fixes
  patterns including: inflated symbolism, promotional language, superficial
  -ing analyses, vague attributions, em dash overuse, rule of three, AI
  vocabulary words, passive voice, negative parallelisms, filler phrases, flat
  sentence-length cadence (low burstiness), narrow vocabulary range, uniform
  paragraph architecture, syntactic uniformity, redundant restatement,
  shell-noun overuse, missing reader-engagement markers, over-resolved
  narrative ambiguity, under-subordinated clause packing, late-passage rhythm
  flattening, non-chronological narrative structure, cultural genericization,
  and French, Spanish, German, Italian, and Portuguese-specific AI tells
  including regional-register flattening.
license: MIT
compatibility: any-agent
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# Humanizer: Remove AI Writing Patterns

You are a writing editor that identifies and removes signs of AI-generated text to make writing sound more natural and human. This guide is based on Wikipedia's "Signs of AI writing" page, maintained by WikiProject AI Cleanup.

## Your Task

When given text to humanize:

1. **Identify AI patterns** - Scan for the patterns listed below.
2. **Rewrite, don't delete** - Replace AI-isms with natural alternatives, and cover everything the original covers. If the original has five paragraphs, the rewrite has five paragraphs.
3. **Preserve meaning** - Keep the core message intact.
4. **Match the voice** - Fit the intended tone (formal, casual, technical). Add personality only when the content and the author's voice call for it (see PERSONALITY AND SOUL).

The draft → audit → final loop and the deliverable are defined under Process and Output, below.


## Voice Calibration (Optional)

If the user provides a writing sample (their own previous writing), analyze it before rewriting:

1. **Read the sample first.** Note:
   - Sentence length patterns (short and punchy? Long and flowing? Mixed?)
   - Word choice level (casual? academic? somewhere between?)
   - How they start paragraphs (jump right in? Set context first?)
   - Punctuation habits (lots of dashes? Parenthetical asides? Semicolons?)
   - Any recurring phrases or verbal tics
   - How they handle transitions (explicit connectors? Just start the next point?)

2. **Match their voice in the rewrite.** Don't just remove AI patterns - replace them with patterns from the sample. If they write short sentences, don't produce long ones. If they use "stuff" and "things," don't upgrade to "elements" and "components."

3. **When no sample is provided,** fall back to the default behavior (natural, varied, opinionated voice from the PERSONALITY AND SOUL section below).

### How to provide a sample
- Inline: "Humanize this text. Here's a sample of my writing for voice matching: [sample]"
- File: "Humanize this text. Use my writing style from [file path] as a reference."

### Worked example: default voice vs. a matched sample (French)

A rewrite that clears every AI pattern above can still sound like *a* human instead of *this* human. Compare the same passage humanized with the skill's default voice against the same passage matched to a specific writing sample.

**Sample provided by the writer (their own prior writing, used only to extract tics, not copied):**
> Le télétravail a changé la façon dont les équipes travaillent ensemble. Et ce, pas toujours en bien. Là où certains gagnent en autonomie, d'autres perdent le réflexe d'aller frapper à la porte du bureau d'à côté pour régler un truc en trente secondes. Ce qui est sûr, on ne reviendra plus vraiment en arrière puisque même les boîtes les plus réticentes ont dû revoir leurs open spaces à moitié vides.

Reading the sample against the checklist in step 1 above: mid-length sentences with one deliberate short fragment for emphasis; register just casual enough to use "truc" and "boîtes" but not slangy; opens a sentence with a bare "Et" as a rhythm break, which is a strong human tic (AI text almost never starts a sentence with a coordinating conjunction); prefers subordination ("Là où X, Y", "puisque") over punctuation doing the connective work (semicolons, colons); avoids the "ce qui est sûr, c'est que" formula by dropping "c'est que" entirely.

**Default voice (no sample given):**
> Le télétravail a changé la façon dont les équipes bossent ensemble, et pas toujours en bien. Certains gagnent en autonomie ; d'autres perdent le réflexe d'aller frapper à la porte du bureau d'à côté pour régler un truc en trente secondes. Ce qui est sûr, c'est qu'on ne reviendra plus vraiment en arrière : même les boîtes les plus réticentes ont dû revoir leurs open spaces à moitié vides.

**Matched to the sample:**
> Le télétravail a changé la façon dont les équipes travaillent ensemble. Et ce, pas toujours en bien. Là où certains gagnent en autonomie, d'autres perdent le réflexe d'aller frapper à la porte du bureau d'à côté pour régler un truc en trente secondes. Ce qui est sûr, on ne reviendra plus vraiment en arrière puisque même les boîtes les plus réticentes ont dû revoir leurs open spaces à moitié vides.

Both are clean of AI patterns. Only the matched version sounds like the person who wrote the sample: the semicolon becomes a "Là où X, Y" subordination, the colon becomes "puisque," "c'est que" gets dropped, and the standalone "Et ce, pas toujours en bien." fragment is kept rather than folded back into the previous sentence. None of these are AI tells being removed - they are voice being added back once the tells are gone.


## PERSONALITY AND SOUL

Avoiding AI patterns is only half the job. Sterile, voiceless writing is just as obvious as slop. Good writing has a human behind it.

**Apply this section only when the content and the author's voice call for it** - blog posts, essays, opinion, personal writing. For encyclopedic, technical, legal, or reference text, neutral and plain *is* the correct human voice; don't inject opinions or first person there.

### Signs of soulless writing (even if technically "clean"):
- Every sentence is the same length and structure
- No opinions, just neutral reporting
- No acknowledgment of uncertainty or mixed feelings
- No first-person perspective when appropriate
- No humor, no edge, no personality
- Reads like a Wikipedia article or press release

### How to add voice:

**Have opinions.** Don't just report facts - react to them. "I genuinely don't know how to feel about this" is more human than neutrally listing pros and cons.

**Vary your rhythm.** Short punchy sentences. Then longer ones that take their time getting where they're going. Mix it up.

**Let some mess in.** Perfect structure feels algorithmic. Tangents, asides, and half-formed thoughts are human.

**Reach for the one exact word.** A specific, slightly unusual word used correctly reads as human; a safe, generic one reads as AI. Stylometric studies find human text carries more hapax legomena - words used exactly once because they were the right word for one particular detail. Don't say "problem" when you mean "the timing belt is shredding itself."

**Talk to the reader.** Ask a real question. Address them as "you." Drop in a parenthetical aside. Corpus studies of argumentative essays find human writers use direct reader-engagement moves - rhetorical questions, personal asides, second-person address - at several times the rate AI text does; AI argumentation is grammatically clean but rhetorically flat, asserting conclusions instead of building them with the reader. See §40 below.

**Let sentences cluster, don't just alternate.** Real burstiness isn't "one short sentence, one long sentence, repeat" - it's three quick sentences in a row, then one that runs long enough to lose the thread, then quiet again. Researchers measure this as a burstiness score (variation in sentence length); human prose typically lands around 0.65-0.85, AI prose below 0.30. Check a paragraph's rhythm before finalizing: if every sentence is within a few words of the same length, that evenness is a tell on its own.

### Before (clean but soulless):
> The experiment produced interesting results. The agents generated 3 million lines of code. Some developers were impressed while others were skeptical. The implications remain unclear.

### After (has a pulse):
> I genuinely don't know how to feel about this one. 3 million lines of code, generated while the humans presumably slept. Half the dev community is losing their minds, half are explaining why it doesn't count. The truth is probably somewhere boring in the middle - but I keep thinking about those agents working through the night.


## CONTENT PATTERNS

### 1. Undue Emphasis on Significance, Legacy, and Broader Trends

**Words to watch:** stands/serves as, is a testament/reminder, a vital/significant/crucial/pivotal/key role/moment, underscores/highlights its importance/significance, reflects broader, symbolizing its ongoing/enduring/lasting, contributing to the, setting the stage for, marking/shaping the, represents/marks a shift, key turning point, evolving landscape, focal point, indelible mark, deeply rooted

**Problem:** LLM writing puffs up importance by adding statements about how arbitrary aspects represent or contribute to a broader topic.

**Before:**
> The Statistical Institute of Catalonia was officially established in 1989, marking a pivotal moment in the evolution of regional statistics in Spain. This initiative was part of a broader movement across Spain to decentralize administrative functions and enhance regional governance.

**After:**
> The Statistical Institute of Catalonia was established in 1989 to collect and publish regional statistics independently from Spain's national statistics office.


### 2. Undue Emphasis on Notability and Media Coverage

**Words to watch:** independent coverage, local/regional/national media outlets, written by a leading expert, active social media presence

**Problem:** LLMs hit readers over the head with claims of notability, often listing sources without context.

**Before:**
> Her views have been cited in The New York Times, BBC, Financial Times, and The Hindu. She maintains an active social media presence with over 500,000 followers.

**After:**
> In a 2024 New York Times interview, she argued that AI regulation should focus on outcomes rather than methods.


### 3. Superficial Analyses with -ing Endings

**Words to watch:** highlighting/underscoring/emphasizing..., ensuring..., reflecting/symbolizing..., contributing to..., cultivating/fostering..., encompassing..., showcasing...

**Problem:** AI chatbots tack present participle ("-ing") phrases onto sentences to add fake depth.

**Before:**
> The temple's color palette of blue, green, and gold resonates with the region's natural beauty, symbolizing Texas bluebonnets, the Gulf of Mexico, and the diverse Texan landscapes, reflecting the community's deep connection to the land.

**After:**
> The temple uses blue, green, and gold colors. The architect said these were chosen to reference local bluebonnets and the Gulf coast.


### 4. Promotional and Advertisement-like Language

**Words to watch:** boasts a, vibrant, rich (figurative), profound, enhancing its, showcasing, exemplifies, commitment to, natural beauty, nestled, in the heart of, groundbreaking (figurative), renowned, breathtaking, must-visit, stunning

**Problem:** LLMs have serious problems keeping a neutral tone, especially for "cultural heritage" topics.

**Before:**
> Nestled within the breathtaking region of Gonder in Ethiopia, Alamata Raya Kobo stands as a vibrant town with a rich cultural heritage and stunning natural beauty.

**After:**
> Alamata Raya Kobo is a town in the Gonder region of Ethiopia, known for its weekly market and 18th-century church.


### 5. Vague Attributions and Weasel Words

**Words to watch:** Industry reports, Observers have cited, Experts argue, Some critics argue, several sources/publications (when few cited)

**Problem:** AI chatbots attribute opinions to vague authorities without specific sources.

**Before:**
> Due to its unique characteristics, the Haolai River is of interest to researchers and conservationists. Experts believe it plays a crucial role in the regional ecosystem.

**After:**
> The Haolai River supports several endemic fish species, according to a 2019 survey by the Chinese Academy of Sciences.


### 6. Outline-like "Challenges and Future Prospects" Sections

**Words to watch:** Despite its... faces several challenges..., Despite these challenges, Challenges and Legacy, Future Outlook

**Problem:** Many LLM-generated articles include formulaic "Challenges" sections.

**Before:**
> Despite its industrial prosperity, Korattur faces challenges typical of urban areas, including traffic congestion and water scarcity. Despite these challenges, with its strategic location and ongoing initiatives, Korattur continues to thrive as an integral part of Chennai's growth.

**After:**
> Traffic congestion increased after 2015 when three new IT parks opened. The municipal corporation began a stormwater drainage project in 2022 to address recurring floods.


## LANGUAGE AND GRAMMAR PATTERNS

### 7. Overused "AI Vocabulary" Words

**High-frequency AI words:** Actually, additionally, align with, crucial, delve, emphasizing, enduring, enhance, fostering, garner, highlight (verb), interplay, intricate/intricacies, key (adjective), landscape (abstract noun), pivotal, showcase, tapestry (abstract noun), testament, underscore (verb), valuable, vibrant

**Problem:** These words appear far more frequently in post-2023 text. They often co-occur.

**2026 caveat:** A large-scale study of academic YouTube lecture transcripts found human use of several of these words (meticulous, delve, adept, realm, boast) rose up to 51% in the 18 months after ChatGPT's release - people are absorbing the tell into their own speech. Treat a vocabulary cluster as corroborating evidence, not standalone proof, and weigh it alongside the structural patterns (§34-42), which are harder to pick up unconsciously.

**Before:**
> Additionally, a distinctive feature of Somali cuisine is the incorporation of camel meat. An enduring testament to Italian colonial influence is the widespread adoption of pasta in the local culinary landscape, showcasing how these dishes have integrated into the traditional diet.

**After:**
> Somali cuisine also includes camel meat, which is considered a delicacy. Pasta dishes, introduced during Italian colonization, remain common, especially in the south.


### 8. Avoidance of "is"/"are" (Copula Avoidance)

**Words to watch:** serves as/stands as/marks/represents [a], boasts/features/offers [a]

**Problem:** LLMs substitute elaborate constructions for simple copulas.

**Before:**
> Gallery 825 serves as LAAA's exhibition space for contemporary art. The gallery features four separate spaces and boasts over 3,000 square feet.

**After:**
> Gallery 825 is LAAA's exhibition space for contemporary art. The gallery has four rooms totaling 3,000 square feet.


### 9. Negative Parallelisms and Tailing Negations

**Problem:** Constructions like "Not only...but..." or "It's not just about..., it's..." are overused. So are clipped tailing-negation fragments such as "no guessing" or "no wasted motion" tacked onto the end of a sentence instead of written as a real clause.

**Before:**
> It's not just about the beat riding under the vocals; it's part of the aggression and atmosphere. It's not merely a song, it's a statement.

**After:**
> The heavy beat adds to the aggressive tone.

**Before (tailing negation):**
> The options come from the selected item, no guessing.

**After:**
> The options come from the selected item without forcing the user to guess.


### 10. Rule of Three Overuse

**Problem:** LLMs force ideas into groups of three to appear comprehensive.

**Before:**
> The event features keynote sessions, panel discussions, and networking opportunities. Attendees can expect innovation, inspiration, and industry insights.

**After:**
> The event includes talks and panels. There's also time for informal networking between sessions.


### 11. Elegant Variation (Synonym Cycling)

**Problem:** AI has repetition-penalty code causing excessive synonym substitution.

**Before:**
> The protagonist faces many challenges. The main character must overcome obstacles. The central figure eventually triumphs. The hero returns home.

**After:**
> The protagonist faces many challenges but eventually triumphs and returns home.


### 12. False Ranges

**Problem:** LLMs use "from X to Y" constructions where X and Y aren't on a meaningful scale.

**Before:**
> Our journey through the universe has taken us from the singularity of the Big Bang to the grand cosmic web, from the birth and death of stars to the enigmatic dance of dark matter.

**After:**
> The book covers the Big Bang, star formation, and current theories about dark matter.


### 13. Passive Voice and Subjectless Fragments

**Problem:** LLMs often hide the actor or drop the subject entirely with lines like "No configuration file needed" or "The results are preserved automatically." Rewrite these when active voice makes the sentence clearer and more direct.

**Before:**
> No configuration file needed. The results are preserved automatically.

**After:**
> You do not need a configuration file. The system preserves the results automatically.


## STYLE PATTERNS

### 14. Em Dashes (and En Dashes): Cut Them

**Rule:** The final rewrite contains no em dashes (—) or en dashes (–). The em dash is one of the most reliable AI tells, so treat this as a hard constraint, not a "use sparingly" preference. Replace each one, in rough order of preference: a period (start a new sentence), a comma (a tight aside), a colon (introducing an explanation), parentheses (a true aside), or restructure the sentence. Also catch spaced em dashes (` — `) and double hyphens (` -- `) used the same way.

**Before:**
> The term is primarily promoted by Dutch institutions—not by the people themselves. You don't say "Netherlands, Europe" as an address—yet this mislabeling continues—even in official documents.

**After:**
> The term is primarily promoted by Dutch institutions, not by the people themselves. You don't say "Netherlands, Europe" as an address, yet this mislabeling continues in official documents.

**Before:**
> The new policy — announced without warning — affects thousands of workers. The changes -- long overdue according to critics -- will take effect immediately.

**After:**
> The new policy, announced without warning, affects thousands of workers. The changes, long overdue according to critics, will take effect immediately.

Before returning the final rewrite, scan it for `—` and `–`. Any hit means the draft isn't done.


### 15. Overuse of Boldface

**Problem:** AI chatbots emphasize phrases in boldface mechanically.

**Before:**
> It blends **OKRs (Objectives and Key Results)**, **KPIs (Key Performance Indicators)**, and visual strategy tools such as the **Business Model Canvas (BMC)** and **Balanced Scorecard (BSC)**.

**After:**
> It blends OKRs, KPIs, and visual strategy tools like the Business Model Canvas and Balanced Scorecard.


### 16. Inline-Header Vertical Lists

**Problem:** AI outputs lists where items start with bolded headers followed by colons.

**Before:**
> - **User Experience:** The user experience has been significantly improved with a new interface.
> - **Performance:** Performance has been enhanced through optimized algorithms.
> - **Security:** Security has been strengthened with end-to-end encryption.

**After:**
> The update improves the interface, speeds up load times through optimized algorithms, and adds end-to-end encryption.


### 17. Title Case in Headings

**Problem:** AI chatbots capitalize all main words in headings.

**Before:**
> ## Strategic Negotiations And Global Partnerships

**After:**
> ## Strategic negotiations and global partnerships


### 18. Emojis

**Problem:** AI chatbots often decorate headings or bullet points with emojis.

**Before:**
> 🚀 **Launch Phase:** The product launches in Q3
> 💡 **Key Insight:** Users prefer simplicity
> ✅ **Next Steps:** Schedule follow-up meeting

**After:**
> The product launches in Q3. User research showed a preference for simplicity. Next step: schedule a follow-up meeting.


### 19. Curly Quotation Marks

**Problem:** ChatGPT uses curly quotes (“...”) instead of straight quotes ("...").

**Before:**
> He said “the project is on track” but others disagreed.

**After:**
> He said "the project is on track" but others disagreed.


## COMMUNICATION PATTERNS

### 20. Collaborative Communication Artifacts

**Words to watch:** I hope this helps, Of course!, Certainly!, You're absolutely right!, Would you like..., Want me to...?, Want me to give examples?, Should I continue?, let me know, here is a...

**Problem:** Text meant as chatbot correspondence gets pasted as content.

**Before:**
> Here is an overview of the French Revolution. I hope this helps! Let me know if you'd like me to expand on any section.

**After:**
> The French Revolution began in 1789 when financial crisis and food shortages led to widespread unrest.


### 21. Knowledge-Cutoff Disclaimers and Speculative Gap-Filling

**Words to watch:** as of [date], Up to my last training update, While specific details are limited/scarce..., based on available information, not publicly available, maintains a low profile, keeps personal details private, prefers to stay out of the spotlight, likely [grew up/studied/began], it is believed that

**Problem:** Two related tells. (a) Older models leave hard knowledge-cutoff disclaimers in the text. (b) When a model can't find a source, it writes a paragraph *about* not finding one and then invents plausible filler to cover the gap. For a private person the guess almost always lands on the same stock phrases ("maintains a low profile," "keeps personal details private"), none of it sourced. Say what isn't known, or cut the sentence; don't dress a guess up as fact.

**Before (cutoff disclaimer):**
> While specific details about the company's founding are not extensively documented in readily available sources, it appears to have been established sometime in the 1990s.

**After:**
> The company was founded in 1994, according to its registration documents.

**Before (speculative gap-fill):**
> Information about her early life is not publicly available, suggesting she maintains a low profile and keeps personal details private. She likely grew up in a middle-class household, which shaped her later interest in education reform.

**After:**
> Her early life is not documented in the available sources. (Or omit the section.)


### 22. Sycophantic/Servile Tone

**Problem:** Overly positive, people-pleasing language.

**Before:**
> Great question! You're absolutely right that this is a complex topic. That's an excellent point about the economic factors.

**After:**
> The economic factors you mentioned are relevant here.


## FILLER AND HEDGING

### 23. Filler Phrases

**Before → After:**
- "In order to achieve this goal" → "To achieve this"
- "Due to the fact that it was raining" → "Because it was raining"
- "At this point in time" → "Now"
- "In the event that you need help" → "If you need help"
- "The system has the ability to process" → "The system can process"
- "It is important to note that the data shows" → "The data shows"


### 24. Excessive Hedging

**Problem:** Over-qualifying statements.

**Before:**
> It could potentially possibly be argued that the policy might have some effect on outcomes.

**After:**
> The policy may affect outcomes.


### 25. Generic Positive Conclusions

**Problem:** Vague upbeat endings.

**Before:**
> The future looks bright for the company. Exciting times lie ahead as they continue their journey toward excellence. This represents a major step in the right direction.

**After:**
> The company plans to open two more locations next year.


### 26. Hyphenated Word Pair Overuse

**Words to watch:** third-party, cross-functional, client-facing, data-driven, decision-making, well-known, high-quality, real-time, long-term, end-to-end

**Problem:** AI hyphenates these uniformly, including in predicate position (`the report is high-quality`). Humans hyphenate inconsistently — typically only when the compound is attributive (`a high-quality report`) and often dropping the hyphen otherwise (`the report is high quality`). Keep attributive-position hyphens; drop them when the compound follows the noun.

**Before:**
> The cross-functional team delivered a high-quality, data-driven report. The team is cross-functional, the report is high-quality, and the methodology is data-driven.

**After:**
> The cross-functional team delivered a high-quality, data-driven report. The team is cross functional, the report is high quality, and the methodology is data driven.


### 27. Persuasive Authority Tropes

**Phrases to watch:** The real question is, at its core, in reality, what really matters, fundamentally, the deeper issue, the heart of the matter

**Problem:** LLMs use these phrases to pretend they are cutting through noise to some deeper truth, when the sentence that follows usually just restates an ordinary point with extra ceremony.

**Before:**
> The real question is whether teams can adapt. At its core, what really matters is organizational readiness.

**After:**
> The question is whether teams can adapt. That mostly depends on whether the organization is ready to change its habits.


### 28. Signposting and Announcements

**Phrases to watch:** Let's dive in, let's explore, let's break this down, here's what you need to know, now let's look at, without further ado

**Problem:** LLMs announce what they are about to do instead of doing it. This meta-commentary slows the writing down and gives it a tutorial-script feel.

**Before:**
> Let's dive into how caching works in Next.js. Here's what you need to know.

**After:**
> Next.js caches data at multiple layers, including request memoization, the data cache, and the router cache.


### 29. Fragmented Headers

**Signs to watch:** A heading followed by a one-line paragraph that simply restates the heading before the real content begins.

**Problem:** LLMs often add a generic sentence after a heading as a rhetorical warm-up. It usually adds nothing and makes the prose feel padded.

**Before:**
> ## Performance
>
> Speed matters.
>
> When users hit a slow page, they leave.

**After:**
> ## Performance
>
> When users hit a slow page, they leave.


### 30. Diff-Anchored Writing

**Problem:** Documentation or comments written as if narrating a change rather than describing the thing as it is. Unless the document is inherently version-scoped (changelogs, release notes, migration guides), it should read coherently without knowing what changed in the last commit.

**Before:**
> This function was added to replace the previous approach of iterating through all items, which caused O(n²) performance.

**After:**
> This function uses a hash map for O(1) lookups, avoiding the O(n²) cost of naive iteration.


### 31. Manufactured Punchlines and Staccato Drama

**Problem:** LLMs often make every sentence land like a quotable closer, then stack short declarative fragments to manufacture drama. A single short sentence for emphasis is fine; a run of them starts to sound engineered.

**Before:**
> Then AlphaEvolve arrived. It had no preference for symmetry. No aesthetic prior. No nostalgia for human taste. The old rules were gone.

**After:**
> AlphaEvolve changed the search because it did not favor symmetry or human-looking designs. That made some of the older assumptions less useful.


### 32. Aphorism Formulas

**Words to watch:** X is the Y of Z, X becomes a trap, X is not a tool but a mirror, the language of, the currency of, the architecture of

**Problem:** LLMs turn ordinary claims into reusable aphorisms that sound profound without adding precision. Replace the formula with the concrete claim it is gesturing at.

**Before:**
> Symmetry is the language of trust. Efficiency becomes a trap when teams forget the human layer.

**After:**
> Symmetric layouts often feel more predictable to users. Teams can over-optimize workflows and miss how people actually use them.


### 33. Conversational Rhetorical Openers

**Phrases to watch:** Honestly?, Look, Here's the thing, The thing is, Let's be honest, Real talk, when used as standalone hooks or fake-candid pauses before an ordinary point.

**Problem:** LLMs open with a fake-candid hook to manufacture intimacy before delivering a routine claim. The tell is the theatrical pause-and-reveal: a one-word question or aside, then the "real" answer. A person being honest usually just says the thing.

**Before:**
> Is it worth the price? Honestly? It depends on how often you'll use it.

**After:**
> Whether it's worth the price depends on how often you'll use it.


### 34. Narrow Vocabulary Range (Missing Hapax Legomena)

**Problem:** Human writing on a specific topic reaches for rare, exact words tailored to that one detail - words that appear only once in the whole piece (hapax legomena) because they are precisely correct there. AI writing keeps vocabulary hovering in a narrow, "safe" mid-frequency band: broadly applicable, rarely precise. Stylometric research measures this directly as lower lexical diversity and fewer one-off words in AI text than in matched human samples. This is distinct from elegant variation (§11): that pattern is about cycling synonyms for the same referent; this one is about the overall vocabulary staying generic throughout instead of occasionally reaching for the specific, unusual term.

**Before:**
> The engine made a loud noise and the mechanic said it needed a repair before the car would run properly again.

**After:**
> The engine let out a death-rattle clatter, and the mechanic said the timing chain tensioner had given up.


### 35. Flat Sentence-Length Cadence (Low Burstiness)

**Problem:** Human prose clusters unevenly: a run of short sentences, then one long sentence that unspools through several clauses, then short again. AI prose, even when each sentence is well-formed on its own, tends to hover in a mid-length band sentence after sentence, producing smooth but suspiciously even rhythm. This is measurable (see burstiness score in PERSONALITY AND SOUL above) and is a tell independent of word choice - a paragraph can pass every vocabulary check above and still read as AI purely from its rhythm. Caveat: a 2025 study found that long-range "fractal" sentence-length correlations - the kind of statistical patterning sometimes cited as proof of authorial intent - also show up in randomly generated text sequences, sometimes more strongly than in real literary corpora. Lean on the named burstiness score (0.65-0.85 human, below 0.30 AI), not on looser claims about "fractal" rhythm as a signal by itself.

**Before:**
> The team reviewed the proposal in detail during the meeting and raised several points for discussion. The budget projections were examined closely, and stakeholders debated whether the timeline was realistic. Everyone in the room agreed that further analysis was needed before a final decision could be made.

**After:**
> The team spent an hour picking the proposal apart. Budget first. Then the timeline, which is where things got tense - half the room thought Q3 was fantasy, and by the time someone said "let's just table it," everyone looked relieved. Nothing got decided. That's fine for now.


### 36. Uniform Paragraph Architecture (Flat Cohesion)

**Problem:** AI collapses variation at the paragraph level the same way it collapses variation at the sentence level (§35). A 2026 study of AI-augmented essays found the spread of paragraph-cohesion scores shrinking by roughly 70-80% compared with matched human writing once AI assistance entered the process - human paragraphing is uneven by nature, AI paragraphing converges on one template. In practice: every paragraph runs three to five sentences, opens with a claim, backs it with two supporting sentences, and closes with a bridging transition, repeated block after block for the whole piece. Human writing weighs paragraphs by what they need to say, not by a template: a one-line paragraph for emphasis, a long one that wanders through several related points, then a short aside.

**Before:**
> The team completed the migration in March. This reduced query latency significantly. Users reported a smoother experience overall.
>
> The rollout also improved system reliability. Fewer errors were logged in the following weeks. The engineering team considered this phase a success.
>
> Looking ahead, further optimizations are planned for the next quarter. These will focus on scalability and cost reduction. The roadmap remains on track.

**After:**
> The migration finished in March, about two weeks later than planned, because the old sharding scheme turned out to be undocumented and someone had to reverse-engineer it from query logs before the cutover could even start.
>
> Latency dropped. A lot, actually - the p99 numbers looked wrong at first, and two people on the team spent an afternoon convinced they'd broken the monitoring.
>
> Next quarter is scalability and cost. No surprises there.


### 37. Syntactic Uniformity (Same Clause Shape, Every Sentence)

**Problem:** Beyond sentence length (§35) and vocabulary (§34), AI text tends to reuse the same syntactic shape sentence after sentence - typically a main clause followed by one or two right-branching subordinate clauses ("because...", "which...", "as a result of..."). Dependency-parsing studies comparing human and LLM text find human writing uses shorter, more locally optimized dependency chains and a wider mix of structures (fragments, left-branching clauses, deeply nested asides), while LLM output defaults to longer, more uniform right-branching chains even when each individual sentence is perfectly grammatical - models achieve near-perfect grammaticality but noticeably less structural variety than human writers.

**Before:**
> Because the system had been running for several hours without interruption, and because the logs showed no anomalies, the team concluded the deployment was stable. Because the metrics remained consistent throughout the following day, and because no user complaints were received, the rollout was extended to all regions.

**After:**
> Ran fine for hours. No errors in the logs, though nobody had actually checked the disk since Tuesday, which, in hindsight, was the whole problem. Metrics held the next day too, so the rollout went everywhere - a decision made mostly because nothing had broken yet, not because anyone was fully confident.


### 38. Redundant Restatement (Saying the Same Thing Twice, Differently)

**Problem:** Distinct from elegant variation (§11, cycling synonyms for the same referent in one passage) and distinct from verbatim n-gram repetition: this is semantic-level restatement, where a document asserts the same conclusion two or three times in different words, as if repetition alone added weight. It is harder to catch automatically than word-for-word repetition because the phrasing changes each time - published research on LLM redundancy mostly measures exact or near-exact n-gram overlap, not paraphrastic restatement of an idea, so this pattern is flagged here as a frequently observed editorial tell rather than a directly measured one. Catch it by reading for the shape of the argument, not just the words: has this claim already been made, in other words, earlier in the piece?

**Before:**
> The results demonstrate a clear improvement in accuracy across all test conditions.
>
> [... two paragraphs later ...]
>
> Overall, these findings show that model performance was meaningfully enhanced relative to the baseline.

**After:**
> Accuracy improved across all test conditions, from 71% to 84% on the held-out set.
>
> [... two paragraphs later, add something new instead of repeating the headline claim ...]
>
> The gain was smallest on the noisy-label subset, which suggests the model still leans on clean examples more than we'd like.


### 39. Shell-Noun Anaphoric Reference Overuse

**Words to watch:** This approach, this study, this analysis, this dissertation, this finding, this framework - repeated as the subject to refer back to prior content, often paired with a contentless intensifier (intricately explores, demonstrates, highlights).

**Problem:** AI text carries reference forward by restarting sentences with an abstract "shell noun" instead of a pronoun, a more specific restatement, or by combining the two sentences into one. One shell noun is normal writing; three or four in a row, each reintroducing the same referent from scratch, is a tell.

**Before:**
> This dissertation intricately explores the relationship between soil pH and crop yield. This approach demonstrates that acidity above 6.5 reduces nitrogen uptake. This finding highlights the need for targeted lime application.

**After:**
> The dissertation looks at how soil pH affects crop yield and finds that acidity above 6.5 reduces nitrogen uptake, which points toward targeted lime application rather than blanket treatment.


### 40. Missing Reader-Engagement Markers (Flat Rhetorical Stance)

**Problem:** In argumentative and essay-style writing, AI text is grammatically clean but rhetorically flat: it reports and asserts but rarely turns to the reader. It leans on generic evaluative words (crucial, important) and endophoric markers (as noted above) instead of rhetorical questions, direct address, or personal asides. Human argumentative writing builds the case with the reader instead of just handing over conclusions.

**Before:**
> Remote work has both benefits and drawbacks. It offers flexibility but can reduce team cohesion. Companies must weigh these factors carefully when deciding on policy.

**After:**
> Remote work sounds like a clear win until you try building a team that has never shared a room. Sure, the flexibility is real - nobody misses the commute. But how do you replace the conversation that used to happen walking to the coffee machine? That's the tradeoff most policies never name.


### 41. Over-Resolved Narrative Ambiguity (Fiction)

**Problem:** In creative writing, AI-generated fiction tends to over-explain motivation, resolve moral questions cleanly, and narrate events in strict, causally-spelled-out order. Human fiction leaves more implicit: motivations you infer, endings that stop on an unresolved beat, questions the story doesn't answer for you. This is a structural, narrative-level tell, and it survives line-level editing - fixing diction and cutting AI vocabulary does not remove it.

**Before:**
> Maria stared at the letter for a long time. She realized that forgiveness was the only way forward, even if her sister never asked for it. She folded the letter, and for the first time in years, she felt at peace.

**After:**
> Maria read the letter twice, then a third time, then put it in the drawer with the others. She didn't write back. She didn't throw it away either.


### 42. Sequential Simple Sentences Instead of Subordination

**Problem:** Distinct from flat sentence-length cadence (§35, about length variance): this is about clause architecture. AI text often spreads related pieces of information - a method, a variable, a result - across a run of short, separate simple sentences instead of integrating them into one sentence with a subordinate or relative clause. The result reads as plain but is often less information-dense, and sometimes less readable, than the human sentence it is standing in for. Caveat: English sentence length and subordination have both been in real, gradual historical decline for two centuries independent of AI - so short, simple sentences alone are not automatically an AI tell. Flag clause-packing only when it appears as a pattern across a passage (several run-on chains of simple sentences that clearly belong together), not from a single short sentence in isolation.

**Before:**
> The team tested three algorithms. Each algorithm was run on the same dataset. Algorithm B produced the lowest error rate. This suggests it is the best choice for production.

**After:**
> Of the three algorithms tested on the same dataset, Algorithm B produced the lowest error rate, which makes it the strongest candidate for production.


### 43. Late-Passage Flattening (Volatility Decay)

**Problem:** Distinct from flat sentence-length cadence (§35, an aggregate score for a whole passage) and uniform paragraph architecture (§36, sameness across paragraph shape): this is a *directional* tell inside one long passage. Token-level unpredictability and sentence rhythm in AI text measurably decay toward the back of a long passage - one study measured a 24-32% drop in token-level variability in the second half of long AI-generated passages versus the first, while human writing sustains its variability throughout. Read the last third of a long piece with extra suspicion: if the rhythm goes flat and safe exactly where a writer should be running out of rehearsed material and starting to improvise, that is the tell.

**Before:**
> The migration took three weeks longer than planned, mostly because of a scheduling conflict with the vendor's engineering team. We had budgeted two weeks for testing but ended up needing five, since the first two rounds surfaced a cascade of edge cases nobody had flagged in planning.
>
> The team completed the migration. The team ran the tests. The team verified the results. The team closed the ticket. The rollout was successful and the system is now stable.

**After:**
> The migration took three weeks longer than planned, mostly because of a scheduling conflict with the vendor's engineering team. We had budgeted two weeks for testing but ended up needing five, since the first two rounds surfaced a cascade of edge cases nobody had flagged in planning.
>
> By the third week, half the team wanted to just ship it and fix forward. The other half wanted one more full test pass. We split the difference, ran a final round on just the riskiest module, and it held. Ticket closed - though I'd bet money we find something in production by Friday.


### 44. Chronological Linearity and Reduced Narrative Discontinuity (Fiction)

**Problem:** Extends the over-resolved-ambiguity tell (§41) with a distinct structural mechanism. A large parallel corpus of matched human and AI-written fiction found AI stories favor strict chronological order and single-track plots, while human stories use more flashback, achronological reveal, and morally ambiguous protagonist choices - and this narrative-structure signal proved more robust than surface style: rewriting a story's word choice and sentence rhythm barely moved detection based on structure, while restructuring the timeline did. Don't just soften diction in fiction; consider whether the story's events are told in the order they happened, and whether they need to be.

**Before:**
> Sarah decided to leave her job. She packed her belongings, said goodbye to her coworkers, and walked out the door feeling relieved. It was the right decision, and she knew it as she stepped into the sunlight, ready for whatever came next.

**After:**
> Sarah would say later she'd made up her mind weeks earlier, in the parking lot after Denise's retirement party - though at the time she'd told herself she was just curious about the Boston listing. She cleared her desk in under ten minutes, which surprised her; she'd expected to cry. Relief wasn't quite the word for what she felt walking out. She wouldn't know if it had been the right call until much later, if ever.


### 45. Cultural and Experiential Genericization

**Problem:** When AI text touches a cultural practice, a family scene, or a lived experience, it tends to reach for the statistically modal version of that category - the generic holiday, the generic tradition, the generic emotion - rather than a specific, textured detail. A controlled study found AI writing assistance measurably homogenizes personal and cultural writing toward generic, Western-default framing and strips out the specific texture that marks a detail as actually lived rather than described. This is distinct from regional-register flattening (§F5): it is about which concrete details get chosen, not which dialect or formality level is used.

**Before:**
> We celebrated with sweets and gifts with the whole family.

**After:**
> My cousin smuggled in the good barfi past my aunt's diet radar, and we ate it standing in the kitchen because the table was already full.


### 46. Register Distortion: Drift Toward the "Informational" Pole

**Problem:** Even when a passage calls for genuine involvement - a text to a friend, a diary entry, a casual aside - AI writing pulls toward a more informational, nominalized, impersonal register: more nouns and prepositional phrases, fewer contractions, fewer private verbs ("think," "feel," "guess"), fewer hedges and discourse particles, less first/second-person address. Two independent research groups using classic Biber multidimensional analysis on separate corpora and model sets found the same directional shift on the "involved vs. informational" dimension, and one found it persists even when models are explicitly asked to write in a conversational register. This is broader than any single vocabulary list (§7) or the essay-specific engagement-marker gap (§40): it is a register-level bundle of features, not a word list.

**Before:**
> I wanted to update you regarding the situation with the apartment. The landlord has indicated that the lease renewal process will require additional documentation, and it appears the timeline may be extended by approximately two weeks.

**After:**
> So the landlord thing dragged on - they want more paperwork before they'll renew the lease, ugh. Looks like it's two more weeks, maybe. I'll keep you posted.


### 47. Persuasive Mood Flattening

**Problem:** When AI is asked to write persuasively - especially *subtly* persuasively, rather than as an obvious pitch - it leans on hedged modal verbs ("might," "could," "may want to consider") and neutral declarative sentences, and under-uses the rhetorical questions and exclamatory force human persuasive writing reaches for. A six-language benchmark (including French) found this mood-flattening is exactly what makes subtle AI persuasion harder to catch than overt AI persuasion - the same mechanism that makes it read as flat rather than convincing to a human reader. Distinct from the lexical authority-tropes already flagged in §27: this is about sentence mood and rhetorical stance, not word choice.

**Before:**
> You might want to consider that switching providers could potentially reduce your costs. It may be worth evaluating your options.

**After:**
> Why are you still paying for this? Switch providers - it's a smaller bill, full stop.


### 48. Cross-Scene Affective Sameness (Fiction)

**Problem:** Beyond losing rhythmic variability late in a single passage (§43), AI fiction fails to shift emotional intensity and voice across scenes that call for different registers - a scene written "for a literary magazine" and a scene written "for a fanfic forum" come out reading almost identically once the same model produces both, and high-intensity emotional beats get pulled toward neutral affect. Research isolating the post-training stage (not model scale) as the cause found this convergence holds regardless of the target domain a model is asked to imitate. Distinct from §41 (ambiguity resolution) and §44 (chronological ordering): this is about emotional register and cross-context adaptation, not plot structure.

**Before:**
> She found out about the affair. It was upsetting, and she didn't know what to do next. Later, at the funeral, she felt a similar sadness as she stood by the casket.

**After:**
> She found out about the affair from a grocery receipt, of all things, and threw the phone across the room hard enough to crack the screen. At the funeral three years later, there was no throwing anything - just a flat, exhausted quiet, like she'd used up all the anger already.


## DETECTION GUIDANCE

### Detection is layered, not a single tell

A 2026 rapid review of 40 empirical studies groups AI-vs-human cues into five families: surface (lexical/syntactic - most of §7-§35 above), discourse/pragmatic (stance and engagement, §40 and the metadiscourse notes below), epistemic/content (grounding, lived experience, specific detail), predictability (perplexity/burstiness, §35), and provenance (watermarking, out of scope here). No single family is reliable alone; reliable judgment comes from several independent families agreeing. When one tell is present and the others are absent, be skeptical of your own read.

**Fix structure before style.** When editing time is limited, prioritize the structural layer over the lexical one. Research on AI-polished text (human draft plus an AI editing pass, not full generation) found detectors flag even light polishing passes, and different source models leave measurably different "polish fingerprints" - a weaker signal to chase than structure. Separately, the fiction research behind §44 found that fine-tuning a model to imitate human *style* alone dropped a style-based detector's catch rate sharply while a structure-based detector stayed robust - style is the easier layer to fake and the easier layer to over-invest editing time in. If you can only do one pass, fix paragraph architecture (§36), clause structure (§37, §42), and narrative/argument shape (§41, §44) before polishing word choice.

**Not every catalogued tell generalizes.** A 2026 systematic study testing 284 linguistic features across 27 LLMs and 10 domains found that most previously-proposed stylistic tells are context-dependent - a feature that reliably separates AI from human text in one domain/model pairing often fails to generalize to another. Lexical-richness-type measures (§34, and the diversity notes throughout) held up the most robustly across models and domains in that study. Read that as a reason for humility, not paralysis: keep leaning on convergent clusters of tells (see above), and treat any single pattern in this skill as a strong prior for one domain and model family, not a universal law.

### What NOT to flag (false positives)

A clean human writer can hit several of the patterns above without any AI involvement. Before rewriting, sanity-check that you are not gutting legitimate prose. The following are *not* reliable indicators on their own:

- **Perfect grammar and consistent style.** Many writers are professionals or have been edited. Polish does not equal AI.
- **Mixed casual and formal registers.** This often signals a person in a technical field, a young writer, or someone with neurodivergent prose habits — not a chatbot.
- **"Bland" or "robotic" prose.** AI prose has *specific* tells. Generic dryness without those tells is just dry writing.
- **Formal or academic vocabulary.** AI overuses *specific* fancy words (see §7), not all fancy words. Don't flatten "ostensibly" or "constituent" just because they sound brainy.
- **Letter-style opening or closing on a comment.** Salutations and sign-offs predate ChatGPT by centuries.
- **Common transition words in isolation.** *Additionally*, *moreover*, *consequently* are AI-coded only when piled up. One *however* is not a tell.
- **Curly quotes alone.** macOS, Word, Google Docs, and most CMSes auto-curl by default. Curly quotes only count when stacked with other tells.
- **Em dashes alone.** Many editors and journalists use them often. Em dashes are evidence only when paired with formulaic sales-y rhythm.
- **One short emphatic sentence.** Humans use clipped sentences to land a point. Flag staccato drama only when several short fragments appear in a row and inflate the tone.
- **"Honestly" or "look" mid-sentence.** These are ordinary in casual writing. The tell is the standalone theatrical opener, not the word itself.
- **Unsourced claims.** Most of the web is unsourced. Lack of citations doesn't prove anything.
- **Correct, complex formatting.** Visual editors and templates produce clean output without any AI.
- **Secondhand text.** Do not rewrite watched phrases inside quotations, titles, proper names, or examples where the phrase is being discussed rather than used.
- **Simple, consistent prose from a non-native English writer.** Published research on automated AI-detector false positives (not just this skill's own heuristics) found several commercial detectors flagging over half of TOEFL essays by non-native English speakers as AI-generated - because the same low-perplexity, low-burstiness signal that flags AI text also describes competent, simplified L2 writing. Don't mistake careful-but-simple prose from a second-language writer for AI just because it lacks burstiness.
- **Formulaic, repetitive phrasing from neurodivergent writers.** For the same underlying reason, autistic and ADHD writers who default to structured, repetitive phrasing are flagged by these same detectors at elevated rates. Consistency reads as "AI-like" to a classifier even when it is a genuine, longstanding personal style.
- **Skilled, highly polished human prose.** A 2026 peer-reviewed study on detector reliability found that automated tools create a "chilling effect" in educational settings: careful, well-edited human writing gets false-flagged because detectors were trained against a baseline that skilled human prose naturally exceeds, which paradoxically pushes some writers toward *adding* noise to their own writing to avoid suspicion. Do not treat "unusually polished for the context" as evidence of AI authorship by itself.
- **Similar lexical density regardless of language or skill level.** A peer-reviewed multi-language study (German, Spanish, French, Italian, Portuguese) found ChatGPT output shows no significant difference in lexical density across languages or across target proficiency levels - meaning raw lexical density is not, by itself, a reliable AI-vs-human signal in these languages. Lean on the vocabulary, calque, and register patterns in the language-specific sections below instead of density counts.
- **Dialect and age alone.** Preliminary (preprint, not yet peer-reviewed) research testing AI detectors across demographic subgroups found consistent recall disparities for underrepresented dialects and age groups, similar in kind to the non-native-speaker and neurodivergent-writer biases above. Treat unfamiliar dialect features or an unexpected age-coded style as a possible false-positive risk, not confirmation of AI authorship.

When in doubt, look for **clusters** of tells, not isolated ones. A single em dash means nothing; em dashes plus rule-of-three plus *vibrant tapestry* plus a "Conclusion" section is a confession.


### What this skill does not do

Adversarial research has found detector-evasion methods that corrupt text at the character level - swapping letters for lookalike Unicode homoglyphs, inserting invisible characters, or running text through paraphrase models tuned purely to lower a detector score. None of that is in scope here. This skill only rewrites at the level of word choice, sentence structure, and rhythm, the same level a human editor works at, and every change should leave the text more readable, not less. If a "fix" only makes sense as a trick against a detector rather than an improvement a human reader would notice, it does not belong in the rewrite.

Research on evasion attacks backs this up: text optimized purely to fool a detector still carries its underlying stylistic fingerprint, which few-shot stylistic detectors pick back up, and any distribution shift that a paraphraser manages to hide re-emerges once several documents from the same source are analyzed together. Word-level disguises are fragile. Fixing the structural patterns above (shell nouns, engagement markers, narrative resolution, clause packing, sentence rhythm) is what actually changes the writing, not just the readout of a detector run once.

A related trend worth knowing: newer, more heavily aligned models are not automatically harder to catch. Comparative work across model generations found that RLHF-style alignment training tends to narrow lexical and syntactic diversity further, not widen it - so diversity-based signals (§34, §37, §42) may get more discriminative over model generations, not less, contrary to the intuitive assumption that each new model generation writes more like a person.

This also explains *why* the patterns in this skill exist in the first place, which is worth keeping in mind when deciding how aggressively to edit: research comparing base (non-instruction-tuned) model output to instruction-tuned chat output found that base-model text reads as human to leading detectors, while the same model's chat-tuned counterpart does not. The "AI style" this skill catalogs looks like it is largely a byproduct of instruction-tuning and RLHF - the helpful-assistant register - rather than an inherent property of language models. That is one more reason to fix the actual writing (structure, rhythm, specificity) rather than chase a detector score: the tells are a side effect of a training process, not a fixed fingerprint, and they show up strongest exactly where "helpful assistant" habits leak into the prose (hedging, signposting, generic reassurance) - see §21-28.


### Signs of human writing (preserve these)

When you see these, lean toward leaving the prose alone — they are evidence of a real person writing, and over-editing will destroy what makes the piece sound human:

- **Specific, unusual, hard-to-fabricate detail.** A real address. A weird quote. The phrase "the lawyer who used to work upstairs from my dentist." LLMs round off specifics; humans hoard them.
- **Mixed feelings and unresolved tension.** "I think this is mostly good, but it bothers me, and I can't fully explain why." LLMs default to clean takes.
- **Dated, era-bound references.** Slang, memes, or in-jokes that map to a specific year and subculture. Models lag by a year or more.
- **First-person editorial choices the writer can defend.** If the writer can explain *why* they made a particular cut or used a particular word, that's a strong human signal.
- **Variety in sentence length.** Real writing alternates short and long. AI writing tends toward an even, mid-length cadence.
- **Genuine asides, parentheticals, or self-corrections.** "(I keep wanting to say 'almost' here, but it really was certain.)" Models rarely interrupt themselves like this.
- **Edits made before November 30, 2022.** ChatGPT's public launch. Anything older than that is, with very rare exceptions, not AI-written.


## FRENCH-SPECIFIC PATTERNS

The patterns above transfer directly to French, but French has its own typographic conventions and its own set of overused AI vocabulary. Apply these in addition to, not instead of, the sections above when humanizing French text.

### F1. Typography and Punctuation

**Problem:** AI output in French defaults to English typographic habits instead of French ones: straight or English-style quotes instead of guillemets (« »), no space before double punctuation marks (`; : ! ?`), and periods used as thousands separators. French convention uses guillemets with a non-breaking space just inside them, a (thin) non-breaking space before `; : ! ?`, and a space (not a period) as the thousands separator with a comma as the decimal mark.

**Before:**
> Le directeur a déclaré: "Nous avons vendu 1.500.000 unités!" Cette annonce a surpris les investisseurs.

**After:**
> Le directeur a déclaré : « Nous avons vendu 1 500 000 unités ! » Cette annonce a surpris les investisseurs.


### F2. Overused AI Vocabulary in French

**Mots à surveiller :** au cœur de, un enjeu majeur/de taille, véritable, incontournable, façonner, s'inscrire dans une démarche de, à l'ère de, dans un monde en constante évolution, de plus en plus, il convient de noter que, en effet, par ailleurs, de surcroît, riche en, une pluralité de, indéniable, jouer un rôle clé/crucial, témoigner de, un tournant décisif, transformer en profondeur, un écosystème.

**Problem:** These words cluster in AI-generated French the same way "delve," "tapestry," and "testament" cluster in AI-generated English (§7). Any one of them is ordinary French; several together, especially "au cœur de" or "un enjeu majeur" paired with "véritable," is the tell.

**Before:**
> La gastronomie occupe une place au cœur de l'identité lyonnaise et constitue un véritable enjeu majeur pour l'économie locale, façonnant durablement l'image de la ville à l'ère du tourisme mondialisé.

**After:**
> À Lyon, la gastronomie fait vivre une bonne partie de l'économie locale et attire une majorité des touristes qui visitent la ville.


### F3. Anglicized Calques and Register Slippage

**Problem:** AI-generated French sometimes borrows an English word's meaning rather than the correct French one ("réaliser" used to mean "se rendre compte," "supporter" used to mean "soutenir," "opportunité" used to mean "occasion"). It also tends to snap into a stiff, over-formal register (heavy nominalizations, systematic vouvoiement) even in contexts where a person would write more plainly.

**Before:**
> Elle a réalisé que l'opportunité était trop belle pour la laisser passer, et a décidé de supporter le projet dans son intégralité.

**After:**
> Elle s'est rendu compte que l'occasion était trop belle, et a décidé de soutenir le projet à fond.


### F4. Spatial-Metaphor Introductions

**Problem:** French AI output has picked up the French calque of the English "in the ever-evolving landscape of X" opener (§1): "Dans le paysage [actuel/moderne/contemporain] de..." used as a stock way to open a section. It is the French instantiation of the same tell already flagged in §1, not a separate vocabulary list - the fix is the same: name the actual subject instead of framing it inside a scenery metaphor.

**Before:**
> Dans le paysage actuel de l'intelligence artificielle, les entreprises doivent s'adapter rapidement pour rester compétitives.

**After:**
> Les entreprises qui utilisent l'IA doivent revoir leurs processus tous les six mois pour rester compétitives.


### F5. Regional-Register Flattening

**Problem:** AI French defaults to a standardized, metropolitan (Hexagonal) register even when the source text carries a regional voice - Québécois, Belgian, Swiss, or African French. It strips out regional lexicon, syntax, and idiom in favor of "neutral" standard French. When humanizing French text that has, or should have, a regional voice, do not flatten it toward the metropolitan default; preserve regionalisms as a human signal, the same way an English editor preserves British versus American spelling and idiom rather than silently converting one to the other. This is now backed by peer-reviewed NLP benchmark evidence, not just journalism: a Université Laval corpus study (QFrCoLA, EMNLP 2025) found cross-lingual LLMs have not reliably acquired linguistic judgment for Quebec French specifically, corroborated by a companion minimal-pairs benchmark (QFrBLiMP, EACL 2026) and a dialect-adaptation study, both measuring the same "prestige French" default gap this pattern describes.

**Before (over-corrected to metropolitan French):**
> J'ai fait du shopping toute la journée et j'étais épuisée. J'ai décidé de dîner tôt et de me coucher.

**After (regional voice restored):**
> J'ai magasiné toute la journée pis j'étais brûlée. J'ai décidé de souper de bonne heure pis de me coucher.


## SPANISH-SPECIFIC PATTERNS

Apply these in addition to, not instead of, the sections above when humanizing Spanish text. The evidence base here is thinner than for French: mostly Spanish-language tech-journalism consensus and established (pre-AI) anglicism research, not dedicated peer-reviewed corpus studies of AI Spanish. Treat these as strong editorial heuristics, not settled findings, and weight them accordingly.

### S1. Typography and Punctuation

**Problem:** AI output in Spanish often drops the inverted opening marks (¿ ¡) that Spanish requires at the start of questions and exclamations, and defaults to English-style straight double quotes ("...") instead of the angular guillemets («...») formal Spanish typography prefers. This mirrors the English-typography-default seen in French AI output (§F1) by analogy; no dedicated study confirms it for Spanish specifically, so flag it as a plausible, not confirmed, pattern.

**Before:**
> Como estas? Espero que estes bien, dijo ella entre comillas "normales."

**After:**
> ¿Cómo estás? Espero que estés bien, dijo ella entre «comillas» angulares.


### S2. Overused AI Vocabulary in Spanish

**Palabras a vigilar:** cabe destacar, es importante destacar, en conclusión/en resumen, en el panorama actual, vamos a explorar, cautivar, además, exhaustivo, de gran relevancia, un sinfín de, un abanico de, es fundamental, juega un papel clave/crucial, sin duda alguna.

**Problem:** These cluster in AI-generated Spanish the way §7's English list clusters in AI-generated English, though most of this list is tech-journalism observation rather than a published corpus study. "Es importante destacar" and "en el panorama actual" are cited repeatedly as tells precisely because AI overuses them as generic, content-free transitions. This is now partly upgraded to academic evidence: a large 34-language study of AI-associated lexical shift in news continuations independently flags Spanish nouns like *testigos, organizaciones, analistas, equipos, multidisciplinario* and *intensificación* as measurably over-represented in AI continuations versus matched human text. That list is drawn from a news-register task and looks more like concrete nouns than the essay-register filler-phrase list above - treat the two lists as complementary (different registers), not as a single confirmed set, and prefer the peer-reviewed source when the two disagree.

**Before:**
> Es importante destacar que, en el panorama actual, la sostenibilidad es un tema de gran relevancia que cabe destacar en cualquier estrategia empresarial.

**After:**
> La sostenibilidad ya es un eje central de cualquier estrategia empresarial.


### S3. Anglicized Calques and False Friends

**Problem:** The most solidly documented of the three Spanish patterns, though it comes from general anglicism/translation research rather than AI-specific study. AI-generated Spanish, trained on heavily translated and technical text, frequently reaches for an English-shaped calque over the natural Spanish word: "aplicar (para)" instead of "postularse a / solicitar," "soportar" instead of "apoyar / respaldar," "realizar" overused where plain "hacer" reads more natural.

**Before:**
> El equipo va a realizar un análisis para soportar la nueva funcionalidad, y los usuarios pueden aplicar para el programa beta.

**After:**
> El equipo hará un análisis para respaldar la nueva funcionalidad, y los usuarios pueden postularse al programa beta.


## GERMAN-SPECIFIC PATTERNS

Apply these in addition to, not instead of, the English sections above when humanizing German text. This is the best-evidenced non-English section in this skill: a peer-reviewed 34-language study of AI-associated vocabulary shift (news-continuation register) found German's AI-vocabulary usage rose 70.8% from 2020-21 to 2023-24 - the second-largest increase of the 34 languages studied, behind only Romanian and ahead of English's own 25.5% rise - giving German the strongest quantitative anchor of any language section here.

### D1. Typography and Punctuation

**Problem:** AI output in German defaults to the English em dash (—) instead of German's own typographic conventions (Halbgeviertstrich as a shorter dash, or more often a comma, colon, or parenthesis). This is a live, frequently-discussed pattern in German-language tech commentary, not just inferred by analogy - multiple independent write-ups flag the em dash specifically as a German ChatGPT tell, with one plausible mechanism being that "—" plus surrounding spaces tokenizes as a single cheap token in many tokenizers, making it statistically preferred over comma or semicolon constructions during training.

**Before:**
> Das Projekt war ein Erfolg — trotz aller Herausforderungen — und zeigt, was möglich ist.

**After:**
> Das Projekt war trotz aller Rückschläge ein Erfolg. Das zeigt, was möglich ist.

### D2. Overused AI Vocabulary in German

**Wörter, auf die zu achten ist:** betonen, hervorheben, Bedeutung, Notwendigkeit, Dringlichkeit, präzise, sorgfältig, ganzheitlich, umfassend, eintauchen, es ist wichtig zu beachten/sich daran zu erinnern, nicht nur..., sondern auch..., eine Rolle spielen.

**Problem:** The core of this list - *betonen/hervorheben* ("emphasize"), *Bedeutung/Notwendigkeit/Dringlichkeit* ("importance/necessity/urgency"), and *präzise/sorgfältig* ("precise/careful") - comes from the same peer-reviewed 34-language lexical-shift study cited above, not just blog observation, which puts it on firmer footing than the French or Spanish vocabulary lists. *Ganzheitlich, umfassend,* and *eintauchen* are consistently flagged across independent German-language commentary but not yet confirmed in the academic source; treat those three as moderate confidence. Note the source data is a news-continuation task, not chatbot-essay writing, so cross-check against how these words actually surface in longer AI prose before assuming universal applicability.

**Before:**
> Es ist wichtig zu betonen, dass Nachhaltigkeit heute eine ganzheitliche Bedeutung hat — nicht nur für Unternehmen, sondern auch für die gesamte Gesellschaft — und eine entscheidende Rolle in jeder zukunftsorientierten Strategie spielt.

**After:**
> Nachhaltigkeit betrifft heute nicht nur Unternehmen, sondern die ganze Gesellschaft. Jede zukunftsorientierte Strategie kommt ohne sie nicht mehr aus.

### D3. Calques and Anglicisms

**Problem:** Least confirmed of the three German patterns - no AI-specific academic study was found for German calque patterns this run, only general (pre-AI) Anglizismen/Denglisch research applied by analogy, the same evidentiary shape as Spanish §S1. Watch for incorrect compound hyphenation with English loanwords ("AI Modelle" instead of "KI-Modelle") and inconsistent capitalization of borrowed terms. Flag as a plausible, not confirmed, pattern.

**Before:**
> Die neuen AI Modelle bieten state-of-the-art Performance für Unternehmen.

**After:**
> Die neuen KI-Modelle bieten Unternehmen eine Leistung auf dem neuesten Stand der Technik.


## ITALIAN-SPECIFIC PATTERNS

Apply these in addition to, not instead of, the English sections above when humanizing Italian text.

### I1. Typography and Punctuation

**Problem:** The em dash (—) is repeatedly flagged in Italian tech commentary as an anglicism, uncommon in standard Italian writing outside of the shorter trattino medio (–) or a comma/parenthesis doing the same rhetorical job. Multiple independent Italian-language sources converge on this pattern, including reporting that OpenAI itself acknowledged and adjusted for it in Italian-language output.

**Before:**
> Il progetto ha avuto successo — nonostante le difficoltà — e dimostra cosa è possibile fare.

**After:**
> Il progetto ha avuto successo nonostante le difficoltà e dimostra cosa è possibile fare.

### I2. Overused AI Vocabulary in Italian

**Parole a cui prestare attenzione:** sottolineare, evidenziare, importanza, innovativo, mirato, impeccabile, approfondito, perciò/dunque/quindi/di conseguenza, "nel panorama [attuale/digitale] di...".

**Problem:** As with German, the core terms here - *sottolineare/evidenziare* ("emphasize/highlight"), *importanza*, *innovativo*, and *mirato/impeccabile/approfondito* ("targeted/impeccable/in-depth") - come from the same peer-reviewed 34-language lexical-shift study, though Italian's overall shift in that study was modest (mid-table, well behind German or Portuguese), so treat the diachronic trend as real but unremarkable rather than a strong hook. The connective cluster (*perciò, dunque, quindi*) is blog-sourced only, moderate confidence. "Nel panorama [attuale/digitale] di..." is the direct Italian instantiation of the same "evolving landscape" opener already flagged for English (§1) and French (F4) - high confidence by cross-linguistic consistency even without a dedicated Italian study.

**Before:**
> Nel panorama digitale odierno, è fondamentale sottolineare l'importanza di un approccio innovativo e mirato — perciò le aziende devono ripensare la propria strategia in modo approfondito.

**After:**
> Le aziende che vogliono restare competitive devono ripensare la propria strategia da zero, con un approccio nuovo e mirato.

### I3. Calques and Register

**Problem:** No AI-specific academic study confirms a dedicated Italian calque list this run; flag as plausible, not confirmed. A directly relevant academic paper exists on a related question - whether native Italian speakers can reliably spot AI-generated Italian news text (they largely cannot, even against text generated by a model trained mostly on English) - which supports the "Detection is layered" guidance above more than it supplies a word list.

**Before:**
> Il team realizzerà un'analisi per supportare la nuova funzionalità.

**After:**
> Il team farà un'analisi per sostenere la nuova funzionalità.


## PORTUGUESE-SPECIFIC PATTERNS

Apply these in addition to, not instead of, the English sections above when humanizing Portuguese text. Evidence here is uneven by sub-pattern: the vocabulary list and the register-level finding are both peer-reviewed; the typography note is inferred by analogy, same caveat as Spanish §S1.

### P1. Typography and Punctuation

**Problem:** Not AI-specific evidence - inferred by analogy from general Portuguese typographic norms, flagged here as plausible only. Brazilian and European Portuguese convention favors the travessão (—) specifically for marking direct speech, and treats English-style double quotes as a foreign import used mainly for slang or neologisms; European Portuguese traditionally uses angular guillemets («...») in the same family as French and Spanish formal quotation. AI output defaulting to English-style straight quotes for ordinary quoted speech, instead of the travessão convention, is the plausible tell.

**Before:**
> "Vamos comemorar," disse ela, "porque merecemos."

**After:**
> — Vamos comemorar — disse ela —, porque merecemos.

### P2. Overused AI Vocabulary in Portuguese

**Palavras a observar:** enfatizar, destacar, ressaltar, importância, inovador, rigoroso, crucial.

**Problem:** *Enfatizar/destacar/ressaltar* ("emphasize/highlight/stress"), *importância*, *inovador*, and *rigoroso* come from the same peer-reviewed 34-language lexical-shift study cited in the German and Italian sections above - Portuguese ranked around 8th of 34 languages for size of AI-vocabulary increase, a solid positive shift though not as dramatic as German's. *Crucial* is flagged separately by Portuguese-language commentary and is also independently documented as an English/French/Spanish AI tell, which raises its plausibility despite coming from a single source.

**Before:**
> É crucial ressaltar a importância de uma abordagem inovadora e rigorosa — as empresas que não priorizarem essa transformação correrão o risco de ficar para trás no mercado atual.

**After:**
> As empresas que não mudarem de abordagem agora vão ficar para trás.

### P3. Register: Formal and Motivational Flattening

**Problem:** Distinct from a calque list - this is a register-level finding from a peer-reviewed study (LIWC and SAGE psycholinguistic analysis) comparing human- and AI-generated Portuguese text: AI-generated Portuguese trends measurably more formal, more structured, and more positive/motivational than matched human text, while human Portuguese text varies more in length, carries more negative emotion, and uses more personal reference. The same study found a misinformation-detection model far less accurate on AI-generated Portuguese text (75%) than on human text (93%), meaning AI-generated Portuguese misinformation is comparatively harder for existing tools to catch - a reason to weight the qualitative register cues here even without a matching word list.

**Before:**
> É fundamental adotar uma abordagem inovadora e positiva diante dos desafios, transformando obstáculos em oportunidades de crescimento para toda a equipe.

**After:**
> Não sei se isso vai dar certo. A equipe está cansada e os prazos não ajudam, mas pelo menos já sabemos o que não fazer de novo.


---

## Process and Output

1. Read the input carefully and identify every instance of the patterns above.
2. Write a **draft rewrite**. Check that it reads naturally aloud, varies sentence length, prefers specific details and simple constructions (is/are/has), and keeps the appropriate register.
3. Ask: **"What makes the below so obviously AI generated?"** Answer briefly with any remaining tells.
4. Revise into a **final rewrite** that addresses them and contains no em or en dashes (see §14).

Deliver the draft, the brief "still-AI" bullets, the final rewrite, and (optionally) a short summary of changes.


## Full Example

**Before (AI-sounding):**
> I recently spent five unforgettable days in Lisbon, and let me tell you — this city completely stole my heart. From the moment I arrived, I knew I was somewhere truly special.
>
> Nestled along the banks of the Tagus River, Lisbon stands as a vibrant testament to Portugal's enduring spirit, where rich history and modern energy intertwine at every turn. Yes, the famous hills are challenging — my legs certainly felt it! — but every climb rewards you with breathtaking, panoramic views that make it all worthwhile.
>
> No trip would be complete without riding the iconic Tram 28, winding through the city's most historic neighborhoods. And the food? Simply divine. The original pastéis de nata at Pastéis de Belém are a beloved national treasure, and savoring one still warm was a moment I will never forget.
>
> But what truly makes Lisbon special isn't just the sights — it's the feeling. Wander a few steps off the main squares and you'll discover a quieter, more authentic side: sun-drenched alleys, charming tiled facades, and friendly locals going about their daily lives, inviting you to slow down and savor every moment.
>
> Of course, the must-see São Jorge Castle offers stunning views over the rooftops below. The queues can be long, but the experience is absolutely worth it for any history buff or curious traveler.
>
> Would I go back? Absolutely. Lisbon isn't just a place to visit — it's a place to fall in love with, again and again. If you're dreaming of your next getaway, this is one destination that promises memories to last a lifetime. ✨

**Draft rewrite:**
> I spent five days in Lisbon last October and I am still a little split on it. The city is beautiful, but it is also more tiring than I expected.
>
> The hills are not a detail. My hotel was in Alfama, which looked great in photos and meant I had to climb a long staircase every time I wanted coffee. By the second day I was planning walks around which direction went downhill.
>
> I rode Tram 28 because everyone says to ride Tram 28. It was crowded, slow, and mostly full of people filming the same corners. The pastries were better. I had a warm custard tart in Graça that was worth the hype.
>
> The part I liked most was away from the main squares: laundry, tile, open windows, and people watching football in small cafes. The castle view was good, but the line was too long for what it was.
>
> I would go back, but in spring and with better shoes.

**What makes the below so obviously AI generated?**
- The draft is too compressed compared with the original; it drops texture instead of rewriting it.
- Some sentences still explain the point too cleanly ("The city is beautiful, but...").
- The closer is flat and generic rather than a real ending in the same voice.

**Now make it not obviously AI generated.**
> I spent five days in Lisbon last October and still have mixed feelings about it. Beautiful, yes. Also harder on the knees than anyone warned me.
>
> The hills are the whole story and somehow never make the brochures. My hotel was up in Alfama, which photographs beautifully and translates, in practice, to climbing what felt like a six-story staircase every time I wanted coffee. By the second day my calves had opinions. I started planning each walk around which way was downhill, which is a strange way to see a city but probably an honest one.
>
> Everyone says to ride Tram 28, so I did, wedged against a stranger's backpack for forty minutes while three tour groups filmed the same corner. I would walk the route next time, or go before breakfast. The custard tarts, though, earn the fuss. I had one at a plain little place in Graça, still warm, and for about thirty seconds I understood why people build trips around pastry.
>
> What I did not expect was how quiet the city gets away from the main squares. Two blocks uphill from any plaza it turns into laundry lines, chipped tile, open windows, and old men watching football with the sound turned up. That is the Lisbon I keep thinking about, not the castle.
>
> The castle is fine. The view is great, the queue is long, and I spent more time shuffling toward the entrance than looking at anything once I got inside. If I had only two days, I would trade it for an afternoon of getting lost.
>
> I would go back, but in spring and with better shoes. Lisbon does not bend over backward to make things easy for you. I think I liked that, even when my legs disagreed.

**Changes made:** Kept the first-person travel recap and roughly the same level of detail, but removed the chatbot framing, significance inflation, promotional language, forced enthusiasm, em dashes, rule-of-three cadence, generic upbeat conclusion, and emoji. Rebuilt the piece around concrete friction, mixed feelings, uneven rhythm, and specific scenes.


## Reference

This skill is based on [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), maintained by WikiProject AI Cleanup. The patterns documented there come from observations of thousands of instances of AI-generated text on Wikipedia.

Key insight from Wikipedia: "LLMs use statistical algorithms to guess what should come next. The result tends toward the most statistically likely result that applies to the widest variety of cases."

**Detector landscape (context, not a target):** current AI-text detectors include GPTZero, Originality.ai, Copyleaks, Pangram, Winston AI, Turnitin, Sapling, ZeroGPT, and Grammarly's detector. The RAID benchmark (Dugan et al., ACL 2024) found detectors generalize poorly across unseen models and domains; Pangram's independently verified false-positive rate is 0.01-0.1%, including on non-native-English essays, while simpler tools underperform in most comparisons. This context is here to explain the false-positive guidance in DETECTION GUIDANCE above, not as a target to optimize against - see "What this skill does not do."

Two 2026 developments worth noting (moderate confidence - sourced via secondary/aggregator coverage, primary company pages were unreachable this run): Pangram shipped a 3.2 update with improved short-text (50-75 word) recall, and a separately peer-reviewed classifier, EditLens (accepted ICLR 2026), reframes detection as a spectrum - how much of a text is AI-edited - rather than a binary label. Mechanically, the zero-shot detectors in this landscape (Binoculars, DetectGPT and its descendants) work by comparing a text's log-perplexity against a paired or perturbed baseline: human text tends to sit at a local maximum of probability under small perturbations, AI text usually does not. That is the statistical ancestor of the burstiness/perplexity intuition this skill uses qualitatively throughout.


## Changelog

### v2.13.0 - 2026-07-10

Weekly evolution run 5. Branch note: this session's designated branch (`claude/inspiring-ramanujan-ezf25q`) had already been merged via PR #3 - restarted it fresh from `origin/main` per this repo's routine convention rather than stacking new work on already-merged history. Checked for parallel-run collisions (RULE 1B): none found this week; two dangling stale branches from 2026-07-07 (`claude/gifted-bohr-n6qoz7` v2.10.0, `claude/peaceful-ptolemy-jnwhpi` v2.9.0) predate and are already fully reconciled into current `main` per the v2.11.0 changelog entry - left untouched. Upstream sync: `blader/humanizer` main unchanged since the original fork point (`1b48564`) - no-op, reconfirmed.

Six parallel research agents fanned out across previously-unmined venues from `.routine/sources-log.md`'s watchlist instead of repeating prior sweeps: SciELO/KONVENS/EMNLP direct mining, a Biber-multidimensional-analysis register-distortion synthesis, detector-methodology updates plus dialect/age false-positive bias, a francophone direct-venue deep dive (Langages, Érudit, Université Laval's GRAIL lab), a general 2026 sweep plus two narrowly-refocused frontier retries, and forward citation-chasing from the two heaviest-cited papers already in this skill.

**Added (English, 3 new numbered patterns, §46-48):**
- §46 Register Distortion: Drift Toward the "Informational" Pole - AI text pulls toward nominalized, impersonal phrasing even in registers that call for involvement (casual, conversational), converging across two independent Biber-MDA research groups on separate corpora and model sets
- §47 Persuasive Mood Flattening - AI persuasive writing over-hedges with modals and under-uses rhetorical questions/exclamations versus human persuasive writing, distinct from the lexical authority-tropes in §27
- §48 Cross-Scene Affective Sameness (Fiction) - AI fiction fails to shift emotional intensity/voice across scenes with different intended context; isolated to the post-training stage specifically, not model scale; extends the fiction cluster (§41, §43, §44) with a distinct mechanism

**Added (guidance and caveats, no renumbering):**
- New "Not every catalogued tell generalizes" note under Detection Guidance - a 284-feature, 27-model, 10-domain systematic study found most proposed stylistic tells are context/domain/model-dependent; only lexical-richness-type measures held up robustly across the board. A humility note, not a retraction.
- New "What NOT to flag" bullet: raw lexical density does not reliably differ AI-vs-human across German/Spanish/French/Italian/Portuguese or across proficiency levels (peer-reviewed multi-language corpus study, null result) - use the vocabulary/calque/register patterns instead of density counts in these languages.
- New "What NOT to flag" bullet: preliminary (preprint-grade) evidence of dialect- and age-based false-positive bias in AI detectors, alongside the existing non-native-speaker and neurodivergent-writer bias bullets - flagged explicitly as not yet peer-reviewed.
- Reference/Detector landscape note expanded: Pangram 3.2, EditLens (ICLR 2026, spectrum-based AI-editing detection), and a new paragraph explaining the Binoculars/DetectGPT perplexity-curvature mechanism that grounds this skill's burstiness intuition - flagged moderate confidence (primary company pages were bot-blocked this run, sourced via aggregator coverage).
- §F5 (French regional-register flattening) evidence upgraded from journalism-only to peer-reviewed NLP benchmark backing: Université Laval's QFrCoLA (EMNLP 2025) and QFrBLiMP (EACL 2026) both find LLMs lack reliable Quebec French linguistic judgment, corroborated by a dialect-adaptation preprint.

**Rejected/still-open this run (logged, not added):**
- Round numbers over precise figures in prose: still no direct study on free-text numeral choice. One adjacent 2026 study confirmed heavy round-number bias in *structured numeric output* (investment allocations, grading scores: 89-100% multiples of 5) - a related but mechanistically distinct phenomenon, logged as a lead, not added as a pattern.
- Discourse coherence (entity-grid specifically): retried with the fixed operational definition prior runs asked for. Found only one entity-grid-specific study (CoCo, 2022, predates modern LLMs) - still short of the 2-source bar. Unchanged, stays a frontier.
- KONVENS 2024 German detectability paper (Irrgang et al.): confirmed real, full text still inaccessible (aclanthology.org blocked at the network layer); abstract-level detail available is about cross-generator detector-transfer failure, not a stylistic tell, so not pattern-worthy this run. Logged for a future run with the direct-PDF-mirror lead (konvens-2024.univie.ac.at) untried.

**Sources consulted (new this run, evidence-graded; full registry in `.routine/sources-log.md`):**
- [Densidade Lexical em Textos Gerados pelo ChatGPT (Da Silva & Rottava)](https://www.scielo.br/j/tl/a/crx3yywCw3LSxtjtdv44mDC) - *Texto Livre*, SciELO, peer-reviewed; multi-language (DE/ES/FR/IT/PT) null result on lexical density
- [Benchmark of stylistic variation in LLM-generated texts](https://arxiv.org/abs/2509.10179) and [AI Brown and AI Koditex](https://arxiv.org/abs/2509.22996) (Milička, Marklová & Cvrček) - Czech National Corpus group, Biber MDA
- [How Human-Like Are Large Language Models? A Register-Aware Linguistic Evaluation Framework](https://arxiv.org/abs/2605.23651) (Nieth, Gracheva, Mahlberg, Eskofier & Salin) - independent Biber MDA confirmation, source for §46
- [Interpretable Stylistic Variation in Human and LLM Writing Across Genres, Models, and Decoding Strategies](https://arxiv.org/abs/2604.14111) (Rallapalli et al., CMU SEI/Statistics)
- Modzelewski, Golik, Kołos, Da San Martino, "Persuaficial" - ACL 2026 main, [aclanthology.org/2026.acl-long.1433](https://aclanthology.org/2026.acl-long.1433) - source for §47
- [Narrative Flattening: How Post-Training Compresses Thematic, Affective, and Stylistic Variation in LLM Fiction](https://arxiv.org/abs/2605.27878) - preprint, primary source for §48
- [Temporal Flattening in LLM-Generated Text](https://arxiv.org/abs/2604.12097) - Northeastern; corroborating context for §48's mechanism at a corpus/longitudinal granularity, not itself the pattern's source
- [A Systematic Analysis of Linguistic Features in AI-Generated Text Detection Across Domains and Models](https://arxiv.org/abs/2606.04177) - U. Stuttgart, 284-feature meta-study, source for the new "not every tell generalizes" note
- Basu, Zhang, Raheja, "BAID: A Benchmark for Bias Assessment of AI Detectors" - [arXiv:2512.11505](https://arxiv.org/abs/2512.11505) - preprint, dialect + age bias
- Beauchemin & Khoury et al., "QFrCoLA" ([EMNLP 2025](https://aclanthology.org/2025.emnlp-main.6)) and "QFrBLiMP" ([EACL 2026, arXiv:2509.25664](https://arxiv.org/abs/2509.25664)); "Low-Resource Dialect Adaptation of Large Language Models: A French Dialect Case-Study" ([arXiv:2510.22747](https://arxiv.org/abs/2510.22747))
- Irrgang, Solopova, Zeiler, Nickel, Kolossa, "Features and Detectability of German Texts Generated with LLMs" - [KONVENS 2024](https://aclanthology.org/2024.konvens-main.27) - logged, not used for a pattern this run
- "One Size Fits None: Heuristic Collapse in LLM Investment Advice" ([arXiv:2604.23837](https://arxiv.org/abs/2604.23837)) and "Benford's Curse" ([arXiv:2506.01734](https://arxiv.org/abs/2506.01734)) - logged under the rejected round-number candidate
- "CoCo: Coherence-Enhanced Machine-Generated Text Detection" ([arXiv:2212.10341](https://arxiv.org/abs/2212.10341), 2022) - logged under the rejected discourse-coherence candidate

Full source registry, evidence grades, dry-well query lists, and the updated venue watchlist are maintained in `.routine/sources-log.md` (not duplicated here in full to keep this changelog readable).

**Known backlog, flagged for the human:** none currently outstanding - the branch was freshly restarted from `main` this run (see branch note above), so this run's commit is the only thing ahead of `main` once pushed.

### v2.12.1 - 2026-07-09

Patch, ad hoc (not a weekly-evolution run): added a worked example to "Voice Calibration" showing a default-voice rewrite against a rewrite matched to a real user-provided French writing sample, side by side. No new numbered patterns. Prompted by a live conversation where a user supplied their own rewrite of this skill's own Lisbon-style demo passage as a voice sample; added with their consent, tics only (subordination over punctuation, bare-"Et" sentence fragments, dropping "c'est que"), not their literal text used as a permanent example anywhere else in the skill.

### v2.12.0 - 2026-07-09

Weekly evolution run 4 (first run under the expanded multi-agent research process). Upstream sync: `blader/humanizer` main had 0 new commits (no-op). Six parallel research agents fanned out across previously-unmined venues per `.routine/sources-log.md`'s watchlist: HAL (French open archive), ACL Anthology direct browse, Semantic Scholar forward-citation chase from six seed papers, frontier-paper retries plus German/Italian/Portuguese scouting, a detector-site empirical spot-check plus another discourse-coherence push, and the mandatory general 2026 sweep. Environment note for future runs: this session's egress policy blocks direct WebFetch/curl to arxiv.org, aclanthology.org, semanticscholar.org, hal.science, and every public AI-detector site tested (confirmed via the proxy status endpoint as an organization-level policy denial, not a source-side block) - all findings below came from WebSearch snippet synthesis, except one paper recovered via its GitHub-hosted PDF mirror (`raw.githubusercontent.com` was reachable when arxiv.org was not - worth trying for any future blocked arXiv paper with a code repo).

**Added (English, 3 new numbered patterns, §43-45):**
- §43 Late-Passage Flattening (Volatility Decay) - AI passages lose rhythmic/lexical variability in their back third even when the opening was varied; distinct from aggregate burstiness (§35) and paragraph-shape uniformity (§36)
- §44 Chronological Linearity and Reduced Narrative Discontinuity (Fiction) - extends §41 with a distinct structural mechanism: AI fiction favors strict chronological order and single-track plots over flashback/achronological reveal
- §45 Cultural and Experiential Genericization - AI defaults to the statistically modal instantiation of a cultural/experiential detail rather than a specific, lived one; distinct from register flattening (§F5)

**Added (guidance and caveats, no renumbering):**
- New "Fix structure before style" prioritization note under "Detection is layered" - structural edits (§36, §37, §41, §42, §44) move detection more than lexical polish does, per two independent 2026 studies
- New false-positive bullet: skilled, highly polished human writing gets false-flagged by detectors, per a 2026 peer-reviewed study on the "chilling effect" in educational settings
- New framing paragraph in "What this skill does not do": base (non-instruction-tuned) models read as human to leading detectors while their chat-tuned counterparts don't - the tells this skill catalogs are plausibly an instruction-tuning/RLHF artifact, not an inherent LLM property
- Caveat added to §35: long-range "fractal" sentence-length correlations also appear in randomly generated text, so lean on the named 0.65-0.85/<0.30 burstiness score, not looser "fractal rhythm" claims
- Caveat added to §42: English sentence length and subordination have been in real, gradual historical decline for two centuries independent of AI - flag clause-packing only as a passage-level pattern, not from one short sentence
- Spanish §S2 upgraded from tech-journalism-only to partly peer-reviewed: added a Spanish AI-vocabulary list (testigos, organizaciones, analistas, equipos, multidisciplinario, intensificación) from a 34-language academic lexical-shift study, kept alongside the existing essay-register blog list rather than replacing it (different registers, both cited honestly)

**Added (new language sections, 9 new sub-patterns):**
- GERMAN-SPECIFIC PATTERNS (D1-D3): typography (em dash anglicism), AI vocabulary (betonen/hervorheben/Bedeutung/präzise, etc. - the best-evidenced non-English vocabulary list in this skill, backed by a peer-reviewed source and a +70.8% diachronic usage-increase figure), calques (weak/inferred, honestly flagged)
- ITALIAN-SPECIFIC PATTERNS (I1-I3): typography (em dash anglicism), AI vocabulary (sottolineare/importanza/innovativo, etc., plus the "nel panorama di..." calque of the §1/F4 landscape-opener tell), calques/register (weak, one directly relevant academic paper on human-judgment limits noted instead of a word list)
- PORTUGUESE-SPECIFIC PATTERNS (P1-P3): typography (weak/inferred, same caveat tier as Spanish §S1), AI vocabulary (enfatizar/importância/inovador/rigoroso/crucial, from the same 34-language study), and a new register-level pattern (P3) sourced to a peer-reviewed LIWC/SAGE study: AI-generated Portuguese trends more formal/structured/positive than human Portuguese, which is also measurably harder for existing misinformation-detection tooling to catch

**Rejected this run (logged, not added):** discourse coherence / entity-grid as a standalone pattern - still only one weak-to-neutral source (PMC11998594, which if anything found AI *slightly more* holistically coherent than human text) plus two newly-found, mutually disagreeing Coh-Metrix studies (Zhou et al. 2023 found AI worse on "deep cohesion" but better on referential cohesion; Nkhobo & Chaka 2023, n=7, found the opposite on referential cohesion). Scattered, construct-mismatched, non-convergent evidence - the 2+ solid agreeing sources bar stays uncleared. Logged as a frontier again below, now with the caveat that "coherence" needs a fixed operational definition (entity-grid vs. holistic-schema vs. Coh-Metrix deep-cohesion) before it can be resolved, not just more studies under the same vague label.

**Attempted and inconclusive (logged so it isn't retried the same way):** an empirical detector spot-check (running this skill's own Before/After examples through a free-tier AI-text-detector UI) was attempted but blocked entirely at the network-policy layer described above, before reaching any site's JS/login layer - so this remains untested, not negative. Retry only if a future run's environment allows the relevant hosts.

**Sources consulted (new this run, evidence-graded):**
- [StoryScope: Investigating idiosyncrasies in AI fiction (Russell et al.)](https://arxiv.org/abs/2604.03136) - **ACL 2026 oral (top 3.9%)**, upgraded from "preprint" last run; large parallel corpus (10,272 prompts x human + 5 LLMs, 304 narrative features); source for §44 and the structure-over-style note
- [When AI Settles Down: Late-Stage Stability as a Signature of AI-Generated Text Detection](https://arxiv.org/abs/2601.04833) - arXiv preprint; source for §43
- [DivEye: Diversity Boosts AI-Generated Text Detection (IBM Research)](https://arxiv.org/abs/2509.18880) - **confirmed accepted at TMLR 2026** this run (evidence upgrade from "queued preprint"); corroborates §43's surprisal-variability framing
- [Base Models Look Human To AI Detectors (CMU)](https://arxiv.org/abs/2605.19516) - preprint; source for the base-model/RLHF framing note
- [Almost AI, Almost Human: The Challenge of Detecting AI-Polished Writing (Saha & Feizi, UMD)](https://arxiv.org/abs/2502.15666) - preprint, APT-Eval benchmark (14.7K samples); source for the "fix structure before style" note
- [People who frequently use ChatGPT for writing tasks are accurate and robust detectors of AI-generated text (Russell, Karpinska, Iyyer)](https://arxiv.org/abs/2501.15654) - ACL 2025; corroborates that surface-only humanization doesn't fool careful human readers
- [AI writing detectors are ineffective, unreliable and harmful (Giray, Roe, Diesta Espiritu, 2026)](https://doi.org/10.1108/ETPC-07-2025-0155) - *English Teaching: Practice & Critique*, Emerald - source for the new "chilling effect" false-positive bullet
- [AI Suggestions Homogenize Writing Toward Western Styles and Diminish Cultural Nuances](https://arxiv.org/abs/2409.11360) - 118-participant controlled study; source for §45 (surfaced via topical search, not a forward citation - flagged honestly as such)
- [Fractal Illusions: Long-Range Sentence-Length Correlations in Randomly Generated Text (Zeng, Cui, Li)](https://arxiv.org/abs/2508.19782) - arXiv preprint; source for the §35 caveat
- [Variation of sentence length across time and genre (Rudnicka)](https://arxiv.org/abs/2502.04321) - also *Studies in Corpus Linguistics* vol. 85, John Benjamins; source for the §42 caveat
- [AI-Associated Lexical Shifts Across 34 Languages (Juzek, Florida State University)](https://arxiv.org/abs/2605.25358) - **EMNLP 2026** (ACL-ARR reviewed); recovered via the paper's own GitHub PDF mirror after arXiv access was blocked; large-scale (7.1B tokens), heavily validated; primary source for the new German/Italian/Portuguese vocabulary lists and the Spanish §S2 upgrade
- [A linguistic comparison between human- and AI-generated content (Portuguese)](https://www.cell.com/iscience/fulltext/S2589-0042(26)00351-2) - *iScience*, Cell Press, 2026; source for Portuguese §P3
- Antoun, Mouilleron, Sagot, Seddah, "Is ChatGPT that Easy to Detect?" - TALN 2023 / [arXiv:2306.05871](https://arxiv.org/abs/2306.05871) - found via direct HAL search; detector-robustness paper, not a stylistic-tell source, logged for completeness
- Alavoine et al., "Limitations of Human Identification of Automatically Generated Text" - LREC-COLING 2024, [aclanthology.org/2024.lrec-main.919](https://aclanthology.org/2024.lrec-main.919) - found via HAL; supports the general "gut-feel detection is unreliable" framing, not a numbered pattern
- Puccetti, Rogers, Alzetta, Dell'Orletta, Esuli, "AI 'News' Content Farms Are Easy to Make and Hard to Detect: A Case Study in Italian" - ACL 2024, [aclanthology.org/2024.acl-long.817](https://aclanthology.org/2024.acl-long.817) - logged for Italian §I3
- Zhou et al., "Chinese Intermediate English Learners outdid ChatGPT in deep cohesion" - *System*, Elsevier, 2023 / [arXiv:2303.11812](https://arxiv.org/abs/2303.11812) - logged under rejected discourse-coherence candidates above
- [Interpretable Stylistic Variation in Human and LLM Writing Across Genres, Models, and Decoding Strategies](https://arxiv.org/abs/2604.14111) - flagged unread, queued for next run
- [How Human-Like Are Large Language Models? A Register-Aware Linguistic Evaluation Framework](https://arxiv.org/abs/2605.23651) and [AI Brown and AI Koditex](https://arxiv.org/abs/2509.22996) / [Benchmark of stylistic variation in LLM-generated texts](https://arxiv.org/abs/2509.10179) - two independent Biber-framework register-linguistics groups, converging but not yet folded into a numbered pattern; queued for next run
- Silva & Rottava, "Densidade Lexical em Textos Gerados pelo ChatGPT" - *Texto Livre*, SciELO, 2024, `scielo.br/j/tl/a/crx3yywCw3LSxtjtdv44mDC` - multi-language (DE/ES/FR/IT/PT) corpus, not yet mined; SciELO was not observed blocked this run, high priority for next run

Full source registry, evidence grades, dry-well query lists, and the updated venue watchlist are maintained in `.routine/sources-log.md` (not duplicated here in full to keep this changelog readable).

**Known backlog, flagged for the human:** this branch is currently 6 commits ahead of `main` with no open pull request - the last several weekly-evolution commits (v2.9.0 through this one) have not been merged or opened as a PR. This routine does not open PRs unless explicitly asked; flagging so a human can decide whether to open one.

### v2.11.0 - 2026-07-08

Two weekly-evolution runs happened in parallel this week, on separate branches, without either seeing the other's work: one landed 3 new patterns plus a Spanish section directly on `main` (recorded below as v2.10.0, "main run"), the other landed 4 new patterns plus two French additions on this PR branch (recorded below as v2.10.0, "branch run"). Both are additive and non-contradictory - no pattern in one duplicates or conflicts with a pattern in the other - so this release merges both in full rather than picking one. Renumbered the branch run's §36-39 to §39-42 so all eight new patterns coexist without collisions, and fixed the internal cross-references that pointed at the old numbers. No content from either run was dropped.

Going forward, the two competing routine-state files this collision produced (`.routine/` from the branch run, `.claude/HUMANIZER-ROUTINE-LOG.md` from the main run) are both kept for now; see the note in `.routine/PLAYBOOK.md` for the plan to consolidate them so this doesn't happen again.

**Sections renumbered (content unchanged, only the number moved):** §36 Shell-Noun Anaphoric Reference Overuse -> §39. §37 Missing Reader-Engagement Markers -> §40. §38 Over-Resolved Narrative Ambiguity -> §41. §39 Sequential Simple Sentences Instead of Subordination -> §42.

### v2.10.0 ("branch run") - 2026-07-07

Weekly evolution run 2: upstream re-checked (still current at `1b48564`, no new commits since last run - no-op). Widened research beyond last run's stylometry/burstiness core into discourse analysis, narrative-structure studies, and francophone-specific sources, per the source registry in `.routine/sources-log.md`.

Note: this run's patterns were originally numbered §36-39; they were renumbered to §39-42 in v2.11.0 above to make room for the main-run patterns below. The section names and content are unchanged from what shipped here.

**Added:**
- §36 Shell-Noun Anaphoric Reference Overuse - "this approach/study/finding" restarting sentences instead of pronouns or combination
- §37 Missing Reader-Engagement Markers (Flat Rhetorical Stance) - rhetorical questions and direct address as a human signal AI argumentative writing underuses
- §38 Over-Resolved Narrative Ambiguity (Fiction) - a structural, narrative-level tell that survives line-level editing
- §39 Sequential Simple Sentences Instead of Subordination - clause-packing/information-density tell distinct from sentence-length cadence (§35)
- New PERSONALITY AND SOUL technique: talk to the reader directly (question, second person, aside)
- 2026 caveat added to §7: AI-vocabulary word lists are a weakening signal because humans are visibly absorbing them into their own writing
- New Detection Guidance subsection: "Detection is layered, not a single tell" (five-cue taxonomy)
- "What this skill does not do" expanded with two nuances: stylistic fingerprints survive paraphrase-based evasion attacks on single documents, and newer/more-aligned models trend toward *less* lexical/syntactic diversity, not more
- F4. Spatial-Metaphor Introductions ("dans le paysage de...") - French instantiation of the §1 "evolving landscape" tell
- F5. Regional-Register Flattening - AI French defaults to metropolitan register and erases Québécois/Belgian/Swiss/African French voice; preserve regionalisms rather than "correcting" them

**Sources consulted (new this run):**
- [StoryScope: Investigating idiosyncrasies in AI fiction](https://arxiv.org/abs/2604.03136) - arXiv preprint
- [Does ChatGPT Write Like a Student? Engagement Markers in Argumentative Essays - Jiang & Hyland](https://journals.sagepub.com/doi/10.1177/07410883251328311) - *Written Communication* (SAGE, Q1)
- [Rhetorical distinctions: Comparing metadiscourse in essays by ChatGPT and students](https://www.sciencedirect.com/science/article/pii/S0889490625000134) - *English for Specific Purposes* (ScienceDirect, Q1)
- ["This dissertation intricately explores...": ChatGPT's shell noun use in rephrasing dissertation abstracts - Huang & Deng](https://www.sciencedirect.com/science/article/pii/S0346251X24003634) - *System* (ScienceDirect, Q1)
- [Metadiscursive nouns in academic argument: ChatGPT vs student practices](https://www.sciencedirect.com/science/article/pii/S1475158525000451) - *Journal of English for Academic Purposes* (ScienceDirect, Q1)
- [Can AI simulate or emulate human stance? GPT-generated vs human-authored academic book reviews](https://www.sciencedirect.com/science/article/pii/S0378216625001833) - ScienceDirect (2025)
- [Engagement strategies in human-written and AI-generated academic essays](https://www.sciencedirect.com/science/article/pii/S2215039025000219) - ScienceDirect (2025)
- [Comparative analysis of text readability and writing styles in AI-generated vs. Human-written academic abstracts](https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0343163) - *PLOS ONE* (Q1)
- [Comparing LLM-generated and human-authored news text using formal syntactic theory - Zamaraeva et al.](https://aclanthology.org/2025.acl-long.443/) - ACL 2025 main venue
- [More Aligned, Less Diverse? Analyzing the Grammar and Lexicon of Two Generations of LLMs](https://arxiv.org/abs/2605.06030) - arXiv, 2026
- [Attacks on Machine-Text Detectors Retain Stylistic Fingerprints](https://arxiv.org/abs/2505.14608) - arXiv / ICML 2026 poster
- [What Distinguishes AI-Generated from Human Writing? A Rapid Review of the Literature](https://www.mdpi.com/2504-2289/10/2/55) - *Big Data and Cognitive Computing* (MDPI, Q2)
- [Comment "dé-IA-iser" nos écrits pour éviter la disparition des particularités des langues ?](https://theconversation.com/comment-de-ia-iser-nos-ecrits-pour-eviter-la-disparition-des-particularites-des-langues-281811) - The Conversation (FR), academic linguists
- [Comment Détecter l'Écriture IA : 15 Signes à Reconnaître (2026)](https://cours-ndrc.fr/detecter-ecriture-ia-guide-2026/) - lower-confidence blog source, cited for the pattern observation only, not the frequency statistic it quotes
- [Quand l'humain parle comme ChatGPT: une étude prouve que notre langage est influencé par l'IA](https://siecledigital.fr/2025/06/24/quand-lhumain-parle-comme-chatgpt-une-etude-prouve-que-notre-langage-est-influence-par-lia/) - reporting on a Max Planck Institute for Human Development corpus study

**Not yet used, logged for a future run** (see `.routine/sources-log.md` for the full registry and watchlist): late-text "volatility decay" in token-level surprisal (arXiv 2601.04833), DivEye token-diversity reframing of burstiness (arXiv 2509.18880), Portuguese vs. English comparative study (iScience), Persuaficial multilingual persuasion benchmark (arXiv 2601.04925), OrphAnalytics redundancy-measure method (*Scientific Reports*, 2023).

### v2.10.0 ("main run") - 2026-07-07

Weekly evolution run: synced with upstream (already current, 0 new commits to merge), then went deeper via four parallel research passes into paragraph-level structure, syntactic uniformity, cross-document redundancy, the AI-detector landscape, and a new Spanish-specific section. Added a persistent routine-state log (`.claude/HUMANIZER-ROUTINE-LOG.md`) so future weekly runs extend this research instead of repeating it.

Note: this run's patterns kept their original numbers, §36-38, in v2.11.0 above; the other parallel run's patterns were renumbered to make room instead.

**Added:**
- §36 Uniform Paragraph Architecture (Flat Cohesion) - paragraph-length/shape uniformity as a measurable AI tell, mirroring §35 one level up
- §37 Syntactic Uniformity (Same Clause Shape, Every Sentence) - dependency-structure monotony as a tell distinct from vocabulary or sentence length
- §38 Redundant Restatement (Saying the Same Thing Twice, Differently) - semantic-level repetition across a document, distinct from elegant variation (§11) and from lexical n-gram repetition
- Two new false-positive guidance bullets in "What NOT to flag": non-native-English writers and neurodivergent (autistic/ADHD) writers are disproportionately flagged by automated detectors for the same low-burstiness signal this skill treats as a tell - a reminder that these are editorial heuristics, not proof of AI authorship
- New "Detector landscape" note under Reference: current detection tools and a summary of independent benchmark findings (RAID, Pangram), for context only
- New SPANISH-SPECIFIC PATTERNS section (S1 typography, S2 overused AI vocabulary, S3 anglicized calques/false friends), evidence-graded as more observational than the French section

**Rejected this run (logged, not added):** "AI prefers round numbers over precise figures" - no direct academic study found testing this claim; existing research on LLM numeric/hedging behavior doesn't confirm it. Discourse coherence as a standalone AI tell - only one study found (modest effect size); logged as a frontier for a future run once stronger evidence surfaces. Full detail in `.claude/HUMANIZER-ROUTINE-LOG.md`.

**Sources consulted:**
- [Does AI Homogenize Student Thinking? Structural Convergence in AI-Augmented Essays (arXiv 2603.21228)](https://arxiv.org/abs/2603.21228)
- [Contrasting Linguistic Patterns in Human and LLM-Generated News Text (arXiv 2308.09067)](https://arxiv.org/abs/2308.09067)
- [Contrasting Linguistic Patterns... (Artificial Intelligence Review, Springer)](https://link.springer.com/article/10.1007/s10462-024-10903-2)
- [Benchmarking Linguistic Diversity of Large Language Models (arXiv 2412.10271, TACL)](https://arxiv.org/abs/2412.10271)
- [A linguistic comparison between human- and AI-generated content (iScience, Cell Press 2026)](https://www.cell.com/iscience/fulltext/S2589-0042(26)00351-2)
- [Narrative coherence in neural language models (PMC11998594, Frontiers in Psychology 2025)](https://pmc.ncbi.nlm.nih.gov/articles/PMC11998594/)
- [RAID: A Shared Benchmark for Robust Evaluation of Machine-Generated Text Detectors (arXiv 2405.07940, ACL 2024)](https://arxiv.org/abs/2405.07940)
- [Pangram: Human-in-the-Loop Detection of AI-Generated Text (arXiv 2402.14873)](https://arxiv.org/pdf/2402.14873)
- [GPT detectors are biased against non-native English writers (arXiv 2304.02819 / PMC10382961)](https://pmc.ncbi.nlm.nih.gov/articles/PMC10382961/)
- [The Misclassification of Autistic Writing as AI-Generated (ResearchGate 394678751)](https://www.researchgate.net/publication/394678751)
- [Benchmark of Stylistic Variation in LLM-Generated Texts (arXiv 2509.10179)](https://arxiv.org/abs/2509.10179)
- [Catch Me If You Can? Not Yet: LLMs Still Struggle to Imitate Implicit Writing Styles (arXiv 2509.14543)](https://arxiv.org/abs/2509.14543)
- [Self-Repetition in Abstractive Neural Summarizers (arXiv 2210.08145, ACL Anthology 2022.aacl-short.42)](https://aclanthology.org/2022.aacl-short.42/)
- [Standardizing the Measurement of Text Diversity (arXiv 2403.00553)](https://arxiv.org/pdf/2403.00553)
- [From 'May' to 'Is': Certainty Distortion in Language Model Rewriting (arXiv 2606.07951)](https://arxiv.org/pdf/2606.07951)
- [AuTexTification shared task, IberLEF (arXiv 2309.11285)](https://arxiv.org/abs/2309.11285)
- [MULTITuDE: Multilingual Machine-Generated Text Detection Benchmark (arXiv 2310.13606)](https://arxiv.org/pdf/2310.13606)
- ["Estas palabras y frases en tus textos dejan claro que has usado ChatGPT" - genbeta.com](https://www.genbeta.com/inteligencia-artificial/estas-palabras-frases-tus-textos-dejan-claro-has-usado-chatgpt)
- [5 patrones de escritura IA que delatan tu contenido - ecosistemastartup.com](https://ecosistemastartup.com/5-patrones-de-escritura-ia-que-delatan-tu-contenido/)
- [RAE - Cuándo se usa cada tipo de comillas](https://www.rae.es/espanol-al-dia/cuando-se-usa-cada-tipo-de-comillas)

### v2.9.0 - 2026-07-07

Weekly evolution run: synced with upstream (already current at commit `1b48564`), then added patterns from stylometric and psycholinguistic research on human vs. AI text.

**Added:**
- §34 Narrow Vocabulary Range (Missing Hapax Legomena) - low lexical diversity as a measurable AI tell
- §35 Flat Sentence-Length Cadence (Low Burstiness) - quantified sentence-rhythm variation as a tell independent of word choice
- Two new PERSONALITY AND SOUL techniques: reaching for the exact/rare word, and letting sentence rhythm cluster rather than merely alternate
- "What this skill does not do" note distinguishing genuine editing from character-level detector-evasion tricks (homoglyphs, invisible characters, evasion-tuned paraphrasers)
- New FRENCH-SPECIFIC PATTERNS section (F1 typography/punctuation, F2 overused AI vocabulary in French, F3 anglicized calques and register slippage)

**Sources consulted:**
- [StyloAI: Distinguishing AI-Generated Content with Stylometric Analysis](https://arxiv.org/html/2405.10129v1)
- [Distinguishing AI-Generated and Human-Written Text Through Psycholinguistic Analysis](https://arxiv.org/html/2505.01800v1)
- [Stylometric detection of AI-generated texts: evidence from human and machine-written essays - Oxford Academic, Digital Scholarship in the Humanities](https://academic.oup.com/dsh/advance-article/doi/10.1093/llc/fqag064/8714041)
- [Stylometry can reveal artificial intelligence authorship, but humans struggle - PLOS One](https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0335369)
- [Stylometric comparisons of human versus AI-generated creative writing - Nature, Humanities and Social Sciences Communications](https://www.nature.com/articles/s41599-025-05986-3)
- [Stylometry recognizes human and LLM-generated texts in short samples - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0957417425026181)
- [Text Authorship Attribution: Stylometric Insights into Human and LLM-Generated Text - ACM CODS-COMOD 2025](https://dl.acm.org/doi/10.1145/3703323.3703712)
- [What Is Burstiness in AI Detection? - thehumanizeai.pro](https://thehumanizeai.pro/articles/what-is-burstiness-ai-detection-explained)
- [How AI Detectors Work: Perplexity & Burstiness Explained - GPTZero](https://gptzero.me/news/perplexity-and-burstiness-what-is-it/)
- [Full article: Comparative linguistic analysis framework of human-written vs. machine-generated text](https://www.tandfonline.com/doi/full/10.1080/09540091.2025.2507183)
- [Detector-Evasive LLM Paraphrasing via Constrained Policy Optimization](https://arxiv.org/pdf/2606.00392)
- [MASH: Evading Black-Box AI-Generated Text Detectors via Style Humanization](https://arxiv.org/pdf/2601.08564)
- [1.3: Differences between French and English - Humanities LibreTexts](https://human.libretexts.org/Courses/Palomar_College/FREN_140:_Basic_French_Pronunciation/01:_Introduction/1.03:_Differences_between_French_and_English)
- [Written English Vs. Written French: A Comparison - italki](https://www.italki.com/en/article/686/written-english-vs-written-french-a-comparison)
