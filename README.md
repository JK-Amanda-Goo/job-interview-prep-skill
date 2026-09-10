# Job Interview Prep (Claude Code skill)

Runs a **live mock interview** for one specific job. You paste the job description and whatever you know about the round, the interviewer, and the format. It asks questions one at a time, in character as the interviewer. You answer out loud — by voice is fine, it reads the transcript. After each answer it tells you what an interviewer would actually have written on their scorecard, then gives you a full debrief at the end.

The point of this skill is that it **isn't generic interview coaching**. "Use the STAR method" and a list of 50 common questions is not practice. This runs the real gauntlet — this round, this seniority, this job's real requirements, this interviewer's likely angle — and tells you the truth about what landed.

## How it works

1. **Profile** *(first run only)* — it reuses the profile from the companion [job-application-answers](https://github.com/JK-Amanda-Goo/job-application-answers-skill) or [job-application-video-intro-script](https://github.com/JK-Amanda-Goo/job-application-video-intro-script-skill) skill if you have one. Otherwise you supply your resume plus the context interviews keep needing. Saved locally. (No resume at all? It'll ask you to put one together first — a mock against no resume is a cold read, not practice.)
2. **Intake** — company, role, job description, and where you are in the process.
3. **Interview context** — it asks what you know about the round (recruiter screen / hiring manager / technical / panel / final), how long it is, who the interviewer is, the overall loop, the format, and anything the recruiter told you to prepare. "I don't know" is fine for any of these — the mock still runs, on sensible defaults with the assumptions named.
4. **Archive check** — if you've done a mock for this company or round before, it reads the old debrief and offers to focus this run on the weak spots.
5. **The mock** — it builds a question set tailored to the round and the JD's real requirements (you don't see the list — that would turn practice into rehearsal), then asks one question at a time in character. You can say "redo," "skip," "harder," or "easier."
6. **Feedback after each answer** — the scorecard line an interviewer would write (including the unflattering read when that's the true one), the single highest-value fix, and the follow-up probe a real interviewer would now ask.
7. **Debrief** — an honest advance / no-advance read, what came through, what cost the most signal, patterns across your answers, specific prep actions, and questions to ask your interviewer.
8. **Archived** locally so the next round can build on it.

## What you get

- A realistic run at the actual round, under mild pressure.
- Per-answer feedback from the interviewer's chair — honest, specific, not a pep talk.
- A written debrief with a straight read on whether this round would advance you, and exactly what to fix before the real thing.

## Your data stays local

Nothing is uploaded. The skill keeps your material in a workspace outside this repo:

```
~/job-interview-prep/
├── profile/    # or it reuses ~/job-application-answers/profile/
└── sessions/   # past mock interviews + feedback, searched for reuse
```

The repo's `.gitignore` blocks personal files as a second line of defense. If you fork this, keep it.

## Install

```bash
git clone https://github.com/JK-Amanda-Goo/job-interview-prep-skill.git ~/.claude/skills/job-interview-prep
```

Then say what you need in a Claude Code session:

> "이 회사 면접 있는데 모의면접 좀 돌려줘" · "Run a mock hiring-manager interview for this role" · or paste a JD and say you have an interview coming up

## Requirements

- Claude Code (or another agent that supports skills)
- Nothing else — no API keys, no external services
- Answering by voice uses your client's own voice input (Claude Code transcribes it); the skill just expects a rough transcript and judges content, not delivery mechanics

## Voice

If you have a personal writing-voice skill (something like `yourname-voice`), this skill uses it when writing the **debrief**, so it reads like a note from someone who watched the interview rather than a form. Your mock answers are your own spoken words and aren't rewritten.

## What this intentionally doesn't do

- **Feed you the questions in advance.** You don't see the set. Rehearsing prepared lines is the opposite of practice.
- **Go easy.** If a round would be a "lean no," it says so, and says why.
- **Replace [job-application-answers](https://github.com/JK-Amanda-Goo/job-application-answers-skill)** (written free-text application answers) or **[job-application-video-intro-script](https://github.com/JK-Amanda-Goo/job-application-video-intro-script-skill)** (spoken video-intro scripts). This one is live interview practice. All three share a profile.

## Files

- `SKILL.md` — the workflow
- `references/question-generation.md` — per-round question playbooks and the tailoring dials
- `references/feedback-rubric.md` — the interviewer's-POV assessment and how to handle voice-transcribed answers
- `references/running-the-mock.md` — the live-loop mechanics: question counts, interviewer personas, pacing
- `assets/profile-template.md` — scaffold for your career context file, shared with the companion skills

## Releasing

Every notable change gets a `CHANGELOG.md` entry (Keep a Changelog format), a matching git tag, and a GitHub Release whose notes are that changelog section:

```bash
# 1. Add a new version section to the top of CHANGELOG.md
# 2. git add -A && git commit -m "..."
git tag -a vX.Y.Z -m "vX.Y.Z - <one-line summary>"
git push origin main --tags
gh release create vX.Y.Z --title "vX.Y.Z" --notes "<paste the CHANGELOG section>"
```

## License

MIT — see `LICENSE`.
