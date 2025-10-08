# SPVS Column Definitions

This document defines each column in the OWASP Software Pipeline Verification Standard (SPVS) dataset.  
Use these definitions when editing the spreadsheet, exporting to CSV or JSON, or building automation.

---

## Valid Categories and Sub-categories

**Categories (Category_ID and catagory_name):**
- **V1 / Plan**
- **V2 / Develop**
- **V3 / Integrate (CI*)**
- **V4 / Release (CD*)**
- **V5 / Operate**

**Sub-categories (by category, used in sub-category_id and sub-catagory_name):**

- **Plan (V1)**
  - V1.1 Identity and Access Management
  - V1.2 Hardening User Machines
  - V1.3 Security Requirements and Risk Assessment
  - V1.4 Developer Tool Operation
  - V1.5 Source Code Management Hardening

- **Develop (V2)**
  - V2.1 Secure Coding Practices
  - V2.2 Software Quality
  - V2.3 Code Review and Analysis
  - V2.4 Perform Security Checks
  - V2.5 Credential Hygiene
  - V2.6 3rd Party library Audit
  - V2.7 Unit Testing

- **Integrate (CI*) (V3)**
  - V3.1 Security of Pipeline Environment
  - V3.2 Credential Hygiene
  - V3.3 Continuous Security Checks
  - V3.4 Integrity of Artifacts

- **Release (CD*) (V4)**
  - V4.1 Final Security Assessments
  - V4.2 Compliance Checks
  - V4.3 Secure Deployment Practices

- **Operate (V5)**
  - V5.1 Access Audit
  - V5.2 Security Standard Enforcement
  - V5.3 Secure Maintenance Practices
  - V5.4 Detection & Monitoring
  - V5.5 Incident Response & Recovery

> Note: Sub-category numbering reflects the current draft and may evolve as SPVS is refined.

---

## Column Descriptions

| Column Name | Description |
|---|---|
| **Category_ID** | Unique identifier of the top-level SPVS category. Valid values are V1, V2, V3, V4, V5. See the list above for the corresponding names. |
| **catagory_name** | Human readable name of the category that pairs with Category_ID. Valid values are Plan, Develop, Integrate (CI*), Release (CD*), Operate. |
| **sub-category_id** | Identifier of the sub-category within the category. Format is V#.## where the first number matches Category_ID. See the lists above for valid values. |
| **sub-catagory_name** | Human readable name of the sub-category that pairs with sub-category_id. Use the names listed above for each category. |
| **req_id** | Unique requirement identifier under a given sub-category. Format is V#.#.# for example V1.2.3. This provides traceability across documents and versions. |
| **req_name** | Short title of the verification requirement. Keep it concise and specific so it is usable in reports and dashboards. |
| **req_description** | Complete statement of the verification requirement. Write it as an objective condition that can be tested. |
| **level 1** | Marks whether the requirement applies at SPVS Level 1. Use an X when in scope, otherwise leave blank. |
| **level 2** | Marks whether the requirement applies at SPVS Level 2. Use an X when in scope, otherwise leave blank. |
| **level 3** | Marks whether the requirement applies at SPVS Level 3. Use an X when in scope, otherwise leave blank. |
| **NIST** | One or more NIST SP 800-53 control identifiers that map to the requirement. Use standard identifiers such as AC-2, IA-5, SI-2. Separate multiple values with commas. |
| **OWASP_CICD_Risk** | One or more OWASP CI/CD Security Top 10 risk identifiers relevant to the requirement. Use the project notation such as CICD-SEC-1. |
| **cwe_mapping** | One or more CWE identifiers associated with the requirement. Use canonical CWE identifiers such as CWE-287 or CWE-798. |
| **cwe_description** | Short description of the CWE mapping to clarify the associated weakness category. Keep this aligned with the CWE entry title. |

---

## Conventions

- Category and sub-category fields must use one of the valid values listed above.  
- Each req_id belongs to exactly one category and one sub-category.  
- Levels are cumulative. Higher levels include all controls from lower levels unless explicitly scoped otherwise.  
- Use consistent separators for multi-value fields. Commas are preferred.  
- Keep naming stable to preserve traceability across versions.
