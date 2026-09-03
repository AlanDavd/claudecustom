> Generate a complete architecture.md for this codebase

-------

Analyze this codebase and generate a comprengensive ARCHITECTURE.md file. Structure the documents with these exact sections.

1. PROJECT STRUCTURE
Include a complete directory tree diagram showing all folders and files. Group by architectural layer or feature.

2. HIGH-LEVEL SYSTEM DIAGRAM
Provide a C4 model Level 1 diagram or text-based block diagram showing: Users -> Frontend -> Backend -> Database and any external services/APIS.

3. CORE COMPONENTS
For each major component (Frontend, Backend Services, Microservices): describe purpose, technologies used, and deployment method.

4. DATA STORES
List all databases, caches, and message queues.
For each: type (PostgreSQL, MongoDB, Redis, S3) purpose, and key schemas/collections.

5. EXTERNAL INTEGRATIONS
Every third-party API or service (Stripe, SendGrid, Firebase, etc). Include purpose and integration method.

6. DEPLOYMENT & INFRASTRUCTURE
Cloud provider, key services (EC2, Lambda, S3, RDS, Kubernetes), CI/CD pipeline, and monitoring tools.

7. SECURITY CONSIDERATIONS
Auth method (OAuth2, JWT, API Keys), autorization model, data encryption (TLS, at-rest), and security tools.

8. DEVELOPMENT & TESTING
Local setup instructions, testing frameworks, and code quality tools.

9. FUTURE CONSIDERATIONS
Known technical debt, planned migrations, and major features on the roadmap.

10. GLOSSARY
Define all project-specific acronyms and terms.

11. PROJECT IDENTIFICATION
Project name, repository URL, primary contact/team, and date of last update.
