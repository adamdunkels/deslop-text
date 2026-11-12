---
name: deslop-text
description: Review written text (landing page copy, idea writeups, emails, any prose) for AI-generated writing patterns and fix them. Run after drafting any text a human will read.
---

You are reviewing written text for AI-generated writing patterns. These are the word choices, sentence constructions, and structural habits that make text immediately recognisable as machine-generated. The goal is text that reads as if a specific human wrote it with a specific point to make.

**This review is advice.** A pattern is worth fixing when it makes the piece worse for its reader. Never trade a clear sentence for a warning-free one; if the text is clear and a check fires, say so and leave it. A count of zero violations says nothing about whether the piece is good.

## How to run this review

1. Identify the target. If the user specified a file, read it. If they pasted text, use that. If neither, ask.
2. Run every check in the **43 warning signs** below against the text.
3. For each violation found, cite the specific phrase or sentence and state which warning sign it triggers.
4. Suggest a concrete rewrite for each violation. Do not just say "remove this" — show what the sentence becomes.
5. Report findings grouped by severity:
   - **High** — patterns that are instant AI tells (W1 filler phrases, W5 marketing language, W6 generic openings, W9 paired adjectives, W15 excited-to-announce)
   - **Medium** — patterns that weaken the writing even when not obviously AI (W3 em-dashes, W7 passive voice, W8 hedging, W11 mechanical transitions, W26 uncontracted forms)
   - **Low** — statistical patterns that only matter in aggregate (W20 "very", W28 repetitive words, W29 sentence length uniformity)
6. End with a count: "X violations found across Y of 43 checks."
7. If the user asks you to fix the text (not just review), apply all rewrites and present the cleaned version.

---

## The 43 warning signs

### W1 · Filler phrases

Phrases that add no meaning. Delete them or rewrite the sentence without them.

Target phrases:
- "it's worth noting", "it bears mentioning", "it goes without saying"
- "at the end of the day", "moving forward", "when all is said and done"
- "delve into", "navigate" (used metaphorically), "underscore" (as emphasis verb)
- "leverage" (as a verb), "utilize" (instead of "use")
- "nuanced", "tapestry", "landscape" (used metaphorically)
- "not only X but also Y"
- "holistic", "robust", "cutting-edge"

### W2 · "Not X, it is Y" constructions

Contrastive framing where the negation adds nothing. The positive statement carries the meaning; the negation is just runway.

The pattern takes many forms:
- Single sentence: "This is not about speed, it is about reliability."
- Split across sentences: "It's not about speed. It's about reliability."
- Inverted/rhetorical: "Speed? No. Reliability."
- With contractions: "It's not one big giveaway. It's a pile of small ones."
- Softer forms: "less about X, more about Y"

Flag any adjacent sentence pair where one negates and the next affirms the same subject, regardless of exact phrasing.

Fix: say what it is directly. Cut the negation.

### W3 · Em-dash overuse

Dashes bolting parenthetical asides onto sentences. In customer-facing copy (landing pages, blog posts), the threshold is zero.

Flag if: any em-dash appears in customer-facing copy (landing pages, blog posts). In internal documents, flag if more than one dash-delimited aside per paragraph, or more than 3 em-dashes in the full document.

Fix: if the aside matters, give it its own sentence or use a semicolon. If not, cut it.

### W4 · Rhetorical questions

Questions used as section openers or transitions rather than genuine inquiry. "What if you could automate your entire workflow?"

Flag if: more than one rhetorical question per 500 words.

Exception: do NOT flag "Question? Answer." pairs where the sentence immediately following the question is a direct answer to it. This is intentional structure (e.g., "How did we solve this? We built a simulator."). Only flag rhetorical questions that are standalone openers or transitions with no direct answer following.

Fix: merge the question and answer into a single declarative sentence, or convert to a "To [verb]..." construction. Never delete just the question and leave the answer orphaned as a non-sequitur statement.

### W5 · Marketing language

Adjectives that sell rather than describe.

Target words: "powerful", "seamless", "revolutionary", "game-changing", "cutting-edge", "best-in-class", "world-class", "next-generation", "innovative", "groundbreaking", "transformative".

Fix: replace with a specific, factual description. "Powerful search" becomes "search that handles 10M records in under 200ms."

### W6 · Generic openings

Opening sentences that could begin any article on any topic.

Target patterns:
- "In today's [connected/digital/fast-paced/modern] world..."
- "As we all know..."
- "Have you ever wondered..."
- "Imagine [a world where/if you could]..."
- "[Industry] is evolving rapidly..."

Fix: start with the specific claim, finding, or situation.

### W7 · Passive voice as habit

Consistent use of passive constructions where active voice would be clearer.

Look for: "was [verb]ed", "is being [verb]ed", "has been [verb]ed", "it was found", "it was determined", "it can be seen".

Flag if: passive constructions exceed 20% of sentences.

Fix: name the actor. "It was found that..." becomes "We found..."

### W8 · Excessive hedging

Qualifying every statement into meaninglessness.

Target patterns: "it seems like", "it appears that", "it could be argued", "one might say", "it is possible that", "arguably", "perhaps", "in some ways".

Flag if: more than 2 hedging phrases per 500 words.

Fix: commit to the claim or cut the sentence.

### W9 · Paired adjectives with "yet" or "and"

"Simple yet powerful", "elegant and robust", "lightweight but comprehensive".

Fix: pick the stronger adjective. Drop the pairing.

### W10 · Meta-references

Text that narrates its own structure instead of just having structure.

Third-person/impersonal forms: "In this post...", "As we discussed above...", "Let's explore...", "In this article...", "As mentioned earlier...", "Below, we'll cover..."

First-person forms: "I grouped them into three tiers based on...", "I've organized these by...", "I read through this list and realized...", "I want to walk you through..."

Both do the same thing: tell the reader about the article's organization rather than letting the organization speak for itself.

Fix: delete. The reader knows they are reading the post. If the structure is clear, you don't need to announce it.

### W11 · Mechanical transitions

Formulaic transition words used to connect paragraphs.

Target: "Furthermore", "Moreover", "Additionally", "In conclusion", "That said", "With that in mind", "Having established that", "It is also worth mentioning".

Fix: connect ideas with a sentence that earns the transition, or just start the next paragraph without one.

### W12 · Bold emphasis in body copy

`<strong>` or `<b>` wrapping a short phrase inside a paragraph to highlight a key selling point: "with **zero configuration**", "in **days rather than months**".

Flag if: 2+ paragraphs use this, or 1 instance appears in the hero subheadline.

Fix: rewrite so emphasis comes from sentence position. Or give the phrase its own line.

Exception: bold lead-ins on bullet-list items. `- **Term.** rest of the bullet` is a structural list convention (naming the concrete thing the bullet is about), not decorative emphasis inside running prose. Check whether the bold text is a list item's own label (not flagged) or mid-sentence emphasis inside a paragraph (flagged).

### W13 · Scare quotes

Quotation marks used for emphasis or irony around ordinary words, not actual quotations. The tool "seamlessly" integrates.

Fix: choose a better word. Drop the quotes.

### W14 · Section-end summaries

Closing a section by restating what was just said. The last sentence of a section paraphrases the first sentence or heading.

Fix: delete. Move on.

### W15 · "Excited to announce/share" openers

"We're excited to announce...", "I'm thrilled to share...", "We're proud to present...".

Fix: state what happened. "We shipped X" not "We're excited to announce X."

### W16 · "Whether you're X or Y" false inclusivity

"Whether you're a startup founder or an enterprise CTO...", "Whether you're just getting started or scaling to millions..."

Fix: pick the actual audience and speak to them directly.

### W17 · Faux-conversational pivots

"Here's the thing:", "Let me be clear:", "The truth is:", "Look:", "So here's what happened:".

Fix: delete the pivot. Start with the substance.

### W18 · Exclamation mark clusters

Multiple exclamation marks in close proximity.

Flag if: more than 1 in any paragraph, or more than 3 in the full document.

Fix: remove all but the one that matters most.

### W19 · Repetitive "You" sentence starters

Multiple consecutive sentences or paragraphs starting with "You".

Flag if: 3+ consecutive sentences begin with "You".

Fix: vary sentence structure. Lead with the action, result, or situation.

### W20 · The word "very"

"Very" weakens specificity. "Very fast" is less precise than "fast" or a specific measurement.

Fix: delete "very" or replace with a specific descriptor.

### W21 · Corporate cliches

Phrases that sound authoritative but say nothing specific.

Target: "think outside the box", "move the needle", "growth mindset", "digital transformation", "synergy", "ecosystem", "paradigm shift", "disruptive", "thought leader", "best practices", "deep dive" (as a noun), "double down", "circle back", "take it to the next level", "game changer", "mission-critical".

Fix: replace with a specific, concrete statement.

### W22 · Hashtag blocks

Blocks of 2+ `#CamelCase` hashtags appended to text.

Fix: delete the hashtag block.

### W23 · Emoji as emphasis

Clusters of decorative emoji (rocket, fire, sparkle, lightbulb, star, checkmark, pointing finger) used for energy in marketing text.

Flag if: 2+ emphasis emoji appear.

Fix: delete the emoji. Let the words carry the weight.

### W24 · Triple-value lists

Three abstract virtues listed in "X, Y, and Z" form: "excellence, collaboration, and innovation". Sounds principled, says nothing concrete.

Fix: pick the one that matters and say something specific about it.

### W25 · Informal corporate slang

Metaphorical business jargon: "circle back", "low-hanging fruit", "boil the ocean", "bandwidth" (used metaphorically), "deep dive", "touch base", "move the needle", "table this", "unpack this", "lean into".

Fix: say what you mean in plain language.

### W26 · Uncontracted forms

"It is", "do not", "is not", "we are", "they have" used consistently with zero contractions anywhere. Produces stiff, formal prose.

Flag if: 2+ uncontracted forms exist and no contractions appear in the entire text.

Fix: use contractions. "It is" becomes "it's", "do not" becomes "don't".

### W27 · Typographic quotes

Curly/smart quotes and smart apostrophes instead of straight quotes. Keyboards produce straight quotes; AI models often output curly ones.

Fix: replace curly quotes with straight quotes.

### W28 · Repetitive word use

Same distinctive word (5+ characters, excluding stopwords) appearing too often. Check two levels:

- **Local clustering**: same word 3+ times within a single paragraph or short passage.
- **Document saturation**: same word appearing more than 8 times per 2000 words, regardless of spacing. A word can pass every local check while still dominating the piece.

Fix: use a synonym, restructure, or cut redundant sentences. For document-level saturation, the fix is often that the text is making the same point repeatedly (see also W31).

### W29 · Sentence length uniformity

4+ consecutive sentences all within 30% of their mean word count. AI tends to produce metronomic sentence lengths; real writing varies.

Fix: vary sentence length. Mix short and long. A three-word sentence after a complex one creates rhythm.

### W30 · Heading emoji

Decorative emoji at the start of markdown headings: "## Getting Started", "### Key Takeaways".

Fix: remove the emoji from the heading.

### W31 · Repeated thematic points

The same idea restated in different words at multiple points in the text. AI tends to re-derive its thesis in every section, producing multiple phrasings of one point rather than advancing the argument.

Example — these three sentences from different sections all say the same thing:
- "Each pattern is individually forgivable. Stacked together, they're a fingerprint."
- "These don't scream AI on their own... they pile up into a recognizable texture."
- "Any single instance means nothing. But when you see all of them, something feels off."

Flag when: a thematic point (not just a word) appears in substantially similar form more than once. Pay attention to the "[one/single/individual] is [fine/nothing]. [Together/combined/stacked] they [signal/reveal]" structure, but don't limit detection to that template.

Fix: say it once, in the strongest place. Delete or replace the weaker instances with points that advance the argument.

### W32 · "X is a Y problem" categorisation

Headings or sentences that categorise instead of saying something concrete: "Slow OTA updates are a dogfooding problem", "Retention is a pricing problem", "Trust is a documentation problem".

Fix: state the cause or the consequence directly. "OTA gets fast when developers have to wait for it."

### W33 · "What X is missing / gets wrong / can't tell you" headings

A formula heading that frames the section as a gap in something else: "What the test matrix is missing", "What most teams get wrong", "What CI can't tell you".

Fix: name the thing directly. "The versions missing from the test matrix", "The controlled environment trap".

### W34 · Machinegun sentences

Three or more short declarative sentences in a row, each under ~10 words. "X is true. Y follows. Z happens. That's the point." Reads as robotic and is a reliable AI tell.

Fix: combine with commas, subordinate clauses, or semicolons. A deliberate two-sentence reframe is fine; a four-sentence barrage is not.

### W35 · Repetitive sentence openings

Three or more sentences in a paragraph starting with the same grammatical pattern: "The X gets replaced. The Y gets tuned. The Z gets moved." or "First, we... Then, we... Next, we..."

Fix: combine into one sentence with a list, or vary the subject and structure so consecutive sentences don't mirror each other.

### W36 · Internet clichés

Phrases that were novel online circa 2015-2022 but have been strip-mined by AI models into cliche. They aren't corporate jargon (W21) or filler (W1) — they're internet-native expressions that AI reaches for as if they're still fresh.

Target phrases:
- "you can't unsee it/them"
- "hits different"
- "rent-free"
- "chef's kiss"
- "the quiet part out loud"
- "I'm here for it"
- "tell me you X without telling me you X"
- "let that sink in"
- "this is the way"
- "say it louder for the people in the back"

Fix: say what you actually mean. If the phrase is doing real work, replace it with a specific observation. If it's decoration, delete it.

### W37 · Negative outcome framing in solution sections

Describing what goes wrong for people who lack the product or approach, rather than what goes right for people who have it. Common in solution, outcome, and conclusion sections of blog posts and landing pages.

Target patterns:
- "Without [X], [bad thing happens]" — "Without that infrastructure, a hardware revision is a gamble."
- "Teams that didn't/don't [X] discover/suffer/face..." — "Teams that didn't invest discover the gap at the worst possible moment."
- "If you don't have [X], [consequence]" — negative conditional framing

Exception: problem sections are supposed to describe pain. Only flag this pattern in solution, outcome, or conclusion sections where the text should be pointing forward.

Fix: rewrite as what happens WITH the product/approach. "With that infrastructure in place, a hardware revision becomes routine." The reader should see themselves succeeding, not failing.

### W38 · Authenticity signals

Words AI models reach for to signal sincerity or emphasis that real writers rarely use. They do the same work as W20's "very" but dressed up as candour: the writer asserts they are being genuine instead of just being genuine.

Target words: "honest" (as an intensifier: "the honest answer," "honest starting point," "honest version"), "genuinely", "truly", "actually", "really".

Exception: "honest" used to describe an action the reader should take ("be honest about the difference," "report honestly") is fine. The flag is for "honest" modifying a noun to signal the writer's own sincerity.

Flag if: 2+ instances per 2000 words, or any single post uses the word 3+ times.

Fix: delete the intensifier. "The honest answer" becomes the answer. "The honest starting point" becomes "the starting point." "Genuinely useful" becomes "useful." If the sentence is weaker without it, the sentence is the problem, not the missing word.

### W39 · Parallel contrast templates

Two adjacent sentences with identical grammatical structure where only the subject and object change, creating a perfectly balanced rhetorical contrast. AI models produce these constantly because the symmetry feels like a satisfying conclusion.

Examples:
- "X stops when Y. A stops when B."
- "X works because Y. A works because Z."
- "X is about Y. A is about Z."
- "X runs on Y. A runs on Z."
- "X succeeds through Y. A succeeds through Z."

The template is: "[Subject] [verb phrase] [object/clause]. [Different subject] [same verb phrase] [different object/clause]." Human writers occasionally produce balanced pairs, but AI does it reflexively, especially at paragraph endings and as pull quotes.

Flag if: two adjacent sentences follow the same grammatical template with only the subject/object swapped.

Fix: say it once with both subjects in one sentence, or use a structurally different sentence for the second idea. "Vibe coding works because every iteration is visible. Agentic engineering works because every iteration is verified" becomes "Cross-domain firmware failures are invisible without a test rig, and agentic engineering is how you close the feedback loop that vibe coding's browser can't reach."

### W40 · "Just became" transformation crutch

"[Thing] just became [new thing]" used as a heading or topic sentence to announce a transformation without stating the mechanism that caused it. Example: the heading "The flow map just became something the agents work from" asserts the shift instead of naming what made it happen.

The tell: "just became" does the work a real sentence should do — it lets the writer skip past *why* or *how* and land on the punchy-sounding result. It reads as a scene transition, not a claim.

Flag if: "just became", "just turned into", "just started [verb]ing" opens a heading, topic sentence, or paragraph, and the mechanism isn't in the same sentence.

Exception: a literal, dateable claim where "just became" states an actual fact the post goes on to support (e.g., a thesis title asserting something recently became true, defended across the whole piece) is not the crutch — the crutch is the *unexplained* transformation used as connective tissue. When in doubt, ask whether the sentence would still make its point with "just" deleted and no other change; if so, "just became" was decoration, not a claim.

Fix: name the actor and the mechanism. "The flow map just became something the agents work from" becomes "A written-down flow states what the product does for the person using it, so an agent can build against it" (say what makes it true, not that it happened).

### W41 · Invented day-of-week specificity

Attaching a specific weekday to a narrative example or incident when the day is invented rather than real, to manufacture a false sense of concreteness. "It landed on a wednesday." "The bug shipped on a Tuesday." The day does no work: swap it for any other weekday and the sentence loses nothing, which is the tell that it was never a fact, just texture.

Flag if: a specific day of the week (Monday–Sunday) is attached to an invented example, walkthrough, or incident narrative, and the day is not drawn from an actual recorded date, a real event, or the post's own established release cadence.

Exception: a weekday used as an idiom for a recurring point in the work week ("what does a VP of Engineering do on Monday morning?") or as part of a real, named release cadence the post has already established (a team that genuinely ships on a fixed weekly day) is not fabricated specificity — it is doing idiomatic or structural work, not manufacturing a fake fact. The flag is for a day bolted onto a one-off invented anecdote to make it sound like a specific, remembered event.

Fix: delete the day, or replace it with detail that actually carries information (how long after the commit, how many changes had landed on top of it, what the release gate was).

### W42 · Personification of an abstract or inanimate subject

Dressing up a plain relationship in agency the subject doesn't have. A product, a screen, a system, or a UI element does not hold intent, effort, or obligation — only a person or a team does.

Target patterns: "X earned/earns Y" ("the flows the bulb earned"), "X owes Y" ("what the product owes the person using it"), "X tries to Z" ("the tile tries to draw a brightness"), "X teaches/learns Z" applied to a non-learning system ("teach the room tile what a plug reports"), and similar verbs of intent, effort, obligation, or cognition (wants, decides, knows, cares, remembers) whose subject is a product, screen, flow, or other non-agent.

The tell: these read as natural house vocabulary once one sentence uses one, because the next sentence imitates it — this is why the pattern survives review passes that catch cruder AI-isms. The word compresses an argument about effort or obligation instead of stating the plain mechanism.

Flag if: any of the above verbs has a subject that is a product, screen, system, flow, or other thing incapable of intent, effort, obligation, or cognition.

Exception: a verb describing literal software or hardware behavior is not personification even though it sounds like an action verb — "the flow runs," "the cloud stores," "the device reports," "the test expects an input" (a test assertion literally expects, in the technical sense) are all fine. "Tries" and "teaches" specifically have large legitimate technical senses ("the client tries three times before failing," "teach the parser a new field format" describing an actual code change) and are not banned words; the flag is only the case where the verb stands in for a single deterministic action and adds implied effort or pedagogy that isn't in the mechanism ("the tile tries to draw a brightness" describes one synchronous draw call, not a retry loop). The test is whether the verb names a mechanism the system executes or an intent/effort/obligation/cognition state it cannot hold. Re-check a borrowed verb against its *new* sentence's subject before reusing it — a word that passed this check for one subject (a test flow) does not automatically pass for a different subject (a rendering element) three sentences later.

Fix: name the literal mechanism, or flip the subject to the person or team who actually holds the intent, effort, or obligation. "The flows the bulb earned" becomes "the flows written for the bulb." "What the product owes the person using it" becomes "what the person using the product should get" or "what the product does for the person using it." "The tile tries to draw a brightness" becomes "the tile draws a brightness" (state the mechanism, drop the implied effort).

### W43 · Comma-and clause stitching

Two independent clauses joined by ", and" where the second is simply the next fact rather than a consequence, complication, or continuation of the first. "There are a lot of them, and they change every release." Both halves are complete claims with no real relationship between them; the comma-and is there because a full stop felt too abrupt, not because the join means anything.

Flag if: a sentence has a comma before "and" joining two independent clauses, and each clause reads as a complete, self-sufficient sentence on its own with nothing lost by splitting them.

Exception: a join where the second clause genuinely depends on, resolves, or is caused by the first is fine and often reads better joined — "The bug shipped, and nobody caught it for a week" is one thought, and splitting it flattens the surprise. The test is whether "and" is doing real logical work (consequence, contrast, an accumulating list building toward a beat) or standing in for a period. This is a judgment call: the shape is too common in ordinary English to flag mechanically.

Fix: split into two sentences ("There are a lot of them. They change every release.") Or cut whichever clause repeats something already said.

---

## Severity classification

**High** (instant AI tells — fix these first):
W1 (filler phrases), W2 ("not X, it is Y"), W5 (marketing language), W6 (generic openings), W9 (paired adjectives), W15 (excited-to-announce), W16 (whether you're X or Y), W17 (faux-conversational pivots), W21 (corporate cliches), W24 (triple-value lists), W32 ("X is a Y problem"), W33 ("What X is missing" headings), W34 (machinegun sentences), W35 (repetitive sentence openings), W37 (negative outcome framing), W39 (parallel contrast templates), W40 ("just became" transformation crutch), W41 (invented day-of-week specificity)

**Medium** (weaken the writing):
W3 (em-dashes), W4 (rhetorical questions), W7 (passive voice), W8 (hedging), W10 (meta-references), W11 (mechanical transitions), W12 (bold emphasis), W13 (scare quotes), W14 (section-end summaries), W18 (exclamation clusters), W19 (repetitive "You"), W22 (hashtags), W23 (emoji), W25 (corporate slang), W26 (uncontracted forms), W30 (heading emoji), W36 (internet clichés), W38 (authenticity signals), W42 (personification of an abstract or inanimate subject), W43 (comma-and clause stitching)

**Low** (statistical — matter in aggregate):
W20 ("very"), W27 (typographic quotes), W28 (repetitive words), W29 (sentence length uniformity), W31 (repeated thematic points)

---

## Principles

- Every rewrite must preserve the original meaning. Removing slop is not an excuse to change what the text says.
- When fixing W5 (marketing language), the replacement must be specific and factual. "Powerful" cannot just become "strong" — it must become a concrete claim.
- When fixing W2 ("not X, it is Y"), keep the Y. The positive statement is almost always the one that matters.
- When multiple violations overlap in one sentence, rewrite the whole sentence once rather than fixing each pattern individually.
- A clean text is not a bland text. The goal is writing with a specific voice and specific claims, not writing with all personality removed.
