# Changelog

All notable changes to this project are documented here. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [0.1.1] - 2026-09-10

### Fixed
- `.gitignore` was matching `references/running-the-mock.md` with its `*-mock.md` pattern (intended only to catch personal mock transcripts landing at the repo root), so that reference file was missing from the v0.1.0 tag. Scoped the patterns to `mock-*.md` / `session-*.md` and restored the file.

## [0.1.0] - 2026-09-10

### Added
- Initial release. An eight-step workflow for running a live mock interview for one specific role: profile → intake → interview context → archive check → build the question set (held back from the user) → run the mock one question at a time in character → per-answer interviewer's-POV feedback → debrief → archive.
- Interview-context intake (Step 2): asks the user what they know about the round type, duration, interviewer, overall process, format, and anything the recruiter asked them to prepare — "I don't know" is an accepted answer for any of them, and the mock runs on named defaults.
- Reuses the profile from the companion `job-application-answers` or `job-application-video-intro-script` skill if present, so the resume and career context don't have to be supplied a third time. Stops and asks the user to build a resume first if they have none.
- Live simulation: questions revealed one at a time, in character as the round's interviewer, with a persona-matched register. The full question set is never shown to the user.
- Honest, interviewer's-POV feedback after every answer — a scorecard line (including the unflattering read when true), one highest-value fix, and the follow-up probe a real interviewer would ask next.
- Built-in handling for voice-transcribed answers: ignores filler, punctuation, capitalization, homophones, and clearly-artifact fragments; still flags not-answering-the-question, no structure, rambling, and missing specifics.
- Local workspace (`~/job-interview-prep/`) with `sessions/` for a searchable archive of past mocks and debriefs — kept outside the repo, with `.gitignore` rules as a second line of defense. Archive reuse offers a weak-spot-focused rerun.
- `references/question-generation.md` — per-round playbooks (recruiter, hiring manager, technical/case, peer panel, executive, behavioral) and tailoring dials for seniority, company stage, resume red flags, and interviewer angle.
- `references/feedback-rubric.md` — the seven assessment dimensions, the scorecard-line format, honest-not-harsh calibration, voice-transcript handling, and the debrief structure.
- `references/running-the-mock.md` — question count by duration, interviewer personas and register, staying in character, feedback pacing, redo/skip controls.
- `assets/profile-template.md` — shared scaffold with `job-application-answers` and `job-application-video-intro-script`.
