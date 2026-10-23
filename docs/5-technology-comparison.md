# Technology Comparison

The proposed platform will collect user skills through a profile or CV, recommend suitable IT professions, identify missing requirements, and create a personal development roadmap. This section compares five technical decisions based on the project's needs and the team's development capacity. The selected solutions are planned choices; their effectiveness will be checked during implementation.

## 1. Frontend Framework

The frontend must support profile editing, career recommendations, an interactive roadmap, progress tracking, and English, Russian, and Kazakh interfaces.

**Table 1. Frontend framework comparison**

| Criterion | React | Vue 3 | Angular |
| --- | --- | --- | --- |
| UI development | Flexible component-based approach | Component-based and approachable | Structured full framework |
| TypeScript | Supported | Supported | Strong built-in support |
| Additional tools | Routing and state libraries added as needed | Official routing and state tools available | Many features provided by the framework |
| Suitability for the project | **Selected:** fits the existing prototype and team experience | Suitable alternative | Suitable, but more structure than needed |

**Decision:** React with TypeScript, Vite, and Tailwind CSS. All three options can build the platform's interface. React is the most practical choice because the team already uses it, so changing frameworks would add work without a clear benefit. [1–3]

## 2. Backend Framework

The backend must provide a REST API, process user data, access PostgreSQL, and run Python-based recommendation and roadmap modules.

**Table 2. Backend framework comparison**

| Criterion | FastAPI | Django REST Framework | Flask |
| --- | --- | --- | --- |
| Python integration | Direct | Direct | Direct |
| Request validation | Pydantic | Serializers | Extra tools or custom code |
| Built-in scope | API-oriented | Broader framework with ORM and admin tools | Lightweight core |
| Suitability for the project | **Selected:** straightforward API development | Suitable, but includes features not needed initially | Suitable, with more setup choices |

**Decision:** Python with FastAPI. It provides clear API endpoints, request validation, and automatic API documentation. The same Python backend can run the recommendation and planning algorithms. SQLAlchemy and Alembic will handle database access and schema changes. [4–6]

## 3. Database Management System

The platform needs to store users, skills, professions, requirements, projects, roadmaps, and progress. These records have many relationships.

**Table 3. Database comparison**

| Criterion | PostgreSQL | MySQL | MongoDB |
| --- | --- | --- | --- |
| Data model | Relational | Relational | Document-based |
| Connected data | SQL joins and foreign keys | SQL joins and foreign keys | References or embedded documents |
| Flexible data | JSONB | JSON | Flexible documents |
| Suitability for the project | **Selected:** combines related tables with flexible fields | Also suitable for core requirements | Less natural for the planned relational structure |

**Decision:** PostgreSQL. It fits the connections between users, professions, and skills. JSONB can store flexible data such as raw CV extraction results. Its full-text search can also support a small RAG knowledge base. A separate MongoDB database is not needed; pgvector can be considered later if vector search in the database becomes necessary. [7–9]

## 4. Career Recommendation Approach

The recommendation module must rank up to ten professions, show a match score, and explain which requirements are covered. The score will represent **coverage of defined requirements**, not the probability of getting a job.

**Table 4. Career recommendation methods**

| Criterion | Rule-based matching | TF-IDF similarity | Embeddings only | Hybrid: embeddings + weighted rules |
| --- | --- | --- | --- | --- |
| Different wording | Requires known aliases | Relies mostly on shared terms | Can identify related meanings | Uses aliases and semantic suggestions |
| Required skills | Checked directly | Not enforced by similarity | Not enforced by similarity | Checked through explicit rules |
| Explainable score | Yes | Similarity is not a match percentage | Similarity is not a match percentage | Yes, based on weighted requirement coverage |
| Main limitation | May miss unfamiliar wording | Limited semantic understanding | Related skills may be confused | Requires tested weights and skill mappings |

**Decision:** **Hybrid semantic matching with weighted rules.** The system will link skills to ESCO identifiers and use embeddings to suggest possible matches when wording differs. The matching rules will verify requirements and calculate a weighted percentage. The result will include matched and unconfirmed skills. A simpler exact/alias-based method will be used as a baseline to evaluate the hybrid approach. [10–12]

## 5. Personalized Roadmap Planning

After a user chooses a profession, the platform must organize missing skills, projects, language development, internship preparation, and optional activities into a realistic sequence.

**Table 5. Roadmap planning approaches**

| Criterion | Fixed templates | Direct LLM generation | LLM + RAG | Dependency-based planning + RAG |
| --- | --- | --- | --- | --- |
| Personalization | Limited without extra rules | Based on the prompt | Based on prompt and retrieved sources | Based on the user's skill gap and rules |
| Learning order | Predefined | Not reliably enforced | Sources alone do not enforce order | Prerequisites are checked by an algorithm |
| Reliability | Depends on templates | May include unsupported steps | Better grounding, but errors remain possible | Structured steps with source-based explanations |
| Main limitation | Difficult to adapt widely | Unpredictable plans | Does not solve ordering | Requires a reviewed dependency graph |

**Decision:** **Dependency-based planning with RAG-assisted explanations.** We will prepare a small graph of skill prerequisites for the initial IT professions. Our Python logic will identify required steps, order them using NetworkX, and add practical and career activities through rules. RAG will retrieve relevant information from a reviewed knowledge base; the LLM will write brief explanations but will not change the mandatory steps. Plans will be saved so that reopening them does not generate a different roadmap. Automatic course search is outside the required scope. [7, 13–14]

## Conclusion

**Table 6. Selected solutions**

| Decision | Selected solution |
| --- | --- |
| Frontend | React, TypeScript, Vite, Tailwind CSS |
| Backend | Python, FastAPI |
| Database | PostgreSQL |
| Career recommendations | ESCO, embeddings, weighted rule-based ranking |
| Roadmap | Skill dependency graph, rule-based planning, RAG-assisted LLM |

These decisions support the platform's core functions without making the recommendation score or roadmap order depend on an external LLM. The selected AI methods and planning rules still require testing. We will evaluate recommendation quality against a rule-based baseline and check roadmap order and usefulness with expert feedback.

## References

[1] React. *Quick Start; Using TypeScript*. https://react.dev/learn ; https://react.dev/learn/typescript  
[2] Vue.js. *Using Vue with TypeScript*. https://vuejs.org/guide/typescript/overview  
[3] Angular. *What is Angular?* https://angular.dev/overview  
[4] FastAPI. *Features*. https://fastapi.tiangolo.com/features/  
[5] Django REST framework. *Serializers*. https://www.django-rest-framework.org/api-guide/serializers/  
[6] Flask. *Welcome to Flask*. https://flask.palletsprojects.com/en/stable/  
[7] PostgreSQL. *Constraints; JSON Types; Full Text Search*. https://www.postgresql.org/docs/current/ddl-constraints.html ; https://www.postgresql.org/docs/current/datatype-json.html ; https://www.postgresql.org/docs/current/textsearch-intro.html  
[8] MySQL. *The JSON Data Type*. https://dev.mysql.com/doc/refman/8.4/en/json.html  
[9] MongoDB. *Data Modeling*. https://www.mongodb.com/docs/manual/data-modeling/  
[10] ESCO. *Use ESCO*. https://esco.ec.europa.eu/en/use-esco  
[11] scikit-learn. *TfidfVectorizer*. https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html  
[12] Reimers, N., & Gurevych, I. (2019). *Sentence-BERT: Sentence embeddings using Siamese BERT-networks*. https://doi.org/10.18653/v1/D19-1410  
[13] NetworkX. *topological_sort*. https://networkx.org/documentation/stable/reference/algorithms/generated/networkx.algorithms.dag.topological_sort.html  
[14] Lewis, P., et al. (2020). *Retrieval-augmented generation for knowledge-intensive NLP tasks*. https://arxiv.org/abs/2005.11401  
