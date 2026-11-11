# Design Computation - Week 2 Weekly Journal

[All Weeks](README.md) · [Week 1](week-01.md) · **Week 2** · [Week 3](week-03.md)

- **Experiment:** Formal Complaint Ghostwriter
- **Workshop:** Bodystorming and iterative agent design
- **Class dates:** Tuesday, October 27, 2026 and Thursday, October 29, 2026
- **Role:** Letter Writing Assistant
- **Context:** MDes Cohort 7 workload-related complaints
- **Current evidence:** Three written System Card versions and one Knowledge Base document

> **Evidence note:** This journal documents the three System Card versions that already exist in our class and team materials. I have not found saved Agent Studio conversations or screenshots for these versions. The changes below are therefore documented as written design revisions, not as observed model behavior.

## Dated Journal Entries

### Tuesday, October 27, 2026 — Formal Complaint Ghostwriter System Design

**Journal focus:** Organize the classroom observations into a rigorous role, System Card, engagement script, and evaluation criteria. The three written System Card versions and the Knowledge Base are documented below.

**Evidence status:** These are existing written design revisions. They are not presented as observed Agent Studio results because saved sessions or screenshots for the three versions have not yet been added.

### Thursday, October 29, 2026 — Google AI Studio App Build

**Journal focus:** Build a basic app with no agent, build a baseline letter-writing assistant without the Role Card, and then build the Formal Complaint Ghostwriter using the design intent, user journey, System Instructions, standardized script, and system diagram.

**Observed evidence so far:** Google AI Studio generated a general letter-writing interface, but the first runtime generation tests failed and the editable preview remained empty. A successful baseline output has not yet been recorded.

**Pending evidence:** A working basic app, a successful no-Role-Card baseline letter, three conversational modifications of the Role Card agent, the in-app system diagram, and one app with a different design goal.

## 1. Week 2 Goal

In Week 2, the focus moved from changing model settings to designing an agent's role, interaction, knowledge, and boundaries. Our team worked on a **Formal Complaint Ghostwriter** that helps a student turn incomplete notes about academic workload into a formal complaint letter.

My main design question is:

> How can a letter-writing assistant help a student move from an incomplete personal account to an accurate and useful complaint letter without inventing facts or taking control away from the student?

The assignment requires a System Card, a repeatable engagement script, reflection on one system design, and at least three cycles of modification and testing in new Agent Studio sessions. The source documents already contain three written versions of the System Card. The next step is to test each version with the same script and preserve the resulting evidence.

## 2. Classroom Bodystorming Method

The classroom activity treated letter writing as a role-based system before moving it into Agent Studio. Each group worked with a Goal Card, three or four fragments of rough user notes, and a single role: **Letter Writing Assistant**.

The user was asked to behave like a real user:

- Answer questions honestly.
- Do not volunteer information before being asked.
- Do not organize the problem for the assistant.
- Do not diagnose what the assistant needs.

The observers used two lenses. The interaction observer watched what had to happen for progress to occur. The system observer watched what the role would need in order to function reliably. During the enactment, the user revealed one additional note at minute five and introduced a new constraint at minute eight.

The debrief questions were also useful as evaluation criteria: What did the assistant do, need, assume, and produce? Where did it struggle? Where did responsibility become unclear? What felt unstable? What required judgment rather than a procedure?

These questions shaped the way I read the three System Card versions. They also provide a structure for the future Agent Studio tests.

## 3. Initial System Card

### Role Name

Formal Complaint Ghostwriter

### Purpose

Help a student from MDes Cohort 7 write a letter to the appropriate university office about an academic workload concern.

### Behavioral Rules

- Use a formal, serious, collegial, and polite voice.
- Ask the student what they experienced and what is happening.
- Allow pauses while the student thinks.

### Interaction Loop

1. **Listening:** Listen to the student's experience in MDes.
2. **Capture:** Record key moments, emotions, and challenges.
3. **Reflect:** Summarize the student's account.
4. **Clarify:** Ask follow-up questions to understand the situation more accurately.

### Boundaries

- Only help with workload-related complaints.
- Keep the student in final control of the letter.
- Confirm accuracy before finalizing.
- Do not make decisions on behalf of the student.

### Does Not Do

- Invent or exaggerate experiences.
- Change the student's intended meaning.
- Promise that the complaint will be resolved.

### Required Inputs

- What happened.
- Who the letter is addressed to.
- What the student wants to happen.
- Specific facts, including dates, course names, deadlines, and frequency.
- Anything the student does not want included.

### Outputs

- A summary of the assistant's understanding for the student to confirm.
- A draft formal complaint letter.
- A list of information the student still needs to decide or check.

## 4. Knowledge Base

The Knowledge Base is separate from the System Instructions. It gives the agent reference information needed to construct a formal complaint letter, but it does not tell the agent how to behave.

The document defines the expected letter structure:

1. Sender's name and contact information.
2. Date.
3. Recipient's name, title, and office.
4. A one-line subject.
5. An opening sentence stating the purpose.
6. A factual description of the issue.
7. Supporting dates and events.
8. The effect of the issue.
9. The requested action.
10. Closing and signature.

It also provides common phrases used in a US university setting and clarifies the limits of a complaint letter. A complaint can create a written record and request an action or response, but it cannot guarantee a resolution and is not a legal filing.

The Knowledge Base also describes the likely recipient's scope. The office may handle scheduling, academic calendars, program requirements, deadlines, workload questions, academic policy, or routing concerns to the correct service. It does not decide the content of an individual course or a student's grade.

## 5. Three Written Versions

The System Instructions document contains three complete versions. The second and third versions preserve the original card and add one new interaction step at a time.

| Version | Written change | Functional effect to test | Evidence status |
|---|---|---|---|
| V1 - Listen and Clarify | The interaction loop ends after clarification, although the Outputs section still promises a draft. | Does the agent remain in an interview loop, or does it decide on its own when to write? | Agent Studio result not yet recorded |
| V2 - Draft with Placeholders | Adds a Draft step after Reflect. The agent should show a complete draft even when some inputs are missing and represent missing information with brackets such as `[date]` or `[course name]`. | Does the agent produce a useful draft without inventing missing facts? | Agent Studio result not yet recorded |
| V3 - Active Revision | Adds a Revise step. When the student says the draft is wrong, the agent should revise it and show the new version instead of asking the student to write replacement wording. If the request is unclear, it should offer two alternatives. | Does the agent take responsibility for revising while keeping the student's intent and final control? | Agent Studio result not yet recorded |

The written progression is:

> Listen and clarify -> produce a usable draft -> support revision

This is a clear evolution of the role, but it is not yet evidence that the agent behaved differently. That claim requires three recorded sessions using the same test conditions.

## 6. Design Tensions to Test

The documents reveal several important questions for the Agent Studio sessions.

### When should drafting begin?

V1 asks the agent to collect required information before writing, but it does not include Draft in the interaction loop. V2 then tells the agent to begin after Reflect even when information is missing. This creates a useful test: can the assistant make progress without presenting uncertain details as facts?

### How should missing information appear?

V2 introduces brackets for missing facts. The test should check whether the agent consistently uses placeholders or quietly fills gaps with plausible-sounding dates, names, or course details.

### What counts as final confirmation?

Every version says the student must confirm accuracy before finalization, but none turns confirmation into a numbered interaction step. The test should check whether the agent explicitly asks for confirmation or treats the first complete draft as finished.

### Who is the recipient?

The original Purpose refers generally to an "officer." The Knowledge Base describes several possible responsibilities of an office. The assistant should clarify the appropriate recipient rather than assuming that one office controls course content, grades, scheduling, and student services.

### Who performs the revision work?

V3 changes the division of labor. The student should describe what feels wrong, while the agent should propose the revised language. The test should examine whether the agent actually revises or shifts the writing task back to the user.

## 7. Fixed Engagement Script for Agent Studio

This is a **planned test script**, not a record of a completed conversation. Each version should be tested in a new session with the same model, temperature, Knowledge Base, and sequence of prompts.

### Step 1 - Initial incomplete request

> I need help writing a formal complaint about workload in my MDes program. Several major deadlines are in the same week, but my notes are incomplete.

The tester should answer questions honestly but should not volunteer all details at once.

### Step 2 - Information provided only when requested

- **Recipient:** The program office, but I do not know the correct officer's name.
- **Desired outcome:** I want the program to review the schedule and coordinate major deadlines more carefully.
- **Known fact:** One deadline was moved earlier, but I have not confirmed the exact date.
- **Exclusion:** I do not want the letter to identify one specific instructor.

### Step 3 - Additional note

> One course deadline was moved earlier and created more overlap with another required project.

### Step 4 - New constraint

> Keep the tone collegial. Do not invent the missing date or course name. Use brackets if information is still missing.

### Step 5 - Revision request

> This draft sounds too strong. Revise it to sound more collaborative, and show me the new version.

The revision request is important for testing V3. If the agent cannot identify what to change, it should offer two possible versions rather than asking the student to write the replacement.

## 8. Evaluation Criteria

| Criterion | Question to record after each session |
|---|---|
| Clarification | Did the agent ask for the recipient, desired outcome, facts, and exclusions? |
| Assumptions | Did it introduce any unsupported date, course, person, motive, or outcome? |
| Draft timing | Did it draft too early, wait too long, or make appropriate progress with placeholders? |
| Knowledge use | Did the letter follow the expected formal structure and stay within the recipient's scope? |
| Tone | Was the language formal, serious, collegial, and polite? |
| User control | Did the agent preserve the student's meaning and ask for confirmation? |
| Revision | Did it revise the wording itself and show the new version? |
| Completion | Did it identify unresolved details instead of presenting the letter as final? |

## 9. Iteration Evidence Table

This table should be completed only after the sessions are run.

| Version | Session evidence | Observed behavior | Problem found | Next modification |
|---|---|---|---|---|
| V1 - Listen and Clarify | Not yet recorded | Pending | Pending | Existing written change: add Draft step |
| V2 - Draft with Placeholders | Not yet recorded | Pending | Pending | Existing written change: add Revise step |
| V3 - Active Revision | Not yet recorded | Pending | Pending | To be decided from actual results |

For each session, I need to preserve the Agent Studio link or export, configuration, complete conversation, and at least one screenshot showing the behavior discussed in the reflection.

## 10. Preliminary Reflection on the Written Design

The three cards show a shift from defining the assistant's attitude to defining its responsibility in the writing process. V1 establishes listening, factual boundaries, and student control. V2 makes the assistant responsible for producing a usable artifact even when information is incomplete. V3 makes it responsible for helping with revision rather than only collecting information.

The separation between System Instructions and Knowledge Base is also important. The System Instructions specify actions, limits, tone, and interaction. The Knowledge Base contains reusable reference information about complaint letters and the recipient's likely scope. The Journal has a third function: it records why the design changed, what happened in testing, and what evidence supports the reflection.

At this stage, the strongest conclusion is about the **written design**, not model performance. The role becomes more operational across the three versions, but the instructions also create tensions around when to draft and how to confirm accuracy. The Agent Studio sessions are necessary to determine whether the new rules resolve those problems or introduce new ones.

## 11. Next Steps

1. Create a new Agent Studio session for V1 and run the fixed script.
2. Save the conversation, configuration, link, and screenshots.
3. Repeat the same procedure for V2 and V3.
4. Complete the evidence table using only observed behavior.
5. Add a final comparison explaining which instruction changed which behavior.
6. Revise the final System Card based on the strongest evidence.

## 12. Source Materials

- `DesComp 2.pdf`, especially the bodystorming workshop, Sample Role Card, Test Your Role, Homework, and diagnostic checklist pages.
- `SYSTEM INSTRUCTIONS.docx`, containing the three written Formal Complaint Ghostwriter versions.
- `KNOWLEDGE.docx`, containing complaint-letter structure, university phrasing, functional limits, and recipient scope.

