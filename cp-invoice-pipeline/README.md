# Automated Invoice Processing Pipeline (GCP & Document AI)

## 1. Executive Summary

This project showcases the end-to-end design and implementation plan for a serverless, event-driven invoice processing pipeline on Google Cloud Platform (GCP). The solution was architected to solve a critical business problem: the time-consuming, error-prone, and costly manual processing of vendor invoices.

By leveraging **Google Document AI** at the core, the system automates the entire lifecycle from ingestion via email to data extraction, validation, and final routing to ERP and analytics systems. This approach eliminates manual data entry, dramatically reduces payment cycle times, and creates a fully auditable, searchable digital archive of all invoices.

-   **Business Problem**: Manual invoice processing was slow, expensive, and error-prone, leading to delayed payments and a lack of real-time financial data.
-   **My Solution**: An automated, "Document AI First" serverless pipeline on GCP that ingests, interprets, validates, and routes invoice data with minimal human intervention.
-   **Core Impact**: The system was projected to reduce monthly processing effort by **~95%** (from 333 hours to 17 hours) and establish a 90% straight-through processing rate, freeing up significant resources and enabling strategic financial benefits[cite: 265, 267].

---

## 2. Key Outcomes & Business Value (Conservative Projections)

The following metrics were established to measure the success and return on investment for this initiative.

| Category | KPI | Target Goal |
| :--- | :--- | :--- |
| **Efficiency** | Man-Hours Saved per Month | **~316 hours** (a 95% reduction)  |
| **Efficiency** | Average Processing Time | **< 1 hour** (from email receipt to ERP entry)  |
| **Accuracy** | Straight-Through Processing (STP) Rate | **> 90%** (zero human intervention)  |
| **Business Value** | Data Availability for Analytics | **< 2 hours** (for real-time spend analysis)  |
| **Scalability** | Cost Avoidance | Scales to handle 2-3x volume with negligible cost increase, avoiding future headcount. |

---

## 3. Technical Architecture Overview

The system is designed as a modular, event-driven pipeline using managed GCP services to ensure scalability, resilience, and low operational overhead.

![Data Flow Diagram](https://mermaid.ink/svg/eyJjb2RlIjoiZ3JhcGggVERcbiAgICBBW0VtYWlsIEluYm94XSAtLT58MS4gSW5nZXN0aW9ufCBCKENsb3VkIFN0b3JhZ2U6IHJhd19pbnZvaWNlcyk7XG4gICAgQiAtLT58Mi4gRXh0cmFjdGlvbnwgQyhEb2N1bWVudCBBSSk7XG4gICAgQyAtLT58RGF0YSBFeHRyYWN0ZWR8IEQoRmlyZXN0b3JlKTtcbiAgICBEIC0tPnwzLiBWYWxpZGF0aW9ufCBEO1xuICAgIEQgLS0-fDQgT3JjaGVzdHJhdGlvbnwgRShDbG91ZCBXb3JrZmxvd3MpO1xuICAgIEUgLS0-IEYoQmlnUXVlcnk6IEFuYWx5dGljcyk7XG4gICAgRSAtLT4gRyhFUlAgU3lzdGVtOiBQYXltZW50KTtcbiAgICBFIC0tPiBIKENsb3VkIFN0b3JhZ2U6IEFyY2hpdmUpO1xuICAgIERbVmFsaWRhdGlvbiBGYWlsdXJlXSAtLT58NS4gRXhjZXB0aW9ufCBJKFB1Yi9TdWIsIEh1bWFuIFJldmlldyk7XG5cbiAgICBzdHlsZSBDIHフィルlDojZDNlYWZkLGstrokeOiMzMzMsZmlsbDpibGFjayxzdHJva2Utd2lkdGg6MnB4O1xuICAgIHN0eWxlIEUgZmlsbDojZDNlYWZkLHN0cm9rZTojMzMzLGZpbGw6YmxhY2ssc3Ryb2tlLXdpZHRoOjJweDsiLCJtZXJtYWlkIjp7InRoZW1lIjoiZGVmYXVsdCJ9LCJ1cGRhdGVFZGl0b3IiOmZhbHNlfQ)

**Core Pipeline Stages:**
1.  **Ingestion**: A Cloud Function, triggered by Pub/Sub notifications from Gmail, saves invoice PDF attachments to a raw Cloud Storage bucket[cite: 52, 53, 54, 55].
2.  **Extraction**: Document AI's Invoice Processor automatically reads the PDF and extracts key-value pairs (Vendor, Invoice ID, Totals, Line Items) into a structured format.
3.  **Validation & Enrichment**: The extracted vendor name is cross-referenced against an approved vendor list in Firestore to append an internal ERP ID.
4.  **Orchestration & Routing**: A Cloud Workflow orchestrates the final steps: renaming and archiving the PDF, and sending structured data to BigQuery for analytics and the ERP system for payment.
5.  **Exception Handling**: Invoices that fail validation (e.g., a new, unrecognized vendor) are automatically routed to a human review queue, creating a self-improving feedback loop.

---

## 4. Skills & Competencies Demonstrated

This project showcases a blend of technical architecture, program management, and business acumen.

-   **Solutions Architecture**: Designing a robust, scalable, and cost-effective serverless architecture on GCP.
-   **AI Adoption**: Integrating a powerful AI service (Document AI) to solve a core business problem and drive automation.
-   **Technical Program Management**: Defining project scope, estimating effort, planning implementation phases, and identifying risks.
-   **Data Strategy & Security**: Establishing a secure data flow with clear audit trails, from ingestion to analytics and archival.
-   **ROI & Business Case Development**: Translating a technical solution into a clear business case with conservative ROI projections and success-oriented KPIs.
-   **Stakeholder Alignment**: Creating documentation that speaks to both technical teams (architecture diagrams) and leadership (executive summary, ROI).

---

## 5. Project Artifacts

For a deeper dive into the project's planning and design, please review the detailed artifacts below.

-   **[📄 01_Executive_Briefing_ROI.md](./01_Executive_Briefing_ROI.md)**: The business case, problem statement, projected ROI, and Key Performance Indicators (KPIs).
-   **[📄 02_Technical_Architecture.md](./02_Technical_Architecture.md)**: A detailed breakdown of the technical components, data flow, and step-by-step implementation logic.
-   **[📄 03_Security_Compliance.md](./03_Security_Compliance.md)**: The data security, confidentiality, and compliance analysis for the pipeline.
-   **[📄 04_Project_Plan_Estimates.md](./04_Project_Plan_Estimates.md)**: The phase-by-phase project implementation plan and conservative man-hour estimates.
-   **[📂 src-examples/](./src-examples/)**: A collection of non-proprietary code snippets and configuration examples.
