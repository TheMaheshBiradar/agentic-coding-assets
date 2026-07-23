# Reusable Prompt: Full Front-to-Back Tech Stack Audit

**Usage:** Paste this prompt into any AI session (Copilot, Claude, Antigravity, etc.) with a new repository open.
Adjust section headers if the project isn't Java (e.g., swap "Servlet container" for "Node.js runtime").

***

You are a Principal Enterprise Architect performing a full front-to-back technology stack audit of this repository. Do NOT modify any code - strictly read, explore, and document.

Systematically explore every layer of the codebase and produce a single `techstack.md` file. 

## What to investigate per layer:

### 1. Frontend & UI
- View technology (JSP, Thymeleaf, React, Angular, Vue) with exact versions.
- CSS Frameworks & Preprocessors (Tailwind, Sass, Bootstrap).
- State Management (Redux, Vuex, Context API).
- Frontend Build Tools (Webpack, Vite, npm scripts).

### 2. API & Integration Layer
- REST/SOAP endpoints - list key URL patterns and frameworks (Spring WebFlux, Jersey, Express).
- API Contracts (OpenAPI/Swagger, gRPC Protobufs, GraphQL Schemas).
- Real-time communication (WebSockets, Server-Sent Events).
- API Gateway / Routing configurations (Spring Cloud Gateway, Zuul, Nginx).

### 3. Service / Business Logic Layer
- Core Framework (Spring Boot, Jakarta EE, NestJS) with exact versions.
- Batch Processing & Scheduling (Spring Batch, Quartz, `@Scheduled`).
- **Caching Strategy:** (EhCache, Redis, Hazelcast, Caffeine). Identify config files and eviction policies.
- **Messaging & Event Streaming:** (Kafka, RabbitMQ, ActiveMQ, JMS, SQS). Identify topics/queues.

### 4. Data Access & Persistence Layer
- ORM & Data Frameworks (Hibernate, Spring Data JPA, MyBatis, Prisma).
- Database Engine(s) (PostgreSQL, Oracle, MongoDB) - note test vs. production dialects.
- Connection Pooling (HikariCP, DBCP2) and transaction management.
- Database Migration Tools (Flyway, Liquibase, Prisma Migrate).

### 5. Security & Compliance
- Authentication & Authorization (Spring Security, OAuth2, JWT, Keycloak, Auth0).
- Secrets Management (HashiCorp Vault, AWS Secrets Manager, `.env` files).
- SAST/DAST & Code Quality (SonarQube, Checkmarx, Dependabot, Trivy configs).

### 6. Observability (Logging, Tracing, Metrics)
- Logging framework (Logback, Log4j2, Winston) and log appenders (Console, File, Logstash).
- Metrics & APM (Micrometer, Prometheus, Datadog, New Relic).
- Distributed Tracing (OpenTelemetry, Zipkin, Jaeger).

### 7. Cloud, CI/CD, & Infrastructure
- CI/CD Pipelines (GitHub Actions, GitLab CI, Jenkinsfile).
- Cloud Native Services (AWS S3, Lambda, Azure Blob, GCP PubSub).
- Infrastructure as Code (Terraform, AWS CDK, CloudFormation).
- Containerization & Orchestration (Dockerfiles, Kubernetes Manifests, Helm Charts).

### 8. Testing Stack
- Testing Frameworks (JUnit 5, TestNG, Jest, PyTest).
- Mocking Libraries (Mockito, WireMock, Testcontainers).
- E2E/UI Testing (Cypress, Playwright, Selenium).

### 9. Third-Party & Internal Dependencies
- List major third-party integrations (e.g., Stripe, Twilio, SendGrid).
- List internal proprietary libraries (e.g., `com.company.shared-auth`).

### 10. Module & Project Structure
- Generate a dependency graph between modules (ASCII diagram).

## 🤖 Strict Output Rules for the AI:
- **No Hallucinations:** If a version or technology is not explicitly found in a configuration file (like `pom.xml` or `package.json`), you MUST write "NOT FOUND". Do not guess.
- **Structured Tables:** Use Markdown tables for libraries: `| Library | Exact Version | Purpose | Scope (Compile/Test) |`
- **Parent BOMs:** If a version is inherited from a parent POM or Spring Boot BOM, write `(Parent-Managed)`.
- **Architecture Diagram:** Include a high-level ASCII architecture diagram at the top showing the full request flow from Frontend -> API -> Service -> Database.
- **Version Mismatches:** Explicitly flag if the `README.md` claims a version (e.g., Java 11) but the build file enforces another (e.g., Java 8).
