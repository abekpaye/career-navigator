# Project Management and Risks

## 1. Project Management and Tracking

- Repository: [GitHub](https://github.com/abekpaye/career-navigator)
- Task tracking: [YouTrack](https://abekpaye.youtrack.cloud/projects/CN)

Project milestones are tracked in YouTrack. Tasks record an owner, priority, deadline, expected result and acceptance criteria. Work is committed in task-specific branches, with task IDs referenced in commits and pull requests. The other team member reviews each pull request before merging into `main`, and the relevant change is linked to its YouTrack task. Weekly supervisor meetings and monthly milestone reviews are planned. The required pre-defense tags are `pre-defense-1`, `pre-defense-2` and `final-pre-defense`.

## 2. Team Responsibilities

| Team member | Main responsibilities |
| --- | --- |
| Aida Bekpayeva | Backend and API development; CV skill extraction and normalization; career matching, skill-gap analysis and roadmap logic; deployment and CI/CD; expert evaluation of recommendations. |
| Quralai Baqytnur | Database design, migrations, persistence and data loading; collection and review of occupation and skill data; frontend, UX, multilingual interface and API integration; user interviews and usability testing. |

## 3. Project Milestones

| Period | Planned work | Milestone |
| --- | --- | --- |
| Oct 2026 | Prepare the required research, comparisons, requirements, diagrams, prototype materials, evaluation and project plans, and supervisor feedback. | October documentation submission. |
| Nov 2026 | Review reference-data sources, prepare the initial occupation and skill dataset and database design, and agree on API contracts and user flows. | Initial reference dataset, database design and agreed interfaces. |
| Dec 2026–Jan 2027 | Implement database storage, backend APIs, profile management and initial career matching; build the corresponding web screens and connect them to the API. | Working application covering profiles and initial career recommendations. |
| Feb–Mar 2027 | Complete CV processing, personalized roadmap logic, reviewed step content and progress tracking; finish the relevant web screens, localization and integration, and obtain expert feedback. | Integrated application with required features ready for user testing. |
| Apr 2027 | Test complete workflows, evaluate recommendation quality, fix defects and complete the thesis report. | Tested application and completed thesis report. |
| May 2027 | Present the work at pre-defense, address comments and prepare the final demonstration and defense materials. | Revised application and final defense materials. |

## 4. Project Dependencies

| Dependency | Reason                                                                                |
| --- |---------------------------------------------------------------------------------------|
| Agreed requirements, database schema and API contracts → implementation | Database, backend and frontend must use compatible data and interfaces.               |
| Reviewed occupation and skill data → career recommendations | Matching depends on documented role requirements and consistent skill records.        |
| Selected profession, reviewed profile and skill prerequisites → personalized roadmap | Plans follow the user's target and known skills.                                      |
| Reviewed learning sources → roadmap explanations | Generated explanations must be based on documented material.                          |
| Integrated database, backend and frontend → end-to-end evaluation | Complete user workflows must be tested as a connected system.                         |
| External datasets, AI services and evaluation participants → relevant work | Data rights, service availability and access to experts and students affect delivery. |

## 5. Risk Management

Likelihood and impact are preliminary Low, Medium or High estimates. Each risk has one owner responsible for monitoring it and coordinating the response.

| Risk | Likelihood | Impact | Mitigation | Owner |
| --- | --- | --- | --- | --- |
| Incomplete or inconsistent occupation and skill data | Medium | High | Verify sources and usage rights; document uncertain requirements for the ten-role catalog. | Quralai Baqytnur |
| Database schema or data integrity problems | Medium | High | Review the schema against API needs; use migrations and integrity checks. | Quralai Baqytnur |
| Incorrect CV extraction or multilingual skill matching | High | Medium | Test representative inputs and let users correct extracted information. | Aida Bekpayeva |
| Misleading match scores or roadmap guidance | Medium | High | Use documented rules, check prerequisites and source support, and seek expert review. | Aida Bekpayeva |
| External AI service limits or costs | Medium | Medium | Control usage and keep manual input and reviewed content available as fallbacks. | Aida Bekpayeva |
| Exposure of private profile or CV data | Low | High | Restrict API and database access; minimize external sharing and exclude secrets and personal data from logs and Git. | Aida Bekpayeva |
| Delays in database, API and frontend integration | Medium | High | Agree on contracts early, integrate by feature and review progress against milestones. | Quralai Baqytnur |
| Poor usability or multilingual interface issues | Medium | Medium | Test main user flows and languages early; revise unclear screens and messages. | Quralai Baqytnur |
