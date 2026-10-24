# Development of an Intelligent Platform for Personalized Career Navigation and Professional Development Planning

A diploma project at Astana IT University, School of Software Engineering.

Students and early-career IT specialists often struggle to relate their skills and projects to the requirements of a profession. Job descriptions list technologies but rarely explain which skills a beginner already covers, which requirements need clarification, or what to learn next. This project addresses that gap by connecting profile analysis, career matching, and development planning in a single web application.

## Scope

Users will be able to enter their background manually or upload a PDF/DOCX CV, review the extracted information, and explore an initial catalogue of 10 IT professions. The system will rank career options using documented role requirements, identify matched, missing, and unconfirmed requirements, and support independent selection of a target profession.

For the selected role, the application will build a development roadmap with prerequisite-based steps, practical tasks, reviewed learning resources, and progress tracking. Users will be able to adjust their available study time and revisit saved plans. The interface will support English, Russian, and Kazakh.

A career-match percentage will represent coverage of documented role requirements, not the likelihood of being hired. Recommendations and roadmap quality will be evaluated against a simpler matching baseline and through expert and user feedback.

## Planned technology stack

| Area | Selected technologies and approach |
| --- | --- |
| Frontend | React, TypeScript, Vite, Tailwind CSS |
| Backend | Python, FastAPI, REST API |
| Data storage | PostgreSQL, SQLAlchemy, Alembic |
| Career matching | ESCO skill mappings, semantic embeddings, weighted rules |
| Roadmap planning | Prerequisite-based planning with NetworkX; RAG-assisted explanations |

## Team

| Member | Responsibilities |
| --- | --- |
| Aida Bekpayeva | Backend and API, CV skill extraction and normalization, career matching, skill-gap and roadmap logic, deployment and CI/CD, expert evaluation |
| Quralai Baqytnur | Database schema, migrations and reference data, frontend and UX, multilingual interface, API integration, user interviews and usability testing |

Supervisor: Sakhipov A.A., PhD, Assistant Professor, School of Software Engineering.

## Current status: October 2026

The project is in the research and design stage. The repository contains the project proposal, supporting research, requirements, architecture diagrams, UX mockups, an evaluation plan, and project management materials. Application development is scheduled for subsequent milestones.

There is no runnable application yet. Installation, execution, and automated testing instructions will be added when the first implementation is available.

The October submission is marked with the `pre-defense-1` tag.

## Documentation

- Research and scope: [Project proposal](docs/1-project-proposal.md) · [Evidence of relevance](docs/2-evidence-of-relevance.md) · [Literature review](docs/3-literature-review.md) · [Existing system comparison](docs/4-existing-system-comparison.md) · [Technology comparison](docs/5-technology-comparison.md)
- Design: [Requirements specification](docs/6-requirements-specification.md) · [Architecture and diagrams](docs/7-architecture-and-diagrams.md) · [UX prototype](docs/8-ux-prototype.md)
- Evaluation and management: [Verification and evaluation plan](docs/9-verification-and-evaluation.md) · [Project management and risks](docs/10-project-management-and-risks.md) · [Supervisor feedback](docs/11-supervisor-feedback.md)

Diagram sources and exports are under [`docs/diagrams/`](docs/diagrams/). Prototype screenshots are under [`docs/prototype/exports/`](docs/prototype/exports/); the [Figma prototype](https://www.figma.com/design/G4VSmgYMqxjA1exqXXMdKz/Career-navigation-platform-UX-prototype?node-id=0-1) shows the planned user flows.

Tasks, milestones, and individual contributions are tracked in [YouTrack](https://abekpaye.youtrack.cloud/projects/CN). Development changes are linked to the corresponding task and reviewed through pull requests.
