# Design Computation — Week 3 Weekly Journal

[All Weeks](README.md) · [Week 1](week-01.md) · [Week 2](week-02.md) · **Week 3** · [Week 4](week-04.md)

- **Class meetings:** Tuesday, November 3 and Thursday, November 5, 2026
- **Platform:** Google AI Studio
- **Main system:** FormalFlow / Correspondent
- **Role:** Formal Complaint Ghostwriter

> **Evidence boundary:** This entry records the design work and the observed baseline failures from Week 3. The successful three-step prototype, deployment tests, peer feedback, and Mini-me evidence were produced during November 10–13 and are documented in [Week 4](week-04.md). A build message is not treated as proof unless the interface behavior was also tested.

## Tuesday, November 3 — Baseline and Design Intent

### Assignment direction

The homework asked us to begin with a simple Google AI Studio app, then build a letter-writing assistant without behavioral guidance, and finally rebuild it with the Role Card. The purpose was to compare a generic generated interface with a more deliberately designed agent.

I do not have saved evidence for a separate non-agent “Camera Obscura” app, so I am not claiming that part as completed. My saved evidence begins with the letter-writing assistant.

### Baseline without the Role Card

I first asked AI Studio to build a simple assistant in which the user could describe a problem and receive an editable formal letter. The interface contained:

- a problem-description field;
- tone choices;
- optional sender and recipient details;
- a Generate Letter button;
- an editable letter preview.

The interface was generated, but the first runtime tests failed. One response returned HTML where JSON was expected and displayed `Unexpected token '<'`. A later attempt displayed `Could not generate the letter right now`. At this stage I had a visible UI, but not a verified working letter agent.

### Design intent

The Role Card changed the goal from “produce a formal-looking letter” to:

> Help the user clarify the situation, identify missing evidence, confirm the intended meaning, produce an editable formal letter, and revise it through conversation without inventing facts or taking final control away from the user.

The most important behavioral requirements were:

- ask for missing facts rather than guessing;
- keep a formal, serious, collegial, and polite tone;
- use visible placeholders for unavailable information;
- confirm the user’s meaning before finalizing;
- let the user revise and approve the final wording.

### Role Card versus Knowledge Base

The **Role Card/System Instructions** control behavior: what the agent asks, how it handles uncertainty, its tone, and where human authority remains.

The **Knowledge Base** supplies reusable reference information: the structure of a US formal complaint letter, useful phrases, the limits of a complaint, and the likely scope of a university office.

Keeping these functions separate helped me see that formatting knowledge does not automatically create responsible behavior.

## Thursday, November 5 — Interaction Plan

I planned the agent as a three-step user journey:

1. **Describe Problem** — the user explains what happened and the desired outcome.
2. **Clarify Details** — the system identifies missing facts and asks concise questions.
3. **Confirm Summary** — the user reviews Situation, Impact, and Requested Resolution before a letter is generated.

### Standardized test prompt

I prepared one repeated scenario so that later versions could be compared:

> I want to complain about the workload in one of my classes. The number of assignments increased, and I do not think the expectations are fair. I want the school to reduce the workload.

I intentionally left out the course title, assignment dates, recipient, and specific requested resolution. These omissions made it possible to test whether the agent would ask, use placeholders, or invent details.

### Planned conversational modifications

The next three changes were defined before testing:

1. Add a missing-fact check with concise clarification questions.
2. Add an editable, explicitly unverified summary before drafting.
3. For ambiguous revision requests, offer two explained alternatives instead of silently guessing.

### Evaluation script

For each run I planned to record:

- whether the app asked for important facts;
- whether it invented a date, course, person, impact, or outcome;
- whether placeholders remained visible;
- whether the user confirmed the summary;
- whether the letter stayed editable;
- whether a revision preserved the user’s control.

## Week 3 Reflection

This week clarified the difference between generating an interface and designing an agent. The baseline looked complete, but the failed runtime showed that appearance was not enough. The Role Card also revealed that “do not invent facts” needed to become visible interaction rules: questions, placeholders, confirmation, and revision controls.

The planned flow was not yet evidence of success. The actual implementation, three modifications, deployment repair, peer feedback, and comparison with Mini-me are recorded in Week 4.

## Links

- [GhostWriter source repository](https://github.com/yi470/GhostWriter)
- [FormalFlow public deployment](https://ghostwriter-sqhi.vercel.app/)
- [FormalFlow Google AI Studio project](https://ai.studio/apps/1c2e08ac-00d5-4350-bde1-aa7a9918171e)
- [Editable system maps in FigJam](https://www.figma.com/board/lCqKByHlpduLcwGlkoVqRB/TDF-Weekly-Journal?node-id=215-361)
