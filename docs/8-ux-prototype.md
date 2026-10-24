# 8 UX and Prototype

The UX prototype illustrates how students and early-career users create a profile, explore IT professions, choose a target role and follow a personal development roadmap. The screen exports below show the main user scenarios without requiring access to Figma.

## 8.1 Prototype access

[View the Career navigation platform UX prototype in Figma](https://www.figma.com/design/G4VSmgYMqxjA1exqXXMdKz/Career-navigation-platform-UX-prototype?node-id=0-1)

The Figma file is shared with view access for anyone with the link. The PNG exports are stored in this repository under `docs/prototype/exports/`.

## 8.2 Main user flow

Users start by choosing CV import or manual profile entry. They review and save their information before viewing recommendations. They can open a recommended profession or independently select any role from the IT career catalogue. After reviewing the role requirements, they set their weekly study time and create a roadmap. They can then open individual steps, consult suggested resources and update their progress.

The workspace sidebar provides access to the profile, recommendations, career catalogue and roadmap.

## 8.3 Key screens and user Scenarios

### 8.3.1 CV Upload or Manual Entry

The entry screen presents CV selection and manual entry as alternative ways to create a profile. It shows the supported file formats and size limit. The current demonstration explicitly states that automatic extraction is unavailable and offers sample CV data or manual entry to continue.

![CV upload and manual profile entry](/docs/prototype/exports/upload-cv.png)

### 8.3.2 Profile review

Users review or enter technical skills, foreign languages, projects, work experience, internships, education and career interests. Technical skills are listed without proficiency percentages; foreign language levels are self-assessed separately. Project fields describe the task, personal contribution, technologies and result. Users select **Save and view recommendations** to continue after reviewing their information.

![Profile review before recommendations](/docs/prototype/exports/review-profile.png)

### 8.3.3 Saved profile

The profile remains accessible from **My profile** in the workspace. Users can reopen their information, add or remove details and explicitly save changes. This screen provides a way to correct or clarify profile information after the initial setup.

![Saved profile in the user workspace](/docs/prototype/exports/saved-profile.png)

### 8.3.4 Career recommendations

Recommendations show IT roles with example requirement-fit scores, matched criteria and information to clarify or develop. Users can search, filter by area and open career details. The percentage represents profile coverage of a role template, rather than the probability of getting a job or proficiency in an individual skill. Unlisted information remains unknown.

![Career recommendations with requirement-fit explanations](/docs/prototype/exports/recommendations.png)

### 8.3.5 Independent career exploration

The **Explore IT careers** screen presents the career catalogue with search and area filters. Users can choose any profession regardless of its recommendation position or current fit. Opening **View career details** leads to the selected role's requirements.

![IT career catalogue for independent profession selection](/docs/prototype/exports/career-catalog.png)

### 8.3.6 Career details and target selection

The role details screen explains the example score and separates matched requirements, requirements not met and information that needs clarification. Users can inspect the calculation criteria, return to their profile or select **Create Roadmap** for this profession.

![Selected profession and explained requirement coverage](/docs/prototype/exports/career-details.png)

### 8.3.7 Roadmap setup

Before creating a plan, users see their selected profession and can inspect the requirements the plan will address. They enter their available hours per week and select the language of external materials. **Create plan** continues to the roadmap. The screen explains that time estimates are approximate and that unknown profile information is a planning assumption.

![Roadmap setup with weekly study time and material language](/docs/prototype/exports/roadmap-setup.png)

### 8.3.8 Personal roadmap

The roadmap shows the selected profession, weekly study time, estimated effort, approximate remaining duration and completion progress. Each step includes its purpose, expected output, estimated effort and status; dependencies are shown where applicable. Users can continue the roadmap, open an individual step or access plan settings. Roadmap completion remains separate from profile information and requirement-fit scores.

![Personal roadmap with steps, estimates and progress](/docs/prototype/exports/roadmap.png)

### 8.3.9 Step details and progress tracking

A step explains why the task matters, why it appears in the plan, its expected output and completion criterion. Suggested actions and an external resource support independent work. Users can change the step status, mark it completed, move to the next step or return to the roadmap. Completing a task changes roadmap progress; users update their profile separately when they choose.

![Roadmap step details, resource and progress controls](/docs/prototype/exports/step-details.png)
