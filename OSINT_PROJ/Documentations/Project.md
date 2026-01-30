**End-of-Studies Internship — Project Plan**

**Project Title:** OSINT Leak Detection and Intelligence Web Platform  
**Intern:** [Your Name]  
**Supervisor:** [Supervisor Name]  
**Duration:** 6 months

---

## 1️⃣ Project Objectives

Develop a web-based OSINT platform capable of detecting, collecting, analyzing, and reporting publicly available leaked data related to a specific target (domain, email patterns, projects).  

Key objectives:
- Monitor public sources (Telegram, paste platforms, GitHub public repos).
- Parse, normalize, and correlate extracted data with the user’s target profile.
- Assess exposure risk and prioritize findings.
- Provide a web interface showing dashboards, findings, and reports (PDF/JSON).
- Ensure confidentiality: each enterprise user sees only leaks related to their profile.
- Allow public/basic users to query general leaks by email or password without creating an account.

---

## 2️⃣ User Types & Profiles

| User Type | Access Level | Functionality |
|-----------|-------------|---------------|
| Public / Basic | No authentication | - View home page with statistics (total leaks collected, sources)
- Query leaks by email or password only
- No target profile creation |
| Enterprise | Authenticated | - Account creation (input domain, email pattern, keywords)
- Single target profile automatically associated
- Run on-demand scan for their domain/projects
- View findings & dashboards filtered for their profile
- Generate PDF/JSON reports
- Chatbot access (future) |

**Key design principle:** Each enterprise user is associated with one target profile, ensuring data isolation and confidentiality.

---

## 3️⃣ Project Scope

### In-Scope
- OSINT sources: Telegram public channels, Paste platforms, GitHub public repos.
- Data types: emails, passwords (masked), API keys, document names, domain-related info.
- Enterprise features: target profile creation, findings dashboard, risk scoring, report generation.
- Public features: home page with statistics, search leaks by email/password.
- Backend: Python (FastAPI/Flask).
- Database: PostgreSQL.
- Frontend: React.js / Vue.js, interactive dashboards.
- Authentication: login, email verification, password reset.

### Out-of-Scope
- Dark web/private paid forums
- Exploiting leaks / validating credentials
- Multi-target profiles per enterprise
- Real-time attack prevention or SOC-style alerts
- Storing full leaked datasets

---

## 4️⃣ Methodology

1. Requirement Analysis & Design – Define user types, tech stack, DB schema, target profile logic.
2. Backend Development – Collectors, parsing, normalization, correlation, risk scoring, report generation.
3. Database Setup – Structured tables, indexing, search, single-target per enterprise user.
4. Frontend Development – Public home page, enterprise login, dashboards, findings, reports.
5. Integration & Testing – Backend ↔ frontend, continuous collection, deduplication, risk scoring.
6. Documentation & Reporting – Methodology, limitations, ethical considerations, final presentation.

---

## 5️⃣ Project Milestones & Timeline

| Month | Milestone | Tasks | Deliverables |
|-------|-----------|-------|-------------|
| 1 | Research & Design | - Define project scope and user types
- Identify sources, data types
- Select tech stack
- Draft architecture including single target per enterprise user | Scope doc, user type definitions, architecture diagram |
| 2 | Database & Backend Setup | - Install PostgreSQL
- Design schema for single target per enterprise
- Implement CRUD API endpoints
- Indexing & full-text search
- Setup users table with authentication | Functional database, API endpoints, test entries |
| 3 | Data Collection Pipeline | - Implement Telegram, Paste, GitHub collectors
- Continuous monitoring pipeline (cron / Celery)
- Logging & error handling
- Store findings in DB | Collector scripts, continuous pipeline, DB updates |
| 4 | Parsing & Normalization | - Extract entities from raw findings
- Deduplicate & normalize
- Classify data (credentials, API keys, documents)
- Prepare for correlation | Structured, deduplicated DB data ready for analysis |
| 5 | Correlation & Frontend Development | - Correlate findings with enterprise target
- Exposure clustering
- Risk scoring (Low/Medium/High)
- Frontend: Public home page with statistics; Enterprise login/account creation; Single target dashboard; Findings display & filters; PDF/JSON report generation | Functional web app for public & enterprise users, correlated data, dashboards, reports |
| 6 | Testing & Documentation | - Unit & integration testing
- False positive analysis
- Generate sample reports
- Document methodology, limitations, ethical considerations
- Prepare presentation/demo | Tested OSINT platform, final documentation, sample reports, demo |

---

## 6️⃣ Technical Stack

| Layer | Technology |
|-------|------------|
| Backend | Python (FastAPI / Flask), Celery / cron scheduler |
| Database | PostgreSQL (structured, indexed) |
| Frontend | React.js or Vue.js, Chart.js / Recharts for dashboards |
| Data Collection | Telethon (Telegram), BeautifulSoup/requests (Paste platforms), GitHub API |
| Reporting | PDF: ReportLab / WeasyPrint, JSON export |
| Authentication | Email verification, password reset, JWT sessions |
| Deployment | Local VM / Dockerized environment |

---

## 7️⃣ Database Design (Key Tables)

- `users` — enterprise users, single target profile association
- `targets` — domain, email pattern, keywords
- `sources` — OSINT sources
- `raw_findings` — raw snippets with metadata
- `entities` — normalized extracted data
- `asset_matches` — correlated findings per target
- `exposure_clusters` — group related leaks
- `risk_assessments` — risk scoring per cluster
- `reports` — generated PDF/JSON reports

**Note:** Public/basic users do not create targets; they query generic leaks by email/password only.

---

## 8️⃣ Deliverables

- Web app with public & enterprise modes
- Backend continuous OSINT monitoring pipeline
- Normalized database storing findings correlated to enterprise target
- Dashboards and analytics for each enterprise user
- Report generation (PDF / JSON)
- Documentation and final presentation

---

## 9️⃣ Ethical & Legal Considerations

- Only publicly available sources are monitored.
- Each enterprise user sees only their target’s data.
- Sensitive data is masked/redacted.
- Reports provide intelligence, not instructions for exploitation.
- DB access and internal logs are secured.

