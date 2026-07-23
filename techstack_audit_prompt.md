# Reusable Prompt: Full Front-to-Back Tech Stack Audit

**Usage:** Paste this prompt into any AI session (Copilot, Claude, etc.) with a new repository open.
Adjust section headers if the project isn't Java (e.g., swap "Servlet container" for "Node.js runtime" for a JS project).

***

You are a Principal Enterprise Architect performing a full front-to-back technology stack audit of this repository. Do NOT modify any code - strictly read, explore, and document.

Systematically explore every layer of the codebase and produce a single `techstack.md` file with the following sections:

## What to investigate per layer:

### 1. Frontend
- View technology (JSP, Thymeleaf, React, Angular, etc.) with versions
- JavaScript libraries and frameworks with exact versions (check vendored files, package.json, CDN references)
- CSS frameworks/preprocessors
- Template engines (Tiles, Handlebars, doT.js, etc.)
- Taglibs or component libraries
- Frontend build tools (webpack, Vite, gulp, grunt, npm scripts - or "None/vendored")

### 2. Web / Middleware Layer
- Servlet container or application server (with version)
- web.xml: list ALL servlets, filters, listeners with class names and URL patterns
- MVC framework config (Spring MVC, JAX-RS, etc.) - component scan, interceptors, view resolvers, message converters
- REST/SOAP endpoints - list each with URL pattern and technology (CXF, Jersey, Spring WebFlux, etc.)

### 3. Service / Business Logic Layer
- Framework modules used (list each Spring module, Jakarta EE spec, etc.)
- Batch processing framework (Spring Batch, Quartz, custom)
- Scheduling (cron triggers, @Scheduled, timer services)
- Caching strategy (EhCache, Redis, Hazelcast, Caffeine - config files and cache names)
- Messaging (JMS, Kafka, RabbitMQ, SQS - connection factories, topics/queues)
- Validation framework (JSR-303, custom)
- Feature toggles / configuration management

### 4. Data Access Layer
- ORM (Hibernate version, JPA version, MyBatis, JDBC templates, custom SQL builders)
- Database engine(s) - production AND test (with JDBC driver versions)
- Connection pooling (HikariCP, DBCP2, c3p0 - pool sizes)
- Transaction management strategy
- Database migration tool (Flyway, Liquibase, manual scripts, or none)
- Key schema objects / table prefixes

### 5. Security
- Authentication mechanism (per environment if different: dev vs prod)
- Authorization model (roles, access rules, voters)
- Password encoding
- SSL/TLS configuration (keystores, truststores, cipher suites)
- CSRF/CORS/X-Frame-Options settings
- Security framework (Spring Security, Shiro, JAAS, custom)

### 6. Logging & Monitoring
- Logging framework + config files
- Log appenders (file, console, remote)
- Health/status endpoints
- Metrics/APM (Micrometer, Prometheus, Datadog, custom)

### 7. Build, CI/CD & Deployment
- Build tool with version constraints (Maven, Gradle, npm, etc.)
- List key build plugins and their purpose
- CI/CD pipeline technology (GitHub Actions, GitLab CI, Jenkins, etc.)
- Deployment target (Docker, Kubernetes, cloud PaaS, bare metal, WAR on app server)
- Environment list (dev, staging, prod, DR)
- Secrets management (Vault, AWS Secrets Manager, env vars)

### 8. Testing Stack
- Test frameworks with versions (JUnit 4/5, TestNG, Jest, Mocha)
- Mocking libraries (Mockito, WireMock, MockServer)
- Integration test frameworks (Testcontainers, Arquillian, Spring Test)
- UI/E2E test tools (Selenium, Cypress, Playwright, PhantomJS)
- Architecture test tools (ArchUnit, Deptective)
- Test database strategy
- Total test count by category (unit vs integration)

### 9. Internationalization
- i18n approach (resource bundles, i18next, ICU, etc.)
- Supported languages

### 10. Internal / Platform Dependencies
- List ALL internal/proprietary libraries with versions and purpose

### 11. Third-Party Dependencies (Key)
- List major third-party libraries with versions

### 12. Module / Project Structure
- Dependency graph between modules (ASCII diagram)

## Output rules:
- Use tables for structured data (library | version | purpose)
- Include an ASCII architecture diagram at the top showing the full request flow
- Report exact versions - do NOT say "latest" or "unknown" without checking
- If a version is managed by a parent POM or BOM, say "(parent-managed)"
- Distinguish between compile, runtime, and test scope dependencies
- Note any version mismatches (e.g., README says X but config says Y)
