# Reliability Coding Instructions

**Scoping review:** Generative AI in Introductory Programming Education
**Purpose:** You are independently coding a sample of 20 papers (48 activity rows) to assess coding consistency. Your coding will be compared against the lead reviewer's coding; disagreements will be resolved by a third-party arbitrator with reference to the source text.

**You have no access to the lead reviewer's coding.** Code based on the activity description, the division detail, and where needed the source paper. If the activity description alone is insufficient, consult the full text of the paper.

---

## 1. What the review is asking

Three research questions:

- **RQ1** — What programming activities are reported as involving generative AI in introductory programming education?
- **RQ2** — How is the implementation work divided between student and AI across these activities?
- **RQ3** — To what extent do studies measure whether students can perform the identified activities without AI assistance?

---

## 2. Your task

You are given a spreadsheet with 48 rows. Each row represents one programming activity identified in a study. The following columns are pre-filled:

- `paper_id` — the study identifier
- `title` — the paper title
- `activity_row` — row number within that paper
- `activity_name` — a free-text description of what the student (or AI) does
- `division_detail` — additional context on how the work is divided

**You fill six columns** (highlighted yellow in the sheet):

1. `taxonomy_code`
2. `taxonomy_label`
3. `division_of_work`
4. `intended_role`
5. `effect_type`
6. `unassisted_measurement`

---

## 3. Evidence rule

**Every coded value must be supportable by the activity description, the division detail, or the source paper.** Do not infer what the authors would probably have said. Do not supply detail from your background knowledge of the tool.

If the activity description and division detail do not contain enough information to assign a value confidently, and you do not have access to the full text, code `unclear` for intended_role or use the closest match for other fields and note your uncertainty.

---

## 4. Field definitions

### 4.1 `taxonomy_code` and `taxonomy_label`

**Question:** Which programming activity from the taxonomy best matches this activity description?

Assign one code from the list below. If the description genuinely fits two codes equally well, pick the one that best describes the **primary cognitive demand** of the activity as described.

#### Cluster C1 — Comprehension of existing code

| Code | Label | Description |
|---|---|---|
| C1.1 | Code reading | Making sense of code without executing it |
| C1.2 | Code tracing | Hand-executing code as the machine would |
| C1.3 | Explaining code | Articulating what code does, describing code purpose |
| C1.4 | Predicting output | Determining or interrogating what code will output |
| C1.5 | Inspecting runtime state | Examining or altering variables while code runs |

#### Cluster C2 — Problem solving and design prior to code

| Code | Label | Description |
|---|---|---|
| C2.1 | Interpreting the problem | Establishing what the task requires |
| C2.2 | Problem decomposition | Breaking a problem into sub-problems |
| C2.3 | Algorithm design | Devising a solution procedure, planning steps |
| C2.6 | UML / OO modelling | Modelling structure before implementation |

#### Cluster C3 — Code production

| Code | Label | Description |
|---|---|---|
| C3.1 | Writing a program | Producing code from a specification — includes any instance where code is written, generated, or produced, whether by the student or by the AI |
| C3.2 | Implementing a design | Converting an algorithm into code; includes Parsons problems (arranging code blocks) |
| C3.3 | Modifying code | Altering, extending, editing, or refactoring an existing program |
| C3.4 | Compiling / executing | Running code, resolving compile-time errors, executing against tests |
| C3.5 | Code style and quality | Producing readable, well-formed code; style checking |

#### Cluster C4 — Verification and correction

| Code | Label | Description |
|---|---|---|
| C4.1 | Writing test cases | Devising tests; test-driven development |
| C4.2 | Evaluating correctness | Judging whether code meets its specification; submitting to autograders |
| C4.3 | Debugging | Detecting, locating and correcting faults |
| C4.4 | Interpreting compiler messages | Acting on compile-time diagnostics; understanding error messages |

#### Cluster C5 — Evaluation of, and communication about, code

| Code | Label | Description |
|---|---|---|
| C5.1 | Peer review of code | Reviewing peers' code for defects and design |
| C5.2 | Presenting solutions | Presenting and critiquing solutions publicly |

#### New activities (no pre-GenAI equivalent)

| Code | Label | Description |
|---|---|---|
| NEW-P | Prompting / NL specification | Writing natural language prompts or specifications for AI code generation; crafting descriptions of desired program behaviour; iterative prompt refinement; EiPE-style description tasks graded via AI code generation |
| NEW-Q | Querying AI for help | Formulating questions, help requests, or debugging queries directed at an AI tutor, chatbot, or assistant; requesting hints, explanations, or next-step guidance from an AI system |
| NEW-E | Evaluating AI output | Judging the correctness, quality, or appropriateness of AI-generated code, explanations, suggestions, or feedback; accepting or rejecting AI proposals based on quality assessment |

**Important notes on taxonomy coding:**

- `C3.1 Writing a program` applies whether the student writes the code or the AI generates it. If the AI generates code from a prompt, that code-generation step is C3.1. The `division_of_work` field captures who does the writing, not the taxonomy code.
- If a student writes a prompt and the AI generates code, these are **two activities on separate rows**: the prompting row is NEW-P, the code generation row is C3.1.
- `NEW-Q Querying AI for help` is for interactions where the student seeks assistance. If the AI proactively delivers feedback without the student requesting it, that is not NEW-Q — look at what the student does with the feedback (e.g., C1.1 if they read it, C3.3 if they modify code based on it).

---

### 4.2 `division_of_work`

**Question:** Who nominally leads this activity? Who performs the substantive work?

| Value | Definition | Examples |
|---|---|---|
| `student-led` | The student performs the activity. AI may be present but is not generating the primary artefact. | Student writes code with AI available but not used for this task; student traces code manually; student writes a prompt |
| `AI-proposes student-decides` | The AI generates a candidate output (code, hint, explanation, fix). The student evaluates, accepts, rejects, or modifies it. | AI suggests a code fix, student decides whether to apply it; AI generates an explanation, student reads and evaluates it; AI proposes next step, student chooses whether to follow |
| `shared / collaborative` | Both student and AI contribute to the artefact in an interleaved, genuinely collaborative way. | Pair-programming style interaction; student and AI take turns building the solution |
| `AI-led` | The AI performs the activity with minimal or no student involvement at that step. The student does not meaningfully inspect, evaluate, or alter the output. | AI generates complete code that goes directly to testing; AI automatically diagnoses and fixes an error without student review |

**Tie-break:** If delegation shifts during the activity, code by **who produced the artefact that gets assessed or used**. If the student prompts but the AI writes the code and the code goes to testing without student review, the code-writing activity is `AI-led`.

---

### 4.3 `intended_role`

**Question:** What is the pedagogical design intent of the AI's involvement in this activity?

| Value | Definition | Look for |
|---|---|---|
| `scaffold with fading` | Support is explicitly designed to diminish as the student gains competence. There is a mechanism for reducing or withdrawing AI assistance over time. | Progressive hint levels, decreasing support across weeks, explicit fading schedules, adaptive difficulty |
| `scaffold` | Support is present and appears educational in intent, but no fading mechanism is described. The AI helps, but there is no stated plan for the help to diminish. | AI provides feedback or hints with no mention of withdrawal; tutoring system with no adaptive reduction |
| `both` | The intervention explicitly combines scaffolded and delegated elements — some activities are scaffolded while others are handed off. | Papers that scaffold debugging but delegate code generation; tools with both hint modes and solution-giving modes |
| `delegate` | The AI takes over the activity with no designed path back to student independence. The intent is for the AI to do this work, not to teach the student to do it. | Code generation as a permanent feature; AI-powered autograding replacing manual review |
| `unclear` | The paper does not describe whether support is designed to fade or persist. You cannot determine the pedagogical intent from the text. | Papers that describe the tool but not its pedagogical rationale; usage studies without design discussion |

**Critical rule:** Code design intent from what the paper describes, not from what you think the tool should do. A tool that looks like it should scaffold but is never described as scaffolding by the authors is `unclear`, not `scaffold`. A tool described as scaffolding but with no fading mechanism is `scaffold`, not `scaffold with fading`.

---

### 4.4 `effect_type`

**Question:** What kind of evidence does the study report for this activity?

| Value | Definition |
|---|---|
| `with` | **Effects with the technology:** task performance, behaviour, or outcomes measured while the AI tool was present and available. Includes: assignment grades with AI permitted, task completion rates during AI-assisted labs, code quality scores on AI-assisted work, interaction logs. |
| `of` | **Effects of the technology:** student performance measured after the AI tool was removed, or on a transfer task without AI. Includes: post-tests taken without AI, retention tests, exams where AI is not permitted, delayed assessments. |
| `both` | Both effects-with and effects-of are measured in the study. |
| `neither` | No performance outcome is measured. The study reports only perceptions, usage patterns, system descriptions, or design rationale. Satisfaction surveys and self-reported learning count as `neither`. |

**Important distinctions:**
- A study where students use AI during labs and then take a closed-book exam without AI is `both` (the lab work is effects-with, the exam is effects-of).
- A study that only measures how students interact with the AI (log analysis, prompt patterns) without any performance outcome is `neither`.
- A study that compares AI-assisted vs. non-assisted groups but measures both groups **while they have their respective conditions** is `with`, not `both` — the non-assisted group is a control condition, not an unassisted post-test.

---

### 4.5 `unassisted_measurement`

**Question:** Did the study test student performance without the AI tool at any point?

| Value | Definition |
|---|---|
| `yes` | Students were assessed, tested, or evaluated in a context where the AI tool was not available. This includes: closed-book exams, post-tests without AI, transfer tasks, delayed retention tests, any assessment explicitly conducted without AI access. |
| `no` | No assessment was conducted without AI access, OR it is not stated whether AI was available during assessment. |

**This is a factual question about what the study did, not about what it should have done.** If the paper does not mention whether AI was available during assessment, code `no` — the absence of a statement counts as absence of evidence.

---

## 5. Procedure

For each row:

1. Read the `activity_name` and `division_detail`.
2. If these provide sufficient information, code all six fields.
3. If not, consult the full text of the paper (identified by `paper_id` and `title`).
4. Assign `taxonomy_code` and `taxonomy_label` first — this anchors the rest.
5. Assign `division_of_work` based on who produces the substantive output.
6. Assign `intended_role` based on what the paper says about the design intent.
7. Assign `effect_type` and `unassisted_measurement` based on what the paper actually measured.

**Do not look at other rows for the same paper before coding each row.** The study-level fields (effect_type, unassisted_measurement) will naturally be the same across rows within a paper, but arrive at that by reading the paper, not by copying from a prior row.

---

## 6. Edge cases

| Case | Decision |
|---|---|
| Activity description says "code generation" or "AI generates code" | Code as C3.1 (Writing a program). The division_of_work field captures that the AI does it. |
| Activity involves both prompting and code generation | These should be on separate rows. If they appear as one row, code for whichever the activity_name emphasises. |
| Activity is "requesting hints" or "asking AI for help" | Code as NEW-Q. |
| Activity is "reading AI feedback" or "reviewing AI explanation" | Code as C1.1 (Code reading) if the student is comprehending content, or NEW-E (Evaluating AI output) if the student is judging correctness/quality. |
| You genuinely cannot decide between two taxonomy codes | Pick your best judgment and note the alternative in the margin or a comment. |
| The paper describes scaffolding but you see no fading mechanism | Code `scaffold`, not `scaffold with fading`. |
| You cannot determine anything about measurement from the activity description alone | Code based on what you know about the paper from its title and any available context. If still unclear, code `neither` for effect_type and `no` for unassisted_measurement. |
