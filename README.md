# Academic Portal & Query Optimization Experiments  
**CS 301 – Introduction to Database Systems**  
**Course Project (Phases A & B)**  

---

## 📖 Overview  
This repository contains a multi‐user academic portal implemented entirely within PostgreSQL (Phase A) and a large‐scale data generation & query‐optimizer experiment suite (Phase B). The portal manages students, faculty, course offerings, registrations, tickets, grade uploads, and transcript/report generation via stored procedures, triggers, constraints, and role‐based privileges. Phase B scripts generate millions of synthetic tuples for movie–actor–company datasets and run `EXPLAIN ANALYZE` experiments to study index usage, selectivity, and join strategies.

---

## 🔑 Key Features  

### Phase A: Academic Portal  
- **Schema Design**  
  - `CourseCatalogue`, `CourseOffering`, `Student`, `Faculty`, `BatchAdvisor`, `DeanOffice`, `Registration`, `TicketHistory`, `Grades` tables  
- **Constraints & Triggers**  
  - No time‐slot clashes, pre‐req checks, credit‐limit enforcement  
  - Privilege enforcement: only Dean can edit catalogue; students see only their grades  
- **Stored Procedures**  
  - Upload time‐table slots, offer courses, register courses, raise/propagate tickets  
  - Generate transcripts, compute CGPA, import grades from CSV  
- **Role‐Based Access Control**  
  - `GRANT`/`REVOKE` to assign minimal privileges per role  

### Phase B: Data Generation & Query Experiments  
- **Synthetic Dataset Generation**  
  - `actor` (300 000 rows), `production_company` (80 000 rows),  
  - `movie` (1 000 000 rows), `casting` (4 million rows)  
  - Parameterized distributions based on team roll numbers & size :contentReference[oaicite:2]{index=2}  
- **Index Creation**  
  - B‑tree indexes on `(a_id)`, `(m_id)`, `(imdb_score)`, `(year)`, `(pc_id)` in respective tables  
- **Experiments (Phase B‑A & B‑B)**  
  - **Selectivity Tests:** six range queries on `imdb_score`, `year`, `pc_id` with `EXPLAIN ANALYZE`  
  - **Join Strategy Tests:** four join queries involving `Actor`, `Movie`, `Casting`, `ProductionCompany`  
  - Automated scripts to collect & summarize optimizer plans  

---
