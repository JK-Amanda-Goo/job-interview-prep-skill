# Question generation

How to build the internal question set for Step 4. The set is derived, not pulled from a bank — it has to fit this round, this seniority, and what this JD actually screens for. Build it, hold it, reveal one question at a time.

## First: the JD's real requirements

Most job descriptions are two or three things that actually matter wrapped in a lot of standard language. Before writing any questions, name the real ones out loud to yourself. Examples:

- A PM JD that lists "data-driven," "cross-functional," "0-to-1," and "customer obsession" is usually really screening for: *has shipped something from nothing*, *can drive a decision without authority*, and *actually talks to users*.
- An eng JD heavy on "scale" and "ownership" is really screening for: *has operated a system in production under load* and *makes the call when on-call*.

At least one **core** question must target each real requirement. That's the difference between a mock that predicts the real interview and one that just fills time.

## Per-round playbooks

### Recruiter / phone screen (usually 30 min)

Screens for: baseline fit, no dealbreakers, real motivation, communication. Not depth.

- Walk me through your background / your resume in a couple minutes.
- Why are you looking to leave? / Why now?
- What do you know about us, and why this role?
- What are you looking for in your next role?
- Compensation expectations; location / work authorization / notice period.
- One light role-fit question ("Have you worked with [core tool/domain]?").

Feedback weight: concision, a clear and non-negative reason for leaving, motivation that sounds specific rather than flattering.

### Hiring-manager interview (45–60 min)

Screens for: can this person do *this* job, how they work, judgment. The core round.

- Resume deep-dive on the one or two experiences closest to this role — "what exactly did *you* do," "what was hard," "what would you do differently."
- "Tell me about a time you..." on each real requirement (owned something end-to-end, handled a disagreement, made a call with incomplete information, dealt with a failure).
- A hypothetical scoped to the actual job ("Your first 90 days here — where do you start?" / "You inherit [situation in the JD] — what do you do?").
- How they operate: prioritization, working with [the function they'll partner with], what they need from a manager.

Feedback weight: "I" not "we," specific decisions and tradeoffs, real numbers, self-awareness on the failure question.

### Technical / craft / case round (45–90 min)

Screens for: the actual skill, live.

- **PM:** a product-sense prompt ("design / improve X"), an execution prompt ("metric dropped 15% — what do you do"), a prioritization / tradeoff prompt, an analytics prompt ("how would you measure success of Y").
- **Engineering:** a coding or system-design problem; digging into a past technical decision.
- **Data / analytics:** a metrics-definition and experiment-design prompt.
- **Design:** a portfolio deep-dive plus a live critique or whiteboard.
- **GTM / ops:** a market-sizing, a process-design, or a "this is broken, fix it" prompt.

Run these as an actual back-and-forth — ask a prompt, let them work, interject with the constraints and follow-ups a real interviewer would. Feedback weight: structured approach, stated assumptions, handles being pushed, arrives somewhere.

### Cross-functional / peer panel (30–45 min each)

Screens for: would I want to work with this person. Collaboration, influence without authority, conflict.

- Tell me about working with a difficult stakeholder / a partner team that disagreed with you.
- A time you changed your mind because of someone else's input.
- How you handle it when [partner function] and your priorities collide.
- What your last team would say you were like to work with.

Feedback weight: accountability without throwing others under the bus, evidence they actually listen, no "everyone loved working with me" with nothing behind it.

### Executive / founder / final (30–45 min)

Screens for: ceiling, strategic thinking, "why us," culture-add, and often a gut check.

- Why this company, why this problem, why now — the real version.
- Where do you think this space / product is going?
- What would you want to change or push on in your first six months?
- What's the hardest thing you've done, and what did it cost you?
- What do you want to be doing in a few years?

Feedback weight: a point of view, not a book report; "why us" that connects to something real about the company; ambition that's specific.

### Values / behavioral deep-dive (45–60 min)

Screens against a specific rubric (the company's values / leadership principles). Every question is "tell me about a time," probed hard for specifics.

- One story per value, each pushed: "what was your specific role," "what did the other person say," "what would you do differently," "what was the result."
- Often a "tell me about a time you failed / got critical feedback / disagreed with a decision and had to carry it out."

Feedback weight: a real story with a real result (not a hypothetical dressed up), genuine ownership, and enough distinct stories that they're not reusing one three times.

## Tailoring dials

Adjust every question set by:

- **Seniority.** IC: depth on personal craft and execution. Lead / manager: how they set direction, grow people, handle a low performer, make org tradeoffs. Exec: strategy, board / cross-org, hiring bar. Don't ask a senior IC "where do you see yourself in 5 years" as a core question; don't let a director slide on "how would you handle two reports in conflict."
- **Company stage.** Seed / early: ambiguity tolerance, breadth, "you'll have no process — is that fine," scrappiness. Scale-up: bringing structure without bureaucracy, hiring, prioritization under fast growth. Big company: navigating scale, influence across a large org, working within existing process.
- **Resume red flags.** A short tenure, an employment gap, a pivot, a step down in title, a jump between unrelated domains — a good interviewer *will* probe these, so the mock must. Ask directly and plainly, the way a fair interviewer would ("I see about eight months at [X] — walk me through that").
- **The interviewer's angle.** A future manager cares about "can you do the job and will you make my life easier." A skip-level cares about ceiling and judgment. A peer cares about collaboration. A founder cares about mission fit and rate of learning. Weight the set toward what this specific interviewer screens for (from Step 2).

## What not to do

- Don't ask trivia or riddles ("how many golf balls fit in a bus") unless the JD or the user says this company actually does that.
- Don't ask more questions than the time allows — a rushed mock teaches the wrong pace. See `references/running-the-mock.md` for counts.
- Don't front-load the hardest question. Real interviews warm up first; a cold curveball produces an unrepresentative answer.
