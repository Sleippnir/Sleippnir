# Data Security & Confidentiality Analysis

Handling sensitive financial documents requires a robust, multi-layered security strategy. This document outlines the security controls implemented within the Google Cloud Platform (GCP) environment to protect the invoice data throughout its lifecycle.

### A. Data at Rest
-   **Concern**: How are invoice PDFs and extracted financial data protected while being stored?
-   **GCP Solution & Actions**:
    -   **Default Encryption**: All data stored in Cloud Storage, Firestore, and BigQuery is automatically encrypted at rest by Google, with no action required.
    -   **Enhanced Control (CMEK)**: For heightened compliance requirements, Customer-Managed Encryption Keys (CMEK) can be configured, giving our organization full control over the keys used to encrypt data.
    -   **Firestore Security Rules**: The databases are locked down with specific security rules that deny all access by default and only grant read/write permissions to the specific service accounts used by the pipeline's Cloud Functions.

### B. Data in Transit
-   **Concern**: How is data protected as it moves between services (e.g., from Cloud Functions to Document AI)?
-   **GCP Solution & Actions**:
    -   **TLS Encryption**: All API calls and data transfers between Google Cloud services are automatically encrypted in transit using TLS.
    -   **VPC Service Controls**: A VPC Service Controls perimeter is established to create a virtual security boundary around the project's services. This prevents data from being moved outside the authorized network (data exfiltration), even by a credentialed user or service.

### C. Access Control & Identity (IAM)
-   **Concern**: How do we ensure only authorized services and personnel can access or modify the pipeline?
-   **GCP Solution & Actions**:
    -   **Principle of Least Privilege**: Each component of the pipeline (e.g., the ingestion function, the extraction function) operates using a dedicated, single-purpose service account. These accounts are granted only the minimal IAM roles necessary to perform their specific task. For example, the ingestion function only has permission to write to the `raw-invoices` bucket, not read from it or access any other part of the system.
    -   **IAM Conditions**: Access is further restricted using IAM Conditions, which allow for granular, resource-specific policies (e.g., allowing a service account to *only* access files with a specific prefix).
    -   **Human Access**: Direct human access to the production environment is heavily restricted, logged, and audited. All deployments and changes are managed through an automated CI/CD pipeline.

### D. Audit & Monitoring
-   **Concern**: How do we track all actions taken within the pipeline for auditing and security analysis?
-   **GCP Solution & Actions**:
    -   **End-to-End Logging**: Every step, from email receipt to final payment processing, is logged in Firestore, creating a clear, application-level audit trail for every single invoice.
    -   **Cloud Audit Logs**: Google Cloud's detailed audit logs are enabled for all services, capturing all administrative access and data access events.
    -   **Automated Alerting**: Alerts are configured in Cloud Logging to automatically notify the security team of any suspicious or anomalous activity, such as an attempt to access data from an unauthorized location or by an unauthorized principal.
