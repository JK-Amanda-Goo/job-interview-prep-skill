---
name: job-interview-prep
description: Runs a live mock interview for a specific job — you paste the job description (and whatever you know about the round, the interviewer, and the format), it asks questions one at a time in character as the interviewer, you answer out loud or by voice, and it gives honest interviewer's-POV feedback after each answer, then a full debrief at the end. It reads your resume first and asks for it if it doesn't have one. Use this skill whenever someone wants to practice or prepare for a job interview: a mock interview, interview practice, "quiz me for this interview," "help me prep for a recruiter screen / hiring manager / panel / final round," rehearsing answers to likely questions, or getting feedback on how they'd answer. Trigger it when the user pastes a job description and says they have an interview coming up, names an interview round or an interviewer, asks what they'll be asked, or wants to run through questions and get feedback — even if they never say the word "mock." Not for written application answers or supplemental essays (that is job-application-answers), video-intro scripts (job-application-video-intro-script), resume/CV writing, salary negotiation, or deciding which jobs to apply to.
---

# Job Interview Prep

Run a realistic mock interview for one specific role. Ask questions the way that round's interviewer actually would, one at a time, in character. Let the person answer out loud (they will often answer by voice, so the input arrives as a rough transcript). Give feedback from the interviewer's chair — honest and specific, not a pep talk — after every answer, then a full debrief at the end.

The trap this skill exists to avoid: generic interview coaching. "Use the STAR method" and a list of 50 common questions is not practice. What actually moves someone's odds is running the real gauntlet — this round, this seniority, this job's real requirements, this interviewer's likely angle — answering under mild pressure, and hearing what an interviewer would have written on their scorecard. The substance comes from the person and their resume; the skill's job is to simulate the room, listen like an interviewer, and tell the truth about what landed.

## The workspace

All user data lives outside this skill directory:

```
~/job-interview-prep/
├── profile/    # resume + career context — but see Step 0, it usually reuses an existing one
└── sessions/   # archive of past mock interviews + feedback, searched for reuse
```

Create `sessions/` on first use. Never commit anything from the workspace into this skill's repo — it holds a real person's career history.

## Step 0 — Profile (first run only)

A mock interview needs the same raw material a real one draws on: the projects the person can tell in full, the career through-line, the gaps or pivots an interviewer will poke at, what they actually want next. That material is very likely already on disk.

Check in this order and use the first one that exists and has content:

1. `~/job-interview-prep/profile/`
2. `~/job-application-answers/profile/` — the companion skill's profile
3. `~/job-application-video-intro/profile/`

If one of the companion profiles exists, **read it and move on.** Do not make the user re-supply their resume because a third skill wants it.

If none exists, say briefly why two minutes now is worth it, then ask for:

- **Resume** — paste, or a path to a PDF/docx/md file. Read it and save a markdown copy to `~/job-interview-prep/profile/resume.md`.
- **The context interviews keep needing** — the two or three projects they'd want to be asked about, how they explain their career path (a pivot, a gap, a short tenure), what they're actually looking for, work-authorization or location constraints, and the story that comes up in every interview. Save to `~/job-interview-prep/profile/context.md` using `assets/profile-template.md` as the scaffold.

Tell the user they can edit these files directly anytime.

**If the user has no resume at all yet:** stop here. A mock interview against no resume is a cold read, not practice. Ask them to put one together first (even a rough one) and come back.

## Step 1 — Intake

Collect, asking only for what's missing:

1. **Company**
2. **Role** (full title)
3. **Job description** — paste. If they only have a link, ask them to paste the text.
4. **Where they are in the process** — is this their first conversation, or have they already done rounds? (Affects what this round will re-cover vs. assume.)

Keep company / role / JD for the whole session — the user may want to run a second round or redo a section.

## Step 2 — Interview context (ask before starting)

The same job produces very different interviews depending on the round and the interviewer. Ask the user what they know — and make clear that "I don't know" is a fine answer for any of these; the mock still runs, just on sensible defaults with the assumptions named.

Ask about:

1. **Which round is this, and how long?** Recruiter / phone screen, hiring-manager interview, technical or case round, cross-functional / peer panel, executive / final, or a values / behavioral deep-dive. Duration (30 / 45 / 60 min) sets how many questions are realistic — see `references/running-the-mock.md`.
2. **The interviewer** — name, title, and anything known about their background (from LinkedIn, the recruiter, or the scheduling email). A founder, a future manager, a skip-level, and a peer all screen for different things and ask in different registers. If they know the name and nothing else, that's still useful — note it.
3. **The stage / process overall** — the full loop if they know it (e.g. "screen → HM → panel of 3 → founder → offer"), and where this round sits. Knowing a later round will cover strategy means this round should go deep on execution instead of spreading thin.
4. **Format and any known structure** — video, phone, or onsite; and whether the recruiter shared a shape ("45 min: 10 min background, 25 min case, 10 min your questions"). Match the mock to it if so.
5. **Anything the recruiter told them to prepare** — a case prompt, a presentation, "be ready to go deep on X." If there's a take-home or presentation component, ask whether they want to rehearse the live Q&A around it.

Summarize back what you'll run: the round, the interviewer persona you'll adopt, roughly how many questions, and the format. Get a quick confirm before starting.

## Step 3 — Check the archive

Interview rounds repeat across applications, and the same weak spots tend to recur. Rewriting a question set from scratch wastes the calibration already done.

```bash
grep -H -e '^company:' -e '^role:' -e '^round:' ~/job-interview-prep/sessions/*.md 2>/dev/null
```

If there's a past session for the same company, a similar role, or the same round type:

- Read it, and read its debrief.
- Tell the user what came up last time and what the debrief flagged as the biggest gaps.
- Offer to **focus this run on the weak spots** rather than starting cold — re-ask the questions that went badly, plus new ones.

If nothing relevant exists, say so briefly and continue.

## Step 4 — Build the question set (internal — do not show it)

Derive the questions from the JD, the round, the seniority, and the interviewer's likely angle. See `references/question-generation.md` for the per-round playbooks and the tailoring dials.

**Do not show the user the list.** Seeing the questions in advance turns practice into rehearsal of prepared lines, which is the opposite of what a mock is for. Build it, hold it, reveal one at a time.

Order it the way a real interview flows:

1. **Warm-up** — a resume walkthrough or a "why this role" opener. Low stakes, gets them talking.
2. **Core** — three to five questions on the JD's real requirements. This is most of the round.
3. **Pressure** — one or two harder ones: a failure, a conflict, a tradeoff they'd defend, a probe at a resume gap.
4. **Their questions** — end by playing the interviewer taking questions, and assess what they ask.

Pull the JD's two or three real requirements the same way the companion skills do — name what the role is actually screening for, past the boilerplate — and make sure at least one core question targets each.

Tell the user, before you start:

- how many questions and roughly how long
- that you'll ask **one at a time, in character** as the interviewer
- that they should answer **out loud, or by voice** — a spoken answer arriving as a rough transcript is expected and fine
- that they'll get feedback after each answer, and a full debrief at the end
- that they can say "redo" to re-answer, or "skip" to move on

## Step 5 — Run the mock (the loop)

For each question, in order:

### Ask it — in character

Ask as the interviewer would actually phrase it. A recruiter and a founder ask the same underlying question in different words and at different depth. One question at a time. No preamble listing what's coming.

### Take the answer

The user answers, often by voice → transcript. Read it for **content, structure, and substance** — not delivery mechanics. See `references/feedback-rubric.md` for how to handle transcription artifacts: ignore filler words, missing punctuation, capitalization, homophones, and clearly-artifact fragments. Judge whether they *answered the question*, whether an interviewer could *follow it*, and whether it *carried signal* for this role. If you genuinely can't tell whether something was a transcription glitch or a real stumble, ask.

### Give feedback — from the interviewer's chair

Honest and specific, the interviewer's POV, not a pep talk (per `references/feedback-rubric.md`). After each answer, give:

1. **The scorecard line** — one or two sentences of what an interviewer would actually jot down right now. Includes the unflattering read when that's the true one ("Answered a different, easier question. Still don't know what *he* did versus the team.").
2. **The single highest-value fix** — the one change that would move this answer most. Not a list.
3. **The follow-up probe** *(when a real interviewer would push)* — ask the follow-up they'd now ask, and let the user answer it. This is where prepared answers fall apart and where the practice is most valuable.

Keep it tight — a few lines, not an essay. Don't re-teach a framework mid-round. Then move to the next question.

### Pacing

Keep it moving. If an answer is strong, say so in a line and go on. Don't let feedback balloon into coaching that stops the simulation — the debrief is where the depth goes.

## Step 6 — Debrief

After the last question, write the full assessment. This is the deliverable the user keeps.

- **The honest read.** Given only this round, would the interviewer advance them? One of: *clear advance / lean advance / on the fence / lean no / clear no* — with the one-sentence reason. This is the interviewer's call, not encouragement.
- **What came through.** The strengths that actually landed in answers — with which answer showed each.
- **What cost the most signal.** The two or three things that most hurt — ranked. Be concrete: which answers, what was missing.
- **Patterns across answers.** The recurring tells — buries the answer, no numbers, "we" instead of "I", one story reused three times, runs long, doesn't land the "why this company" — that a single-answer note wouldn't catch.
- **Prep actions before the real interview.** Specific and few. "Rewrite the [X] story with the number and your decision in the first two sentences" beats "work on structure."
- **Questions to ask the interviewer.** Three or four, tailored to this round and this interviewer — the kind that show they've thought about the company, not filler.

## Step 7 — Archive

Save to `~/job-interview-prep/sessions/YYYY-MM-DD-company-role-round.md`:

```markdown
---
company: Acme
role: Senior Product Manager
round: hiring-manager
interviewer: "Jane Doe, Director of Product"
date: 2026-09-10
read: lean advance
---

## Questions and answers

### Q1 — [question]
**Answer:** [transcript / summary]
**Feedback:** [the scorecard line + fix]

### Q2 — ...

---

## Debrief
[the full Step 6 assessment]
```

Accurate frontmatter is what makes Step 3 work next time — especially `role`, `round`, and `read`.

Then offer the next round, or a focused redo of the answers that went worst.

## Voice

If the user has a personal writing-voice skill (something like `<name>-voice`), use it when writing the **debrief** — it should read like a note to them, not a report. The mock answers themselves are the user's own spoken words; don't rewrite those.

## Reference files

- `references/question-generation.md` — per-round question playbooks (recruiter, hiring manager, technical/case, panel, executive, behavioral) and the tailoring dials for seniority, company stage, and resume red flags (Step 4)
- `references/feedback-rubric.md` — the interviewer's-POV assessment: the dimensions, the scorecard-line format, how to handle voice-transcribed answers, and what honest-not-harsh sounds like (Step 5)
- `references/running-the-mock.md` — the live-loop mechanics: question count by duration, interviewer personas and register, staying in character, pacing (Steps 2, 4, 5)
- `assets/profile-template.md` — scaffold for `profile/context.md` (Step 0)
