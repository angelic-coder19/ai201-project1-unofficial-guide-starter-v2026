# The Unofficial Guide

<!-- Replace this line with your name and which corpus you picked. -->

> **This file is your submission.** Fill it in as you go — most sections get
> written during the milestone that produces them, not at the end.
>
> How the starter works, and every command you'll need, is in `RUNNING.md`.
> Leave that file alone.
>
> **Paste everything as text.** No screenshots, no video. A typed table gets
> full credit; a picture of the same table gets none.
>
> Delete these instruction blocks as you replace them. The `<!-- -->` comments
> are notes to you and don't show up when the page renders — you can leave them
> or remove them.

---

# Unit 1

## What This Does

     I picked the city_guides corpus, which contains detailed information about different cities, modes of transportation, physical features, places to see, the time to visit and the varying ease with wich to access each city . My system is designed to answer questions related to the different cities, providing accurate and relevant information based on the documents in the city_guides corpus.


## Chunking Strategy

**Chunk size: 200**
**Overlap: 50**

<!-- What about YOUR documents made you pick these numbers? Short posts and
     long sectioned guides don't want the same chunking, and "800 seemed
     reasonable" earns nothing. Point at something you noticed when you read
     the documents in Milestone 1.

     If you changed your mind partway through, say so and say why. That's worth
     more than pretending you got it right first time.

     Milestone 3. -->
I played around with a number of chuck sizes, tested the results with different questions and I ultimately decided to use 500 characters as the chunck size. I chose this because  because each chunk had roughly one specific point of information. Given that I used the city guides corpus, a 500 character chunk size worked well because each chunk focused on one aspect of a city's guide. a 100 character overlap made sure that information was not to crowded from other unrelated chuncks and was also enough to maintain context from one chunk to the next.
One huge improvement I noticed was that 500 character chunk size allowed one specific question to be answered accurately: both smaller and larger chunk sizes failed to find the specific answer within the corpus inspite of the distance being well below the cut off. 

<!-- Five chunks, pasted as text. Label each one and name the file it came from
     AND the function that produced it — the grader checks your code against
     what you claim here.

     `python app.py chunks -n 5` prints all three for you. Copy them straight
     across.

     Milestone 3. -->

**Chunk 1** — source: `` — produced by: ``

```
# Getting around the region with limited mobility

An honest assessment rather than a promotional one. Some of these places are
difficult and it is better to know in advance.

## Straightforward

**Thornby Wells** is the easiest town in the region. It is flat, compact, and
everything is within three minutes of everything else. Parking is free for two
hours anywhere in town and the station is central. The pump room and gardens
are level throughout.

**Marchwood** has a modern tram network with le
```

**Chunk 2** — source: `` — produced by: ``

```
cheese and little else, and it closes at 4pm. Bring supplies; this is not a place with options.

## What to see

The valley itself is the attraction. The footpath network is dense and well marked, an
```

**Chunk 3** — source: `` — produced by: ``

```
ital is in Brightwater; there is
a minor injuries unit locally with limited hours.
```

**Chunk 4** — source: `` — produced by: ``

```
an climb for £2. The old trackbed walk runs six miles to the next village along an easy gradient and is the best half-day here.

## Where to stay

Two inns on the square and a handful of rooms above the pubs. Booking ahead matters between May and September andnot at all otherwise. There is no accommodation of any kind within four miles of the town in either direction.

## When to goJ

Late spring and early autumn. The Saturday market runs year-round but is much reduced from November to February
```

**Chunk 5** — source: `` — produced by: ``

```
# Getting around the region

## The railway

The line runs along the river valley, connecting Brightwater to the regional
hub in 50 minutes. Eleven services a day on weekdays, six on Sundays. The line
north of Brightwater closed in 1963 and everything beyond it is bus or car.

Tickets are cheaper booked the day before than on the day, and considerably
cheaper than that booked a week ahead. There is no ticket office at
Brightwater station outside weekday mornings; the machine on the platform take
```

## Sample Answer

<!-- One complete question and answer, pasted as text, with the source line
     visible. Milestone 4. -->

**Question: How 
long does it take to drive from Brightwater to Corry Vale?**

**Answer: Driving from Brightwater takes 35 minutes on a good road as far as the valley mouth and then 20 more on a poor one.**

```
```

**My relevance cutoff:**

<!-- The number you set in config.py, and how you got there.

     You ran five questions your corpus covers and the five in OUT_OF_SCOPE
     that it clearly doesn't, and wrote down the best distance for each. What
     did those two groups look like? Where was the gap? Put the actual numbers
     here — the table below wants all ten rows.

     Milestone 4. -->

| Question | In corpus? | Best distance |
|"What city is the considered the regional hub where all trains meet?|Yes|0.568|
|  |  |  |

## How I Used AI

<!-- Two specific moments. For each: what you asked for, what came back, and
     what you changed about it.

     "I asked Claude to write the chunking function from my notes. It ignored
     the overlap, so I added that myself" is the level of detail we're after.
     "I used AI to help me code" is not.

     Milestone 5. -->

**1.**
I asked Copilot to tell me what the best chunk size I could use given the city_guides copus I was using. It recommended 800 and with an overlap of 150. This was the exact initial configuration. I ignored it and tried out several other configuarations: 400, 1000, 180, 500 and 200. I was not satisfied with the size of the chunks and how much extra scope they had. So I decided to experiment with all the sizes I listed. This allowed me to discover that one of my hardest questions was answered accurately with a size of 200. I would have not found this out if it just accepted the initial recommendation. 

**2.**
Since I had ran different trials with different chuk sizes and overlaps, I decided to automate the filling in of the answers and into the readme. I thought this would be duplication of work that I already did when I did my trials. I knew what the distances were for each of my questions because I tried to see how a new chunk size or overlap would affect the responses. Since learning had already happened, I was okay with having copilot automate the repetitive queries and data entry.

<!-- ── Stretch features ─────────────────────────────────────────────────────
     Doing one? Say so here BEFORE you start. A feature this README never
     claims earns nothing.
     ───────────────────────────────────────────────────────────────────────── -->

---

# Unit 2

<!-- These sections get ADDED to what's already above. Don't delete or rewrite
     unit 1 — the point is that someone can see what you said before you knew
     how it went. -->

## Run Log — Before

<!-- Your five criteria, three runs each. `python run_eval.py --label before`
     runs the questions, puts the OUT_OF_SCOPE ones through the gate, and
     writes it all into results/ for you. Targets come from criteria.md; the
     verdict column is your call.

     Criterion 3 is measured in one deterministic pass rather than three, so
     the same number goes in all three run columns. That's correct, not lazy.

     Milestone 1. -->

| Criterion | Target | Run 1 | Run 2 | Run 3 | Verdict |
|---|---|---|---|---|---|
| 1. Retrieved chunk contains the answer | 4 of 5 | 5 of 5 | 5 of 5 | 5 of 5 | MET |
| 2. Every answer names a source | 5 of 5 | 5 of 5 | 5 of 5 | 5 of 5 | MET |
| 3. Gate stops out-of-corpus questions | 4 of 5 | 5 of 5 | 5 of 5 | 5 of 5 | MET |
| 4. Complete chunks | 4 of 5 | 1 of 5 | 1 of 5 | 1 of 5 | MISSED |
| 5. Correct in-corpus answers | 4 of 5 | 4 of 5 | 4 of 5 | 4 of 5 | MET |

<!-- Underneath, paste the REAL output for each criterion from one of your
     runs — the actual text your system produced, not a description of it.
     Name the file and function that produced it. -->

The run was produced by `run_eval.py::main`, using `store.py::search` and
`chunker.py::split_documents`, with a 0.6 relevance cutoff. The five best
distances were 0.309, 0.568, 0.439, 0.385, and 0.487. The gate refused all
five out-of-scope questions; their distances ranged from 0.830 to 0.988.

The answers for Corry Vale, Marchwood, Givens Mill, and the weather-dependent
walking paths matched the expected answers and named sources. For example:

> Marchwood is considered the regional hub where every railway line meets.
> This information comes from `guide_marchwood.md`.

The Kestrelford answer was the only failure. It said that the documents did
not provide a complete list of attractions, even though `guide_kestrelford.md`
was retrieved.

## Verdicts

<!-- MET or MISSED for each of the five, against the target you wrote last
     unit — not a new one. Plus a sentence on how you decided. That sentence
     matters most where it was close.

     If your target said 4 of 5 and your runs came out 4, 3, 4, that's a MISS.
     The target has to hold, not show up occasionally.

     Milestone 2. -->

| # | Criterion | Verdict | How I decided |
|---|---|---|---|
| 1 | Retrieved chunk contains the answer | MET | All five questions retrieved a relevant source chunk, exceeding the target of four. |
| 2 | Every answer names a source | MET | All fifteen generated answers named at least one source document. |
| 3 | Gate stops out-of-corpus questions | MET | The gate refused 5 of 5 out-of-scope questions, exceeding the target of four. |
| 4 | Complete chunks | MISSED | Only 1 of 5 sampled chunks ended at a complete thought; several ended mid-word or mid-sentence. |
| 5 | Correct in-corpus answers | MET | Four of the five questions matched their expected answers in every run. |

## Diagnoses

<!-- For each miss: which stage caused it, and how. The stage alone isn't
     enough — you need the mechanism.

     Not a diagnosis: "Question 3 didn't work."
     A diagnosis:     "Question 3 asks about laundry costs. The answer is in
                       one sentence that got split across two chunks, so
                       neither chunk on its own contains it."

     The five stages: loading → chunking → embedding → retrieval → generation.

     Look for a pattern. If three misses all ask about numbers, that's one
     problem, not three.

     Missed nothing? Say so, then say honestly whether your targets were set
     low, and which one you'd tighten and to what.

     Milestone 3. -->

Criterion 4 was missed at the chunking stage. The current 500-character
chunks often preserve the relevant topic, but fixed-size splitting cuts some
sentences at the boundary. Kestrelford was not a retrieval failure: its source
was retrieved, but generation produced an incomplete answer. That makes the
Kestrelford failure primarily a generation issue.

## The Improvement

**What I changed:**

I compared a 200-character chunk size with 50-character overlap against the
500-character size with 100-character overlap. The smaller chunks returned
the exact Kestrelford attractions answer, but simple questions such as Corry
Vale became less reliable. I kept 500/100 because it answered 4 of 5 test
questions and was the better overall balance.

**Why I picked it:**

The city guides contain short sections with related facts. A 500-character
chunk usually keeps one focused point together, while 100 characters preserve
some context across boundaries. The 200/50 setting was more precise for one
question but harmed other retrieval results.

<!-- Connect it to a specific diagnosis above in one sentence. If you can't,
     you picked a fix because it sounded impressive. -->

### Run Log — After

<!-- Same format, same five criteria, three runs each.
     `python run_eval.py --label after` -->

| Criterion | Target | Run 1 | Run 2 | Run 3 | Verdict |
|---|---|---|---|---|---|
| 1. Retrieved chunk contains the answer | 4 of 5 | 5 of 5 | 5 of 5 | 5 of 5 | MET |
| 2. Every answer names a source | 5 of 5 | 5 of 5 | 5 of 5 | 5 of 5 | MET |
| 3. Gate stops out-of-corpus questions | 4 of 5 | 5 of 5 | 5 of 5 | 5 of 5 | MET |
| 4. Complete chunks | 4 of 5 | 1 of 5 | 1 of 5 | 1 of 5 | MISSED |
| 5. Correct in-corpus answers | 4 of 5 | 4 of 5 | 4 of 5 | 4 of 5 | MET |

**Did it help?**

Yes, overall. The 500/100 configuration answered four of five in-corpus
questions, named sources in every answer, and refused all five out-of-corpus
questions. The 200/50 configuration was better for Kestrelford alone, but it
made simpler questions such as Corry Vale fail, so I kept the more balanced
setting. Chunk completeness is still below target and needs a structure-aware
split on headings or sentence boundaries.

<!-- Say plainly whether it did, and how you know. If it made things worse,
     say that — a change that backfired, honestly reported, earns full credit
     and is more interesting than one that worked. What matters is that you can
     tell.

     Milestone 4. -->

## What's Still Broken

<!-- For each criterion still missed after your fix: what you'd do about it,
     and why you stopped where you did.

     "I ran out of time" is fine if it's true. Pretending nothing is left is
     not.

     Milestone 5. -->

## What I'd Do Differently

<!-- Knowing what you know now — which of your five criteria would you write
     differently, and why?

     Milestone 5. -->
