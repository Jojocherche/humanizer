# Humanizer

A portable agent skill that removes signs of AI-generated writing from text, making it sound more natural and human. It is plain Markdown, so it can run in any harness that supports skill-style instructions.

## Installation

### Skills CLI

Install with the cross-agent skills CLI:

```bash
npx skills add blader/humanizer
```

Update an existing install:

```bash
npx skills update humanizer
```

To install into every supported agent harness:

```bash
npx skills add blader/humanizer --agent '*'
```

To target one configured harness, pass its agent name:

```bash
npx skills add blader/humanizer --agent <agent-name>
```

### Claude Code plugin

Claude Code users can also install Humanizer as a plugin:

```
/plugin marketplace add blader/humanizer
/plugin install humanizer@humanizer
```

The skill is then invoked as `/humanizer:humanizer`.

### Manual

Any agent harness can use the skill directly because the runtime artifact is `SKILL.md`. Install it wherever your harness expects skill directories, or copy `SKILL.md` into an existing skill folder.

For example:

```bash
git clone https://github.com/blader/humanizer.git /path/to/your/skills/humanizer
```

Or, if you already have this repo cloned:

```bash
mkdir -p /path/to/your/skills/humanizer
cp SKILL.md /path/to/your/skills/humanizer/
```

## Usage

Invoke the skill however your agent harness exposes installed skills. Common forms include a slash command or a direct request:

```
/humanizer

[paste your text here]
```

```
Please humanize this text: [your text]
```

### Voice Calibration

To match your personal writing style, provide a sample of your own writing:

```
/humanizer

Here's a sample of my writing for voice matching:
[paste 2-3 paragraphs of your own writing]

Now humanize this text:
[paste AI text to humanize]
```

The skill will analyze your sentence rhythm, word choices, and quirks, then apply them to the rewrite instead of producing generic "clean" output.

## Overview

Based on [Wikipedia's "Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) guide, maintained by WikiProject AI Cleanup. This comprehensive guide comes from observations of thousands of instances of AI-generated text.

The skill also includes a final "obviously AI generated" audit pass and a second rewrite, to catch lingering AI-isms in the first draft.

### Key Insight from Wikipedia

> "LLMs use statistical algorithms to guess what should come next. The result tends toward the most statistically likely result that applies to the widest variety of cases."

## Patterns Detected (with Before/After Examples)

**Note:** `SKILL.md` is the source of truth and is ahead of this table - it now documents 45 numbered English patterns (§1-45) plus five language-specific sections (French, Spanish, German, Italian, Portuguese). This table has not been kept in sync through several recent weekly-evolution runs (last fully updated at 35 patterns, v2.9.0); rebuilding it fully is logged as follow-up work rather than attempted as a rushed partial edit here. See `SKILL.md`'s own Changelog section for the complete, current pattern list and sourcing.

### Content Patterns

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 1 | **Significance inflation** | "marking a pivotal moment in the evolution of..." | "was established in 1989 to collect regional statistics" |
| 2 | **Notability name-dropping** | "cited in NYT, BBC, FT, and The Hindu" | "In a 2024 NYT interview, she argued..." |
| 3 | **Superficial -ing analyses** | "symbolizing... reflecting... showcasing..." | Remove or expand with actual sources |
| 4 | **Promotional language** | "nestled within the breathtaking region" | "is a town in the Gonder region" |
| 5 | **Vague attributions** | "Experts believe it plays a crucial role" | "according to a 2019 survey by..." |
| 6 | **Formulaic challenges** | "Despite challenges... continues to thrive" | Specific facts about actual challenges |

### Language Patterns

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 7 | **AI vocabulary** | "Actually... additionally... testament... landscape... showcasing" | "also... remain common" |
| 8 | **Copula avoidance** | "serves as... features... boasts" | "is... has" |
| 9 | **Negative parallelisms / tailing negations** | "It's not just X, it's Y", "..., no guessing" | State the point directly |
| 10 | **Rule of three** | "innovation, inspiration, and insights" | Use natural number of items |
| 11 | **Synonym cycling** | "protagonist... main character... central figure... hero" | "protagonist" (repeat when clearest) |
| 12 | **False ranges** | "from the Big Bang to dark matter" | List topics directly |
| 13 | **Passive voice / subjectless fragments** | "No configuration file needed" | Name the actor when it helps clarity |

### Style Patterns

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 14 | **Em/en dashes** | "institutions—not the people—yet this continues—" | Cut them: periods, commas, colons, or parentheses |
| 15 | **Boldface overuse** | "**OKRs**, **KPIs**, **BMC**" | "OKRs, KPIs, BMC" |
| 16 | **Inline-header lists** | "**Performance:** Performance improved" | Convert to prose |
| 17 | **Title Case Headings** | "Strategic Negotiations And Partnerships" | "Strategic negotiations and partnerships" |
| 18 | **Emojis** | "🚀 Launch Phase: 💡 Key Insight:" | Remove emojis |
| 19 | **Curly quotes** | `said “the project”` | `said “the project”` |
| 26 | **Hyphenated word pairs** | “cross-functional, data-driven, client-facing” | Drop hyphens on common word pairs |
| 27 | **Persuasive authority tropes** | "At its core, what matters is..." | State the point directly |
| 28 | **Signposting announcements** | "Let's dive in", "Here's what you need to know" | Start with the content |
| 29 | **Fragmented headers** | "## Performance" + "Speed matters." | Let the heading do the work |
| 30 | **Diff-anchored writing** | "This function was added to replace..." | Describe what it does, not what changed |
| 31 | **Manufactured punchlines / staccato drama** | "It had no preference. No prior. No nostalgia." | Use varied sentence lengths and concrete claims |
| 32 | **Aphorism formulas** | "Symmetry is the language of trust" | Replace the formula with the actual claim |
| 33 | **Conversational rhetorical openers** | "Honestly? It depends..." | Remove the fake-candid setup |
| 34 | **Narrow vocabulary range** | "made a loud noise" | "let out a death-rattle clatter" |
| 35 | **Flat sentence-length cadence** | Every sentence ~18-20 words, no variation | Mix short bursts with one long unspooling sentence |

### Communication Patterns

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 20 | **Chatbot artifacts** | "I hope this helps! Let me know if..." | Remove entirely |
| 21 | **Cutoff disclaimers** | "While details are limited in available sources..." | Find sources or remove |
| 22 | **Sycophantic tone** | "Great question! You're absolutely right!" | Respond directly |

### Filler and Hedging

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 23 | **Filler phrases** | "In order to", "Due to the fact that" | "To", "Because" |
| 24 | **Excessive hedging** | "could potentially possibly" | "may" |
| 25 | **Generic conclusions** | "The future looks bright" | Specific plans or facts |

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

**After (Humanized):**
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

## References

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) - Primary source
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) - Maintaining organization

## Version History

- **3.1.0** - Added 4 patterns to a new EXTENSION PATTERNS section: shell-noun anaphoric reference overuse, register distortion toward the "informational" pole, persuasive mood flattening, and additional anglicized calques in French ("faire du sens," "adresser un problème"). All numbered patterns (§1-33) and the French-specific section (F1-F4) are unchanged and now frozen going forward - new material only ever lands in EXTENSION PATTERNS after passing a 3-point bar (actionable, non-contradictory, applies to English or French). Full sourcing in `SKILL.md`'s Changelog.
- **3.0.0** - Clean reset to the upstream blader/humanizer base (33 patterns + French-specific section), keeping six targeted additions from the interim 2.9.0-2.13.0 runs. Dropped a large batch of academic-apparatus patterns (old #34-48), German/Italian/Portuguese/Spanish sections, and a numeric burstiness score - these had accumulated contradictions and relied on statistics that weren't practical for an editor to apply consistently. See `SKILL.md`'s Changelog for the full list of what was kept and why.
- **2.12.0** - Weekly evolution run 4: added patterns #43-45 (late-passage rhythm flattening, non-chronological narrative structure, cultural/experiential genericization), plus caveats to #35 and #42, a "fix structure before style" prioritization note, a new false-positive bullet, and full German- and Italian-specific pattern sections plus a Portuguese-specific pattern section (new). Upgraded Spanish AI-vocabulary evidence with an academic source. Full sourcing in `SKILL.md`'s Changelog.
- **2.10.0 / 2.11.0** - Two parallel weekly-evolution runs added patterns #36-42 (paragraph-cohesion uniformity, syntactic uniformity, redundant restatement, shell-noun anaphora, reader-engagement markers, over-resolved narrative ambiguity, under-subordinated clause packing) and a Spanish-specific patterns section; reconciled into a single v2.11.0 release. Full detail in `SKILL.md`'s Changelog (this README's version history was not updated in real time for these two runs - backfilled here).
- **2.9.0** - Added patterns #34 (narrow vocabulary range / missing hapax legomena) and #35 (flat sentence-length cadence / low burstiness) from stylometric research; added a French-specific patterns section (typography, AI vocabulary, anglicized calques); added a scope note distinguishing genuine editing from detector-evasion tricks; enriched the personality section with two techniques grounded in the same research. 35 patterns total.
- **2.8.2** - Replaced the full before/after example with a first-person Lisbon trip recap. The after now keeps the same topic, perspective, and rough length as the before while removing the AI tells without becoming clipped or slogan-like. No change to the 33 patterns.
- **2.8.1** - Added cross-agent installation docs, optional Claude Code plugin packaging, and a compact secondhand-text false-positive guard. No change to the 33 patterns.
- **2.8.0** - Added style/cadence patterns #31-33 for manufactured punchlines, aphorism formulas, and conversational rhetorical openers; expanded #20 to catch offer-to-continue chatbot closers. 33 patterns total.
- **2.7.0** - Added pattern #30 (diff-anchored writing); made em/en dashes a hard cut rather than "overuse"; expanded #21 to cover speculative gap-filling ("maintains a low profile"). 30 patterns total.
- **2.6.0** - Cleanup pass: consolidated the duplicated workflow sections, gated the personality guidance to content where voice is wanted, removed the model-fingerprinting subsection, and condensed the worked example. No change to the 29 patterns.
- **2.5.1** - Added a passive-voice / subjectless-fragment rule, raising the total to 29 patterns
- **2.5.0** - Added patterns for persuasive framing, signposting, and fragmented headers; expanded negative parallelisms to cover tailing negations; tightened wording around em dash overuse; fixed frontmatter wording to use "filler phrases"
- **2.4.0** - Added voice calibration: match the user's personal writing style from samples
- **2.3.0** - Added pattern #25: hyphenated word pair overuse
- **2.2.0** - Added a final "obviously AI generated" audit + second-pass rewrite prompts
- **2.1.1** - Fixed pattern #18 example (curly quotes vs straight quotes)
- **2.1.0** - Added before/after examples for all 24 patterns
- **2.0.0** - Complete rewrite based on raw Wikipedia article content
- **1.0.0** - Initial release

## License

MIT
