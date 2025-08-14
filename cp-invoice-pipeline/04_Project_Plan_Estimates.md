# Implementation Plan & Effort Estimates

This document provides a conservative, phase-by-phase estimate of the man-hours required to build, test, and deploy the "Document AI First" invoice pipeline into a production environment.

The estimates assume a team with general familiarity with Google Cloud Platform but budget for the learning curve on specific services and for the rigor required to build a production-hardened, secure, and maintainable system.

**Total Estimated Effort**: **402 - 636 hours**
This equates to approximately **10 to 16 person-weeks** for a single engineer.

| Phase / Component | Estimated Hours | Key Activities & Considerations |
| :--- | :--- | :--- |
| **Phase 0: Setup & Configuration** | 48 - 72 hours | - GCP Project setup, VPC configuration, enabling APIs.<br>- Firestore database creation and security rules setup.<br>- Document AI Processor creation and testing.<br>- Source control (Git) repository setup.<br>- Service Account creation with initial IAM roles. |
| **Step 1: Ingestion** | 60 - 90 hours | - Setting up Gmail API push notifications via Pub/Sub.<br>- Writing and testing the Cloud Function to handle Pub/Sub messages, retrieve attachments, and save to GCS/Firestore.<br>- Robust error handling for non-PDF attachments or API failures. |
| **Step 2: Extraction** | 36 - 60 hours | - Writing and testing the Cloud Function triggered by GCS file creation.<br>- Integrating with the Document AI Node.js/Python client library.<br>- Parsing the Document AI JSON response and updating Firestore.<br>- Handling potential Document AI processing errors. |
| **Step 3: Validation** | 48 - 72 hours | - Designing and populating the `canonical_vendors` Firestore collection.<br>- Writing and testing the Firestore-triggered Cloud Function.<br>- Implementing the logic for matching vendor names (may require fuzzy matching for robustness).<br>- Logic to flag invoices for the human review queue. |
| **Step 4: Orchestration** | 72 - 120 hours | - Designing the Cloud Workflow YAML definition.<br>- Implementing workflow steps: file rename/move, BigQuery insertion, ERP API call.<br>- **Note**: ERP integration is the biggest variable. This estimate assumes a well-documented, modern REST API. |
| **Step 5: Exception Handling** | 48 - 72 hours | - Setting up the `human-review-queue` Pub/Sub topic.<br>- Writing the Cloud Function to publish review tasks.<br>- **Note**: This does not include building a custom UI. Assumes notifications are sent to a tool like Slack or email. |
| **Testing & Deployment** | 90 - 150 hours | - Writing unit/integration tests for all Cloud Functions.<br>- End-to-end testing with various real-world invoice examples.<br>- Setting up CI/CD pipelines (e.g., using Cloud Build) for automated deployment.<br>- Final security review and documentation. |
