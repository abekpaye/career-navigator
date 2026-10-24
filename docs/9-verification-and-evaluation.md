# 9 Verification and evaluation plan

Verification will check the requirements defined in Section 6. Evaluation will measure extraction and matching quality, roadmap consistency, usability and perceived usefulness. This section describes planned work; no completed tests or evaluation results are claimed.

## 9.1 Testing plan

Unit, integration and end-to-end tests will verify the acceptance criteria in Section 6. Manual checks will assess interface quality and content clarity.

| Area | Requirements | Planned checks |
| --- | --- | --- |
| Accounts and profiles | F-01–F-05 | Test authentication, manual editing, PDF/DOCX extraction, skill mapping and user review before analysis. Invalid uploads must preserve saved data. |
| Career recommendations | F-06–F-09, F-11 | Check the ten-role catalogue, weighted scores, explanations, incomplete-data handling, independent target selection and explicit recommendation updates. |
| Roadmaps and progress | F-12–F-17 | Check gap coverage, prerequisites, step information and reviewed resources. Time changes and progress updates must preserve profile data; replacement plans must preserve earlier plans. |
| Persistence, security and privacy | F-18, NF-01–NF-03 | Verify saved data after reload and restart, account isolation, credential protection and CV privacy. Interrupted or repeated saves must not lose or duplicate records. |
| Reproducibility and failures | NF-04, NF-05 | Confirm identical scores and required steps for fixed inputs and rules. Simulate AI failures and verify fallback options without losing saved results. |
| Performance and interface | NF-06–NF-09 | Measure response times under Section 9.3 conditions. Check desktop and mobile layouts, three interface languages, keyboard navigation and clear feedback. |

User sessions will cover profile review, recommendation interpretation, target selection, roadmap creation and progress updates. Task completion, assistance and feedback will be recorded, including whether users understand the score and their next action.

Results will be linked to requirement IDs. All Must acceptance criteria must pass; failed checks will be corrected and repeated. Should features F-10 and F-19 will be tested separately if implemented.

## 9.2 Outcome metrics

The following metrics will assess technical quality and usefulness to users.

| Outcome | Measurement | Proposed target or decision rule |
| --- | --- | --- |
| CV skill extraction | Precision, recall and F1 against manually labelled skills, before user correction. | Report results and extraction errors by language and file format. |
| Skill mapping | Precision and recall of ESCO mappings against manually checked labels. | Report correct, incorrect, missed and unresolved mappings. |
| Career recommendations | Precision at 3 against practitioner judgements on the same held-out profiles. | Higher than the baseline; otherwise, no ranking improvement is demonstrated. |
| Roadmap quality | Prerequisite order, required step information and reviewed resources; practitioner ratings of relevance and actionability from 1 to 5. | All structural checks pass. Report practitioner ratings and required revisions. |
| User task completion | Percentage of tasks completed without assistance, with errors and help requests recorded. | Report completion rates by task and correct problems blocking the core workflow. |
| Clarity and usefulness | User ratings from 1 to 5 and questions about the match score and next development step. | Report ratings, correct interpretations and recurring difficulties. |
| API performance | Median and 95th-percentile response times, errors and timeouts. | At least 95% of ordinary reads and saves complete successfully within 2 seconds. |

## 9.3 Measurement conditions

Every evaluation run will record the Git commit, dataset split, catalogue and ESCO versions, alias dictionary, semantic model and thresholds, weights, planning rules, reviewed source snapshot and AI model or prompt settings. Identical saved inputs and versions must reproduce scores and required tasks, although generated wording may vary.

Performance testing will use the integrated React, FastAPI and PostgreSQL application in one documented environment. The report will record CPU, memory, operating system, deployment configuration and network location. Seed data will contain ten test accounts, their profiles and three saved plans per account, covering all ten professions. Five concurrent authenticated virtual users will alternate ordinary reads and valid saves on separate accounts, with a one-second pause between requests. Following a one-minute warm-up, three measured five-minute runs will each collect at least 100 reads and 100 saves; extend a run if needed. Record median and 95th-percentile latency by operation, throughput, errors and timeouts from the load client's request start to response completion. Fast error responses will not count as successful requests.

CV extraction and AI explanation generation will be measured separately because they involve external services. Their durations, failures and configured timeout limits will be recorded. Each must show loading feedback and end with a result or clear recovery option. Simulated service failures will be distinguished from measurements using the real provider.

Interface checks will cover desktop Chrome and Firefox and mobile Chrome. The core workflow will be checked in English, Russian and Kazakh, including language switching without losing saved data or progress. These checks will not be presented as support for every browser or full accessibility certification.

## 9.4 Baseline comparison

The baseline will normalise text and match skills through exact names and a fixed alias dictionary. It will use the same ten-role catalogue, requirement weights, coverage formula, insufficient-data rules and tie-breaking policy as the proposed system. It will not use embedding-based semantic mapping.

The proposed hybrid method will add semantic mapping for alternative wording while retaining explicit weighted scoring. Both methods will receive identical reviewed profiles. Aliases, semantic thresholds and other settings will be fixed using development cases before running the held-out evaluation. Test labels will not be used for tuning; later revisions will be reported separately.

This comparison will isolate the contribution of semantic mapping. Results will include correct additional matches, incorrect semantic matches and missed skills. A gain will be claimed only if the held-out measurements support it.
