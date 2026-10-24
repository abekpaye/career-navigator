# 7 Architecture and diagrams

The proposed application will use a web client, a Python/FastAPI backend and a PostgreSQL database. The diagrams describe the system’s external interactions, user scenarios and internal components.

## 7.1 System context diagram

![System context diagram](/docs/diagrams/exports/system-context.png)

The platform connects students and early-career users with career recommendations and development roadmaps. Users provide profile information, select a profession and record progress. The platform returns explained results and saved plans.

ESCO provides occupation and skill identifiers, labels and aliases. Reviewed reference sources provide selected vacancy evidence, prerequisites and learning resources. These data are prepared and imported by the project team. The external AI provider supports CV information extraction and explanations based on retrieved sources, receiving only the information needed for each task.

## 7.2 Use case diagram

![Use case diagram](/docs/diagrams/exports/use-case.png)

The main workflow covers account access, profile creation, information review, career recommendations, target selection and roadmap creation. CV import is an optional extension of profile creation; users can enter information manually. Newly entered or extracted information must be reviewed and saved before analysis.

Users can independently choose any catalogue profession, explicitly refresh recommendations, reopen earlier plans, update or undo progress and change weekly study time. Comparing two professions has Should priority. The external AI provider participates in CV extraction and preparation of roadmap explanations.

## 7.3 Component diagram (draft)

![Component diagram (draft)](/docs/diagrams/exports/component.png)

The web client, built with React, TypeScript, Vite and Tailwind CSS, provides profile editing, career exploration, roadmaps and progress tracking in English, Russian and Kazakh. It communicates with the REST API over HTTPS, exchanging structured data as JSON. The API validates requests, identifies the authenticated user and routes operations to internal backend modules.

The accounts and profiles module manages authentication, record ownership, manual entry and CV processing. Extracted information returns to the client as an editable draft. After user review and saving, the career recommendations module normalises skills, applies ESCO and semantic mappings, and calculates weighted requirement coverage. Results distinguish matched requirements, known gaps and unknown information.

The roadmaps and progress module uses the reviewed profile and selected role requirements to identify development tasks. NetworkX orders tasks according to prerequisites. The module calculates time estimates, records progress and preserves earlier plan versions.

The catalogue and retrieval module supplies documented requirements, prerequisites and reviewed resources. The AI integration adapter sends relevant CV text or fixed tasks with retrieved sources to the external provider and validates its output. Backend rules determine scores and required roadmap steps; AI-generated wording does not change these decisions.

The persistence layer uses SQLAlchemy and transactions to read and save users, profiles, analyses, roadmaps, progress and reference data in PostgreSQL. Results return through the API to the client. Reopening a roadmap loads its saved content, while recommendation refreshes and plan replacement require explicit user actions.
