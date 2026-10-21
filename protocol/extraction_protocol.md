# Data Extraction Instructions

**Scoping review:** Generative AI in Introductory Programming Education
**Reviewer:** Beimnet Zenebe
**Purpose of this document:** full-text paper data extraction — one row per activity (with the study details for each paper)
---

## 1. What the review is asking

Three research questions:

- **RQ1** — What uses of generative AI are reported in introductory programming education?
- **RQ2** — What programming difficulties are addressed through these uses?
- **RQ3** — How do the included studies characterise the relationship between GenAI use and the targeted activity: does it scaffold the activity, or substitute for it?

## 2. Unit of extraction

**One row per activity.**

An *activity* is a task the student performs that could be named independently on a syllabus or in a lab sheet.

| Rule | Detail |
|---|---|
| **Student-performed** | If no student does it, it is not an activity. An LLM generating exercises that an instructor reviews is not an activity. A student interpreting an auto-generated hint is. |
| **Independently nameable** | "Wrote a function" and "debugged the function" are two activities. "Opened the IDE" is not. |
| **Distinguished by delegation** | If the same nominal task is performed under two different arrangements (e.g. with and without AI, or at two scaffolding levels), create **one row per arrangement**. |

---

### 4.1 Meta Data

`paper_id` , `citation`

Supplied from the Zotero export. 

### 4.2 Descriptive Fields

| Field | Values |
|---|---|
| `country` | Where the study ran; `not stated` |
| `course` | Verbatim course description (e.g. "CS1", "introductory Python for non-majors") |
| `course_level_confirmed` | `yes` / `inferred` / `not stated` — is it explicitly a first programming course? |
| `n_participants` | Number; `not stated` |
| `study_design` | `experience report` / `observational` / `interaction log analysis` / `controlled comparison` / `randomised trial` / `survey` / `think-aloud or lab study` / `mixed` |
| `tool_named` | e.g. ChatGPT, Copilot, CodeHelp |
| `tool_type` | `commercial general-purpose` / `purpose-built for this course` / `both` / `not stated` |

### 4.2 Study Level Conceptual Fields

| Field | Values |
|---|---|
| `ai_constrained` | Did the tool deliberately withhold, degrade or delay output? Describe briefly. |
| `measurement_type` | See Sec 7 |
| `ability_measured` | See Sec 7 |
| `authors_own_framing` | One line: how do the authors describe the AI's role? Quote if possible. |

### 4.3 Activity level 

`activity_name` · `delegation_level` · `delegated_to` · `residual_knowledge_demand` · `measurement_is_activity_specific` · `durability` · `evidence` · `confidence` · `notes` · `framework_strain`


## 5. Activity fields, defined

### 5.1 `activity_name` — controlled vocabulary

> see activity-taxonomy document

### 5.5 `delegation_level`

| Value | Test |
|---|---|
| `student-led` | The student performs the task; AI is available but supplies no content toward the assessed artefact |
| `AI-proposes` | AI offers content the student must evaluate, accept, reject or modify |
| `AI-executes` | AI produces the content; the student directs, reviews or integrates it |
| `full` | AI produces the content and the student does not meaningfully inspect or alter it |


### 5.8 `quadrant` — derived

| | Traditional skill (`unchanged`) | New or transformed (`transformed` / `new`) |
|---|---|---|
| **AI executes** (`AI-executes` / `full`) | **Q1** AI-executed, traditional | **Q4** AI-executed, new |
| **Human executes** (`human-led` / `AI-proposes`) | **Q2** Human-executed, traditional | **Q3** Human-executed, new |

Q4 means **the student's role inside an AI-automated workflow** — interpreting auto-generated hints, acting on auto-generated tests. If there is no student role at all, there is no activity and no row.


---

## 7. Measurement and durability

### 7.1 `measurement_type`

| Value | Test |
|---|---|
| `none` | No outcome is measured. Usage, satisfaction and perception alone count as `none` for this field. |
| `task success only` | Completion, correctness, time, grades — measured while the AI was available |
| `assisted performance` | A structured measure of performance with the AI present (e.g. code quality scored on AI-assisted submissions) |
| `unassisted post-test or transfer` | Performance measured **with the AI removed**, or on a transfer task |

Only the last supports any claim about effects *of* the technology.

### 7.2 `ability_measured`

Following Salomon et al., record separately:

- `with` — performance observed while the student and the tool worked together
- `of` — performance observed after the partnership was withdrawn
- `both`
- `neither`


### 7.3 `measurement_is_activity_specific`

`activity-specific` — the paper measures this activity in particular
`inherited from study` — the paper reports one outcome covering the whole intervention, copied down from the study block

Where inherited, copy the study-level value and mark it. Do not claim an activity-specific effect the paper did not measure.

### 7.4 `durability` — derived from evidence only

| Value | Condition |
|---|---|
| `scaffold` | Unassisted or transfer performance was measured **and** was maintained or improved |
| `scaffold w fading` | Unassisted or transfer performance was measured **and** (gradual) fading of tool was stated |
| `offload` | Unassisted or transfer performance was measured **and** was not maintained |
| `not determinable` | No unassisted measurement exists |


