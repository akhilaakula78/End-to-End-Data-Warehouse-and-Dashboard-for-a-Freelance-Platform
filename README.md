# End-to-End Data Warehouse & BI Dashboard for a Freelance Platform

This project demonstrates the complete architecture of a modern data warehousing and analytics solution, modeled around a freelance services marketplace (akin to Upwork). It spans the entire data lifecycle—from transactional schema design and dimensional modeling to the creation of a fully interactive QlikView dashboard. By simulating a real-world business use case, this initiative showcases technical depth, tool versatility, and analytical storytelling.

---

## Project Overview

**Objective:**  
To architect a comprehensive data warehouse for a freelance platform that tracks project postings, freelancer bids, client-freelancer interactions, and reviews. The warehouse supports scalable, analysis-ready data for executive dashboards and business insights.

**Tech Stack:**  
- **Data Modeling:** MySQL Workbench  
- **BI & Dashboarding:** QlikView  
- **Data Simulation:** Python (Faker library)  
- **Documentation:** PDF Diagrams & Screenshots  

---

## Phase 1: Transactional System (ER Modeling)

The foundation of the data warehouse begins with designing a normalized transactional database that captures operational data from the freelance platform.

### Core Entities

- **Clients:** Users who post projects and initiate contracts
- **Freelancers:** Professionals who place bids and complete work
- **Projects:** Defined by scope, budget, and timeline
- **Bids:** Freelancers' proposals with cost and time estimates
- **Reviews:** Client feedback post-project completion

Each entity is interconnected with appropriate foreign key relationships to preserve referential integrity. The model was designed in **MySQL Workbench** and populated with mock records using forward engineering.

**Entity Relationship Diagram:** `docs/ERD_Model.pdf`  
**SQL Script & ERD Image:** `er_modeling/`

---

## Phase 2: Analytical System (Dimensional Modeling)

To support OLAP-style queries and dashboard visualizations, the transactional model was transformed into a **star schema**—a best-practice architecture for analytical querying.

### Dimensional Components

- `DimensionClient_AkhilaA`
- `DimensionFreelancer_AkhilaA`
- `DimensionProject_AkhilaA`
- `DimensionTime_AkhilaA`

> Three date-related fields—**Bid Date**, **Proposed Start Date**, and **Proposed End Date**—are derived from the central time dimension using aliases, ensuring consistency and eliminating redundancy.

### Fact Tables

- `FactTransactions_AkhilaA`: Captures freelancer bids, linking all dimensions
- `FactReviews_AkhilaA`: Stores numerical ratings and qualitative feedback

Special care was taken to **eliminate circular references and synthetic keys** through schema normalization and aliasing, enabling optimal performance in QlikView.

**Star Schema Diagram:** `docs/Dimensional_Model.pdf`  
**Design Details:** `dimensional_model/`

---

## Phase 3: Business Intelligence Reporting (QlikView)

The final stage delivers a fully interactive **business intelligence dashboard** in QlikView. It visualizes key metrics and patterns within the freelance ecosystem, enabling stakeholders to make data-driven decisions.

### Dashboard Views

1. **Introduction Sheet:** Project overview and metadata
2. **Client Insights:** Top clients, average review scores, total project spend
3. **Freelancer Insights:** Performance ratings, bid conversion ratios
4. **Project Insights:** Average bid durations, budgets, and approval rates
5. **Dashboard Summary:** Unified KPIs and filters for drill-down analysis

All fields from the star schema were loaded into QlikView via custom scripts. Circular and synthetic keys were resolved through careful data modeling, ensuring clean joins and reliable filters.

**Dashboard Visuals & Model:** `docs/QlikView_Dashboard.pdf`  
**QlikView File & Screenshots:** `bi_dashboard_qlikview/`

---

## Data Simulation (Realism via Faker)

Since this project was not backed by a real production database, a **synthetic dataset** was generated using Python’s `faker` library. The dataset reflects plausible business scenarios, replicating the complexities of an actual freelance platform:

- 50 clients
- 99 freelancers
- 500 projects
- 1,000 transaction records
- 1,000 review entries
- Time dimension covering January to October 2024 (daily granularity)

This artificial yet realistic dataset allowed for meaningful exploratory analysis, while maintaining flexibility and reproducibility.

---

## Key Takeaways

- Translated operational data into analytical formats for executive decision-making
- Modeled clean, scalable schemas in both ER and dimensional forms
- Created a BI dashboard that tells a cohesive, data-driven story
- Simulated production-like datasets without compromising on integrity
- Gained hands-on expertise with MySQL Workbench, QlikView, and schema optimization


