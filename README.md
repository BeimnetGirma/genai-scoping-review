# What Changes When GenAI Enters the Classroom? A Scoping Review of Activities, Division of Work, and Measurement Practices

**Supplementary materials** for:

> [authors]. (2027). *Generative AI in Introductory Programming Education: A Scoping Review of Activities, Division of Work, and Measurement Practices* Submmitted to the 2027 IEEE/ACM International Conference on Software Engineering: Software Engineering Education and Training (ICSE-SEET '27).

## Overview

This repository contains the data, protocols, and analysis scripts for a scoping review examining how generative AI interacts with programming activities in introductory courses. The review analysed 110 studies (294 activity instances) and addressed three research questions:

- **RQ1:** What programming activities are reported as involving generative AI in introductory programming education?
- **RQ2:** How is the implementation work divided between student and AI across these activities?
- **RQ3:** To what extent do studies measure whether students can subsequently perform the identified activities without AI assistance?

## Repository Structure

```
├── data/
│   ├── extraction_data.csv          # Complete coded dataset (294 activities)
│   ├── included_studies.csv         # List of all 110 included studies
│   └── reliability_arbitration.csv       # 20-paper reliability sample with author, AI, and coauthor codings
│
├── protocols/
│   ├── screening_protocol.md        # Title/abstract screening criteria 
│   ├── extraction_protocol.md       # Data extraction and charting protocol
│   ├── reliability_protocol.md      # Reliability coding instructions provided to the second rater
│   └── activity_taxonomy.docx       # Programming activity taxonomy (27 activities, 6 clusters)
│
├── scripts/
│   └── generate_figures.py          # Python notebook to reproduce all figures from extraction_data.csv
│
└── README.md
```

## Data

**extraction_data.csv** — One row per activity instance. Fields include: paper ID, activity name, taxonomy code (C1.1–C6.1), division of work (student-led / AI-proposes / shared / AI-led), implementation responsibility (student-implemented / AI-implemented / shared), intended role (scaffold / delegate / both / unclear), effect type (with / of / both / neither), and unassisted measurement (yes / no). This is the dataset from which all reported figures and statistics are derived.

**included_studies.csv** — Study-level metadata for all 110 included papers: paper ID, title, authors, year, venue, DOI, country, programming language, and GenAI tool used.

**reliability_arbitration.csv** — The 20-paper sample used for the coding consistency check. Contains the first author's coding, the second rater's (Gemini 3.5) independent coding, and the arbitrator's resolution for each disagreement, with reasoning.

## Protocols

**screening_protocol.md** — The inclusion/exclusion criteria, and decision procedure used during title and abstract screening in ASReview. Documented prior to screening.

**extraction_protocol.md** — The data extraction and charting protocol, including field definitions, coding rules, evidence requirements, and edge-case decisions.

**reliability_protocol.md** — The coding instructions provided to the second rater (Gemini 3.5) for the reliability check. Contains the same field definitions and taxonomy reference used by the first author.

**activity_taxonomy.docx** — The complete programming activity taxonomy: 24 activities constructed from Luxton-Reilly et al. (2018) SLR plus 3 post-GenAI extensions identified inductively during extraction. Activities are organised into 6 clusters with codes, labels, and definitions.

## Scripts

**generate_figures.py** — A Python script (designed for Jupyter Notebook) that reads `extraction_data.csv` and generates all figures reported in the paper. 

## Citation

If you use these materials, please cite the paper:

```bibtex
citation details
```

## License

TBD

## Contact

TBD
