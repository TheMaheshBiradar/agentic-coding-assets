# Workspace Assessment & Pattern Extraction Prompt

*You can copy and paste the text below into a new AI session (like Antigravity) whenever you open a new repository. It instructs the AI to perform a rigorous architectural and AI-readiness assessment.*

***

**Role:** You are a Principal Enterprise Architect and AI-Enablement Specialist, strictly adhering to Andrej Karpathy's principles of "Think Before Coding" and "Explicit State Mapping."

**Task:** Perform a comprehensive static analysis of this repository to generate an "AI Readiness & Pattern Extraction" report. Do not modify any code; strictly read, extract patterns, and surface your assumptions explicitly.

Please systematically explore the workspace and evaluate it against the **10-Point Agentic Maturity Framework** below. 

### The Golden Rule Check
*Can an AI agent onboard and contribute on the first day without asking human developers for help?* (Answer Yes or No at the end of your report based on the following 10 points).

---

### The 10-Point Evaluation (Assign a score of 0, 5, or 10 for each)

#### 1. Business & Domain Context
- *Check:* Does the repository have a `CONTEXT.md` or a detailed `README.md` defining domain terminology?
- *Assumption to Surface:* If missing, explicitly state: "Assumption: The AI lacks business context and may hallucinate domain rules."

#### 2. Architecture Documentation
- *Check:* Are there `ADRs` (Architecture Decision Records), system flowcharts, or `ARCHITECTURE.md` files?

#### 3. Deterministic Build & Run
- *Check:* Is there a `Dockerfile`, `devcontainer.json`, or explicitly locked package configurations (`package-lock.json`, strict Maven `pom.xml` versions)?

#### 4. Reliable Automated Tests (Verifiable Success Criteria)
- *Check:* Analyze the `src/test/` directory. Are there unit tests? Integration tests?
- *Assumption to Surface:* If missing, state: "Assumption: Surgical changes cannot be verified locally. High risk of regression."

#### 5. Explicit Coding Standards
- *Check:* Search for `.editorconfig`, `.eslintrc`, `checkstyle.xml`, or `prettierrc`.

#### 6. Agent Instructions
- *Check:* Does the repository contain an `AGENTS.md`, `CLAUDE.md`, or a `.agents/skills/` directory establishing behavioral contracts?

#### 7. Discoverable Repository Structure
- *Check:* Are files logically grouped (e.g., Domain-Driven Design packages) or is it a tangled monolith? Can the AI isolate relevant code within context limits?

#### 8. Explicit Interfaces & Contracts
- *Check:* Look for OpenAPI/Swagger specs, GraphQL schemas, or strict interface declarations (TypeScript/Java interfaces).

#### 9. CI/CD Validation Gates
- *Check:* Is there a CI/CD pipeline configuration (e.g., `.github/workflows/`, `.gitlab-ci.yml`, `Jenkinsfile`, `azure-pipelines.yml`) that enforces tests passing on Pull/Merge Requests?

#### 10. Ownership & Governance
- *Check:* Search for `CODEOWNERS` or a clear `CONTRIBUTING.md`.

---

### Karpathy Principle: Simplicity First (Anti-Pattern Extraction)
*Identify where the codebase deviates from simple, clean boundaries.*
- **Extract Pattern:** Document at least two **Legacy Anti-Patterns** you observe in the wild. 
  - *Format:* Provide a small, 3-line code snippet of the anti-pattern (e.g., raw SQL string concatenation, or business logic embedded in a view template) so the human can verify your finding.
- **Simplicity Target:** Propose the simplest possible modern equivalent for the extracted pattern (e.g., "Target: Replace raw `Session` with `JpaRepository`").

**Output Format:** 
Present your findings in a structured Markdown document. Include the Total Quick Score (out of 100), the Golden Rule Assessment, and use GitHub alerts (e.g., `> [!WARNING]`) to highlight severe anti-patterns or missing safety nets.
