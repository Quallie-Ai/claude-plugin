# Project types

Read this at checkpoint 1 (Intake), once the user has named the project type:
what the research is for, intake follow-ups, analyses, findings shape, pitfalls.

Ask the follow-ups the way SKILL.md says to ask everything: one question per
message, your recommendation first, then wait for the answer before the next.
The numbered lists below are the order to ask in, never a form to send whole.
Skip any the data already answers: call `get_project`, `summarize_project` and
`list_analyses` first, and read any analysis the researcher already ran with
`get_analysis`.

These apply to every type:

- Choose a cohort with `list_tags` and `list_participants`. Use
  `filter_participants` (then `get_filter`) only when membership needs a
  transcript read; tags are instant and free.
- Ask `extract_concept` for everything you need in ONE call per question, with
  an open, non-leading instruction. Poll it with `get_extraction`.
- Back every claim with exact wording from `fetch_quotes` (poll `get_quotes`),
  and back the strongest moments with video. At checkpoint 2, only search:
  `find_clips`, read with `get_clip_search`, and check `list_clips` for clips
  that already exist. A search result is a candidate, not a clip: it has no
  clip id and cannot go into a clip embed. Keep the candidates (entry, utterance
  ids, quote) with their theme.
- Create nothing in Quallie.Ai before the outline is approved. At checkpoint 4,
  turn each candidate the approved outline uses into a clip with `create_clip`
  (reuse a clip from `list_clips` when one already covers the moment), and only
  then embed it. Candidates for themes the user dropped are never cut.
- Count how many participants support a finding before you give it a headline.

## Concept testing

Creative and UX evaluation. The research decides which concept, proposition or
design landed, and why, so a team can choose, merge or refine.

Intake follow-ups:

1. Which concepts or stimuli were tested, and how are they labelled in the
   data (A/B/C, names, routes)?
2. Was the order of exposure rotated, or did everyone see them in one order?
3. Which criteria matter most (comprehension, relevance, appeal, credibility,
   likelihood to act)?
4. Is there a winner hypothesis or a concept the client is attached to?

Analyses: one `extract_concept` call that asks, per concept, for first
reaction, what was understood, what appealed, what put people off and any
stated preference, so every concept is read on the same terms. Use
`fetch_quotes` for verbatims per concept and criterion. Use `find_clips` for
the clearest reaction to each concept, ideally one positive and one negative.

Findings shape: a side-by-side comparison of the concepts on the agreed
criteria, then what drove preference, then what to keep, fix or drop in each.
Lead with the overall verdict.

Pitfalls:

- Order effects: the first concept seen often reads as clearest or weakest.
  Note the exposure order when it matters.
- Stated preference is not the same as comprehension. A concept people liked
  but misunderstood is a finding in itself.
- Do not let the client's favourite steer the extraction instruction.

## Journey mapping

CX research. The research maps how people move through an experience, stage by
stage, so a team can see where it breaks and what matters most.

Intake follow-ups:

1. What are the journey stages, as the client names them? If none exist yet,
   should the stages come from the data?
2. Whose journey is it (new customers, churned, a segment)?
3. Is there a stage the client already suspects is broken?

Analyses: one `extract_concept` call that asks for each stage the participant
went through, what triggered it, what went wrong, workarounds, and emotional
highs and lows. Use `filter_participants` when a stage only applies to some
people (for example those who contacted support). Use `find_clips` for the
moment that matters most at each stage.

Findings shape: the stages in order, each with its pain points, its moments
that matter and one clip. Close with the two or three stages to fix first.

Pitfalls:

- Not everyone reaches every stage. Report each stage against the people who
  went through it, not the whole sample.
- A stage list imposed by the client can hide a stage participants actually
  describe. Say so when the data shows one.
- One dramatic story is not a pattern: check how many participants share it.

## Comms & brand

Creative development. The research hears how messaging, a campaign or a brand
really landed: what people took from it, in their own words.

Intake follow-ups:

1. Which campaign, messages or brand assets were shown, and how are they
   labelled in the data?
2. What was the intended takeout of each?
3. Was recall unprompted, prompted, or both?

Analyses: one `extract_concept` call that asks for the takeout in the
participant's words, the language and metaphors they used, what they remembered
unprompted, and any confusion or rejection. Use `fetch_quotes` heavily: in this
type the exact wording is the finding. Use `find_clips` for reactions worth
showing, not describing. When a theme wants several of them joined, note it
in the outline; the reel itself is made with `create_reel` at checkpoint 4,
after the outline is approved and its clips exist.

Findings shape: language and metaphor themes, then intended versus actual
takeout per message, then salience and memorability. Reels and verbatims carry
more weight here than in any other type.

Pitfalls:

- Do not paraphrase the language: quote it. A paraphrase loses the finding.
- Prompted recall inflates memorability. Keep it apart from unprompted recall.
- Strong opinions about the advertising itself can crowd out what the message
  actually communicated.

## New product or service

NPD. The research shows what people need before something is built: unmet
needs, the workarounds they rely on today, and what resonates.

Intake follow-ups:

1. Is this discovery (needs only) or are there early ideas or prototypes to
   react to?
2. Which segments matter, and are they tagged in the data?
3. What decision will the report feed (go or no-go, prioritisation, a brief)?

Analyses: one `extract_concept` call that asks for the job the participant is
trying to do, how they do it today, the workarounds, what frustrates them and
what they would pay or switch for. Compare resonance across segments by
narrowing with tags or `filter_participants` and reading each group's results.
Use `fetch_quotes` so every need has an evidence trail.

Findings shape: needs and workarounds, evidenced, ranked by how widespread and
how painful each is. Then resonance across segments, then the opportunity.

Pitfalls:

- Stated intent ("I would use that") overstates real demand. Weight described
  behaviour and existing workarounds above it.
- A need mentioned once with feeling is not a widespread need. Report counts.
- Keep the participant's problem separate from the client's proposed solution.

## Cultural insights

Ethnography and organisational culture. The research tracks behaviours, values
and how culture shifts across markets, communities or groups.

Intake follow-ups:

1. Which markets, communities or groups are compared, and how are they tagged?
2. Were the interviews in several languages? Should quotes stay in the original
   language, with a translation, or in translation only?
3. Are there hypotheses or themes the client expects to see?

Analyses: one `extract_concept` call across all participants with an open
instruction about behaviours, values and tensions, then read the results per
market or group. Use `fetch_quotes` to keep the analysis verbatim first. Use
`find_clips` for the moments that make a difference between groups visible.

Findings shape: a cross-market or cross-group theme comparison: the shared
themes first, then where groups diverge, each with evidence from each group.

Pitfalls:

- Unequal group sizes skew comparisons. Say how many people stand behind each
  group's finding.
- Do not read a translation's wording as the participant's own metaphor.
- Avoid national stereotypes: describe what these participants said and did.

## Innovation & thought leadership

Foresight and futures. The research draws on first-person accounts and expert
interviews to surface unique points of view and signals of where things are
heading.

Intake follow-ups:

1. Who was interviewed (experts, early adopters, the general public), and are
   the cohorts tagged?
2. What horizon or domain is the foresight about?
3. Is the output for an internal strategy team or for publication?

Analyses: one `extract_concept` call that asks for the change each participant
sees, the evidence they give for it, what is driving it and what they expect
next. Read the results across cohorts to see which signals recur. Use
`fetch_quotes` to keep each point of view attributed and exact.

Findings shape: signals of change across cohorts, each with its drivers and the
points of view behind it. Then the patterns that recur, then the outliers worth
watching.

Pitfalls:

- One articulate expert can dominate. Separate a signal from a single opinion.
- Distinguish what participants observe now from what they predict.
- For a publication, check that quotes are cleared for external use.

## Other

Ask the user to describe the objective of the research in one sentence. Derive
the approach from it: name the decision the report feeds, start from the
closest type above, and say which of its questions, analyses and findings shape
you will borrow. Confirm that plan before running any analysis.
