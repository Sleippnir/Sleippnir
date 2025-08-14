# CV Aligner Pro: AI Persona & Process Architecture

[![Status: Conceptual](https://img.shields.io/badge/status-conceptual-blue)](./)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

This repository contains the complete architectural and operational design for **"CV Aligner Pro,"** a sophisticated AI persona created to bridge the gap between a candidate's experience and the specific requirements of a job description.

This is not a collection of code, but a comprehensive set of design documents that define a system's behavior, constraints, and workflow. The architecture emphasizes an **ethical, transparent, and user-centric approach**, ensuring the final output is both impactful and truthful.

## Core Concepts

The CV Aligner Pro system is built on a foundation of key principles:

-   **Ethical & Truthful by Design:** The system's primary directive is to operate without fabrication. All generated content is based on user-provided information and requires explicit user confirmation, governed by the strict rules in [`Module 6`](./Module%206_CV%20Aligner%20Pro%20-%20Operational%20%26%20Ethical%20Guardrails.md).
-   **Recruiter-Centric Approach:** The process is informed by real-world recruiter practices, as defined in [`Module 1`](.Module%201_%20The%20Recruiter_s%20Lens%20-%20Core%20Evaluation%20Principles.md), focusing on impact, quantification, and scannability to pass the "6-second scan."
-   **Modular & Repeatable Process:** The workflow is broken down into distinct, sequential modules, ensuring a logical, consistent, and auditable process from initial analysis to final output.
-   **Transparency & Collaboration:** The [`Visual Mapping Tool`](./Module%202a_Visual%20Mapping%20Tool%20-%20Presentation%20%26%20Initial%20Confirmation.md) (`Module 2a`) serves as a central point for collaboration, allowing the user to see and confirm the AI's alignment analysis before proceeding.

## System Architecture

The design specifies a dual-persona system to separate concerns, ensuring a clean division between content strategy and final presentation.

1.  **[`CV Aligner Pro`](./Persona%20Definition_%20CV%20Aligner%20Pro%201.3.md)**
    The core "brain" of the operation. This persona is responsible for analyzing, interacting, crafting content, and performing quality assurance according to the defined process modules.

2.  **[`CV Formatter`](./Persona%20Definition_%20CV%20Formatter%20%28v1.1%20-%20LaTeX%20Aware%29.md)**
    A specialized, operational persona responsible for layout and presentation. It takes the structured content from the Aligner Pro and produces the final, polished document.

## Process Workflow

The system operates in a clear, step-by-step sequence defined by the modules. Each module has a specific purpose and builds upon the last.

| Module                                                                                                   | Purpose                                                                           |
| :------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------- |
| **[`Module 0`](./Module%200_Foundational%20Context%20%26%20Purpose.md)**                                     | **Foundational Context:** Establishes the project's goal and success metrics.       |
| **[`Module 1`](./Module%201_The%20Recruiter_s%20Lens%20-%20Core%20Evaluation%20Principles.md)**            | **The Recruiter's Lens:** Defines the core evaluation principles (STAR, quantification). |
| **[`Module 2`](./Module%202_Strategic%20CV%20Deconstruction%20%26%20JD%20Analysis.md)**                     | **JD & CV Deconstruction:** The AI performs its initial analysis of all inputs.     |
| **[`Module 2a`](./Module%202a_Visual%20Mapping%20Tool%20-%20Presentation%20%26%20Initial%20Confirmation.md)** | **Visual Mapping Tool:** Presents the analysis to the user for confirmation.       |
| **[`Module 3`](./Module%203_Eliciting%20Excellence%20-%20Hypothesis-Driven%20%26%20Map-Guided%20User%20Interaction.md)** | **Eliciting Excellence:** The AI intelligently questions the user to fill gaps.     |
| **[`Module 4`](./Module%204_Content%20Alchemy%20-%20Transforming%20Confirmed%20Information%20into%20Tier-Aware%20Impact.md)** | **Content Alchemy:** Transforms the confirmed facts into impactful CV statements.    |
| **[`Module 5`](./Module%205_Quality%20Assurance%20%26%20Final%20Polish.md)**                                 | **Quality Assurance:** A final internal review for consistency, alignment, and polish. |
| **[`Module 6`](./Module%206_CV%20Aligner%20Pro%20-%20Operational%20%26%20Ethical%20Guardrails.md)**           | **Ethical Guardrails:** The non-negotiable rules that govern every step of the process. |

## Project Contents

-   [`Persona Definition_ CV Aligner Pro 1.3.md`](./Persona%20Definition_%20CV%20Aligner%20Pro%201.3.md)
-   [`Persona Definition_ CV Formatter (v1.1 - LaTeX Aware).md`](./Persona%20Definition_%20CV%20Formatter%20%28v1.1%20-%20LaTeX%20Aware%29.md)
-   [`Module 0_Foundational Context & Purpose.md`](./Module%200_Foundational%20Context%20%26%20Purpose.md)
-   [`Module 1_The Recruiter_s Lens - Core Evaluation Principles.md`](./Module%201_The%20Recruiter_s%20Lens%20-%20Core%20Evaluation%20Principles.md)
-   [`Module 2_Strategic CV Deconstruction & JD Analysis.md`](./Module%202_Strategic%20CV%20Deconstruction%20%26%20JD%20Analysis.md)
-   [`Module 2a_Visual Mapping Tool - Presentation & Initial Confirmation.md`](./Module%202a_Visual%20Mapping%20Tool%20-%20Presentation%20%26%20Initial%20Confirmation.md)
-   [`Module 3_Eliciting Excellence - Hypothesis-Driven & Map-Guided User Interaction.md`](./Module%203_Eliciting%20Excellence%20-%20Hypothesis-Driven%20%26%20Map-Guided%20User%20Interaction.md)
-   [`Module 4_Content Alchemy - Transforming Confirmed Information into Tier-Aware Impact.md`](./Module%204_Content%20Alchemy%20-%20Transforming%20Confirmed%20Information%20into%20Tier-Aware%20Impact.md)
-   [`Module 5_Quality Assurance & Final Polish.md`](./Module%205_Quality%20Assurance%20%26%20Final%20Polish.md)
-   [`Module 6_CV Aligner Pro - Operational & Ethical Guardrails.md`](./Module%206_CV%20Aligner%20Pro%20-%20Operational%20%26%20Ethical%20Guardrails.md)
