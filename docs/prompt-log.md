
# PayLink - AI Prompt Log

This document records the AI tools used during Phase 1,
the prompts submitted, generated outputs, and human modifications.

## Prompt Log

### Entry 1: GitHub Actions Workflow

- **Date:** 2026-11-25
- **Task:** Create CI Workflow
- **AI Tool:** ChatGPT
- **Purpose:** Generate a GitHub Actions workflow for the PayLink backend.

**Prompt:**

"Create a GitHub Actions CI workflow for a Python FastAPI
project using MySQL. The workflow should install dependencies,
check Python syntax, run a linter, and execute tests."

**AI Output:**

Generated a GitHub Actions YAML workflow using Python,
pip, Ruff, and Pytest.

**Human Review / Modifications:**

Reviewed the generated workflow and added it to
.github/workflows/ci.yml.

**Result:**

The workflow successfully installed dependencies,
checked Python syntax, and ran the linter.
The test step failed because no tests existed yet.

---

### Entry 2: user stories

- **Date:** 2026-11-23
- **Task:** Create 13 user stories and stalkholders
- **AI Tool:** chatgpt
- **Purpose:** generate 13 user stories

**Prompt:**

# PayLink – Requirements Analysis Prompt

**Role:**  
Act as an experienced Software Requirements Analyst specializing in Software Engineering.

**Context:**  
I am working on a university project called **PayLink**, a digital wallet and bill-payment backend system in Egypt, similar to Fawry and Vodafone Cash.

Use the attached **PayLink Year Work Project – Student Brief** as your primary source. It contains the project description, business rules, functional requirements, and system constraints.

**Tasks:**

1. **Problem Summary:** Write one concise paragraph explaining PayLink's purpose, the problems it solves, and its expected benefits, focusing on reliable payments, wallet management, duplicate-charge prevention, and biller integration.

2. **Stakeholders:** Identify and briefly describe the responsibilities of Customer, Agent, System Administrator, Support Employee, Billers, PayLink Management, and Engineering Team.

3. **User Stories:** Convert exactly the first 13 functional requirements (FR-1 to FR-13) into 13 User Stories (US-01 to US-13), using:
   "As a [role], I want [feature], so that [benefit]."
   
   Include each story's ID, corresponding FR ID, title, description, and priority (Must, Should, or Could). Preserve the original meaning and priorities.

4. **Acceptance Criteria:** Provide clear, specific, testable criteria for every User Story using Given / When / Then. Include successful and important failure scenarios where applicable, following the document's business rules, payment states, and constraints.

5. **Requirements Review:** Identify unclear, incomplete, conflicting, or ambiguous requirements, along with assumptions and decisions requiring clarification.

**Constraints:**
- Use the attached Student Brief as the primary source.
- Preserve all original business rules, terminology, and numerical values.
- Do not invent features or change requirements.
- Keep the language simple, professional, and suitable for undergraduate Software Engineering students.
- Ensure consistency, completeness, clarity, and testability across all User Stories and Acceptance Criteria.
- Clearly identify information not specified in the source instead of making assumptions.

**Expected Output:**

1. Problem Summary (one paragraph).
2. Stakeholders (table: Stakeholder | Responsibilities).
3. Exactly 13 User Stories (US-01 to US-13), each containing:
   - User Story ID
   - Functional Requirement ID
   - Title
   - Description
   - Priority
   - Acceptance Criteria (Given / When / Then)
4. Requirements Review (ambiguities, missing information, assumptions, and clarification decisions).

**AI Output:**

Generated a requirements analysis containing:

Problem Summary.

Stakeholder identification and responsibilities.

13 User Stories (US-01 to US-13) linked to FR-1 to FR-13.

Acceptance Criteria using Given / When / Then.

Priority classification (Must, Should, Could).

Requirements review, including ambiguities and missing information.

**Human Review / Modifications:**

Reviewed the generated User Stories and Acceptance Criteria against the official PayLink Student Brief to ensure they preserve the original business rules, functional requirements, priorities, and numerical values. Any assumptions or unclear requirements were identified for further discussion with the team.

**Result:**

Produced a structured requirements analysis document covering the first 13 functional requirements. The output provides a clear foundation for reviewing and finalizing the User Stories before proceeding with the system design phase.

### Entry 3: Understanding Dockerfile and Docker Compose

- **Date:** 2026-11-24
- **Task:** Understanding Dockerfile and Docker Compose
- **AI Tool:** ChatGPT
- **Purpose:** o understand how Dockerfile and Docker Compose work, why they are needed, and how to implement them independently in the PayLink project.

**Prompt:**

Explain Dockerfile and Docker Compose step by step in a beginner-friendly way. Clarify the purpose of each file, explain their commands and configuration, and guide me through creating them for the PayLink project using Python and FastAPI.

**AI Output:**

Provided a step-by-step explanation of Dockerfile and Docker Compose, including their purpose, main components, and how they can be used in the PayLink project.

**Human Review / Modifications:**

Reviewed the explanation to understand the Docker concepts and how each configuration works before implementing them in the project.

**Result:**

Gained a better understanding of Dockerfile and Docker Compose and became more prepared to create and configure them independently for the PayLink project.


### Entry 4: UML Diagrams Generation

- **Date:** 2026-11-24
- **Task:** Generate UML Diagrams
- **AI Tool:** ChatGPT
- **Purpose:**  Generate the Domain Class Diagram, Use Case Diagram, and Sequence Diagram for the Pay a Bill process based on the project requirements.

**Prompt:**

"Generate the Domain Class Diagram, Use Case Diagram, and Sequence Diagram for the Pay a Bill process based on the PayLink project requirements."

**AI Output:**

Generated all three requested UML diagrams:

Domain Class Diagram.

Use Case Diagram.

Sequence Diagram for Pay a Bill.

The generated diagrams were reviewed to ensure they matched the project requirements.

**Human Review / Modifications:**

Reviewed the generated diagrams and identified an extra actor in the Use Case Diagram that was not required. Removed the unnecessary actor to make the diagram consistent with the project requirements.
**Result:**

[Final result]

Obtained the three UML diagrams. The Use Case Diagram was corrected after removing the extra actor, and the diagrams were prepared for further review and use in the project documentation.

### Entry 5: [Task Name]

- **Date:** [Date]
- **Task:** [Task]
- **AI Tool:** [Tool]
- **Purpose:** [Purpose]

**Prompt:**

[Write the exact prompt used]

**AI Output:**

[Summarize the generated output]

**Human Review / Modifications:**

[Describe the changes made]

**Result:**

[Final result]