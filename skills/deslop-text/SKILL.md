---
name: deslop-text
description: Review written text (landing page copy, idea writeups, emails, any prose) for AI-generated writing patterns and fix them. Run after drafting any text a human will read.
---

You are reviewing written text for AI-generated writing patterns. These are the word choices, sentence constructions, and structural habits that make text immediately recognisable as machine-generated. The goal is text that reads as if a specific human wrote it with a specific point to make.

## How to run this review

1. Identify the target. If the user specified a file, read it. If they pasted text, use that. If neither, ask.
2. Run every check in the **30 warning signs** below against the text.
3. For each violation found, cite the specific phrase or sentence and state which warning sign it triggers.
4. Suggest a concrete rewrite for each violation. Do not just say "remove this" — show what the sentence becomes.
5. Report findings grouped by severity:
   - **High** — patterns that are instant AI tells (W1 filler phrases, W5 marketing language, W6 generic openings, W9 paired adjectives, W15 excited-to-announce)
   - **Medium** — patterns that weaken the writing even when not obviously AI (W3 em-dashes, W7 passive voice, W8 hedging, W11 mechanical transitions, W26 uncontracted forms)
   - **Low** — statistical patterns that only matter in aggregate (W20 "very", W28 repetitive words, W29 sentence length uniformity)
6. End with a count: "X violations found across Y of 30 checks."
7. If the user asks you to fix the text (not just review), apply all rewrites and present the cleaned version.

---

## The 30 warning signs

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

Contrastive framing where the negation adds nothing. "This is not about speed, it is about reliability" — just say "This is about reliability."

Look for: "it is not X, it is Y", "this is not about X, it is about Y", "not X — Y", "less about X, more about Y".

Fix: say what it is directly. Cut the negation.

### W3 · Em-dash overuse

Dashes bolting parenthetical asides onto sentences. One em-dash per document is fine. Three or more is a pattern.

Flag if: more than one dash-delimited aside per paragraph, or more than 3 em-dashes in the full document.

Fix: if the aside matters, give it its own sentence. If not, cut it.

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

Text that refers to itself.

Target phrases: "In this post...", "As we discussed above...", "Let's explore...", "In this article...", "As mentioned earlier...", "Below, we'll cover..."

Fix: delete. The reader knows they are reading the post.

### W11 · Mechanical transitions

Formulaic transition words used to connect paragraphs.

Target: "Furthermore", "Moreover", "Additionally", "In conclusion", "That said", "With that in mind", "Having established that", "It is also worth mentioning".

Fix: connect ideas with a sentence that earns the transition, or just start the next paragraph without one.

### W12 · Bold emphasis in body copy

`<strong>` or `<b>` wrapping a short phrase inside a paragraph to highlight a key selling point: "with **zero configuration**", "in **days rather than months**".

Flag if: 2+ paragraphs use this, or 1 instance appears in the hero subheadline.

Fix: rewrite so emphasis comes from sentence position. Or give the phrase its own line.

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

Same distinctive word (5+ characters) repeated 3+ times within a short span (~500 characters). Excludes common stopwords.

Fix: use a synonym or restructure.

### W29 · Sentence length uniformity

4+ consecutive sentences all within 30% of their mean word count. AI tends to produce metronomic sentence lengths; real writing varies.

Fix: vary sentence length. Mix short and long. A three-word sentence after a complex one creates rhythm.

### W30 · Heading emoji

Decorative emoji at the start of markdown headings: "## Getting Started", "### Key Takeaways".

Fix: remove the emoji from the heading.

---

## Severity classification

**High** (instant AI tells — fix these first):
W1 (filler phrases), W2 ("not X, it is Y"), W5 (marketing language), W6 (generic openings), W9 (paired adjectives), W15 (excited-to-announce), W16 (whether you're X or Y), W17 (faux-conversational pivots), W21 (corporate cliches), W24 (triple-value lists)

**Medium** (weaken the writing):
W3 (em-dashes), W4 (rhetorical questions), W7 (passive voice), W8 (hedging), W10 (meta-references), W11 (mechanical transitions), W12 (bold emphasis), W13 (scare quotes), W14 (section-end summaries), W18 (exclamation clusters), W19 (repetitive "You"), W22 (hashtags), W23 (emoji), W25 (corporate slang), W26 (uncontracted forms), W30 (heading emoji)

**Low** (statistical — matter in aggregate):
W20 ("very"), W27 (typographic quotes), W28 (repetitive words), W29 (sentence length uniformity)

---

## Principles

- Every rewrite must preserve the original meaning. Removing slop is not an excuse to change what the text says.
- When fixing W5 (marketing language), the replacement must be specific and factual. "Powerful" cannot just become "strong" — it must become a concrete claim.
- When fixing W2 ("not X, it is Y"), keep the Y. The positive statement is almost always the one that matters.
- When multiple violations overlap in one sentence, rewrite the whole sentence once rather than fixing each pattern individually.
- A clean text is not a bland text. The goal is writing with a specific voice and specific claims, not writing with all personality removed.
