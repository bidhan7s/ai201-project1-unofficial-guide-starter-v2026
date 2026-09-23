# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**

I chose 4 out of 5 because all five questions have answers somewhere in my
documents, so the retrieval system should find the right information most of
the time. I didn't require 5 out of 5 because retrieval may miss the best chunk
for one question, so 4 out of 5 is still a strong target without requiring
perfect retrieval.

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**

This is a RAG system, so the answers are supposed to be grounded in the
documents that were retrieved. I chose every answer because naming a source
lets someone see where the information came from. If an answer doesn't name any
source, it becomes harder to verify whether the response is actually based on
my corpus.

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

<!-- The five questions are the ones in `OUT_OF_SCOPE` at the bottom of
     `questions.py`, and `run_eval.py` puts them through the gate and writes
     what happened into your run log. Swap them for your own if you'd rather —
     just keep five of them, or the "4 of 5" above has nothing to be 4 of. -->

**Why this target:**

The relevance gate is there to stop the system from answering questions when
my documents don't contain relevant information. I chose 4 out of 5 because I
want it to reject most unrelated questions, but I allow one failure because the
similarity scores for in-scope and out-of-scope questions may not separate
perfectly.

---

## 4. Something about your chunks

At least 4 of 5 sampled chunks should stay focused on one main topic. A chunk
passes when the information in it relates to that topic and fails when it mixes
unrelated topics.

**Why this target:**

I chose this target because focused chunks should help retrieval avoid unrelated
information. I chose 4 out of 5 because I want a strong standard while allowing
one imperfect chunk.

---

## 5. Your choice

I choose 5 out of 5. For an answer to pass, at least one source document named
in the answer must contain information that supports the answer's main factual
claim. If multiple sources are named, I only require at least one of them to
support the main answer.



**Why this target:**

I chose this target because my five test questions are based on facts that I
know exist in the corpus, so I expect every answer to have at least one source
that actually supports its main claim. A source should provide evidence for the
answer, not just be related to the same general topic.


---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
