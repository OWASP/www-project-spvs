# Secure Pipeline Verification Standard (SPVS) Categories Overview

This document outlines the stages and subcategories of the Secure Pipeline Verification Standard (SPVS), designed to integrate security throughout the software development lifecycle.

---

## Column Descriptions

| Column Name | Description |
|---|---|
| **Category_ID** | Unique identifier of the top-level SPVS category. Valid values are V1, V2, V3, V4, V5. See the list above for the corresponding names. |
| **catagory_name** | Human readable name of the category that pairs with Category_ID. Valid values are Plan, Develop, Integrate, Release, Operate. |
| **sub-category_id** | Identifier of the sub-category within the category. Format is V#.## where the first number matches Category_ID. See the lists above for valid values. |
| **sub-catagory_name** | Human readable name of the sub-category that pairs with sub-category_id. Use the names listed above for each category. |
| **req_id** | Unique requirement identifier under a given sub-category. Format is V#.#.# for example V1.2.3. This provides traceability across documents and versions. |
| **req_name** | Short title of the verification requirement. Keep it concise and specific so it is usable in reports and dashboards. |
| **req_description** | Complete statement of the verification requirement. Write it as an objective condition that can be tested. |
| **level 1** | Marks whether the requirement applies at SPVS Level 1 – Foundational. |
| **level 2** | Marks whether the requirement applies at SPVS Level 2 – Standard. |
| **level 3** | Marks whether the requirement applies at SPVS Level 3 – Advanced. |
| **NIST** | One or more NIST SP 800-53 control identifiers that map to the requirement. Use standard identifiers such as AC-2, IA-5, SI-2. Separate multiple values with commas. |
| **OWASP_CICD_Risk** | One or more OWASP CI/CD Security Top 10 risk identifiers relevant to the requirement. Use the project notation such as CICD-SEC-1. |
| **cwe_mapping** | One or more CWE identifiers associated with the requirement. Use canonical CWE identifiers such as CWE-287 or CWE-798. |
| **cwe_description** | Short description of the CWE mapping to clarify the associated weakness category. Keep this aligned with the CWE entry title. |

### Conventions

- Category and sub-category fields must use one of the valid values listed above.  
- Each req_id belongs to exactly one category and one sub-category.  
- Levels are cumulative. Higher levels include all controls from lower levels unless explicitly scoped otherwise.  
- Use consistent separators for multi-value fields. Commas are preferred.  
- Keep naming stable to preserve traceability across versions.

---

## **Categories (Category_ID and Category_Name)**

* **V1 / Plan**
* **V2 / Develop**
* **V3 / Integrate**
* **V4 / Release**
* **V5 / Operate**

---

## **Sub-Categories (by category, used in Sub-Category_ID and Sub-Category_Name)**

### **Plan (V1)**

* V1.1 Identity and Access Management
* V1.2 Hardening User Machines
* V1.3 Security Requirements and Risk Assessment
* V1.4 Developer Tool Operation
* V1.5 Source Code Management Hardening

### **Develop (V2)**

* V2.1 Secure Coding Practices
* V2.2 Software Quality
* V2.3 Code Review and Analysis
* V2.4 Perform Security Checks
* V2.5 Credential Hygiene
* V2.6 3rd Party Library Audit
* V2.7 Unit Testing

### **Integrate (V3)**

* V3.1 Security of Pipeline Environment
* V3.2 Credential Hygiene
* V3.3 Continuous Security Checks
* V3.4 Integrity of Artifacts

### **Release (V4)**

* V4.1 Final Security Assessments
* V4.2 Compliance Checks
* V4.3 Secure Deployment Practices
* V4.4 Transition Security

### **Operate (V5)**

* V5.1 Access Audit
* V5.2 Security Standard Enforcement
* V5.3 Secure Maintenance Practices
* V5.4 Detection & Monitoring
* V5.5 Incident Response & Recovery

---

# **Category Details**

---

## **V1 – Plan**

> This stage focuses on defining the scope, objectives, and security requirements for the upcoming iteration. It includes assessing potential risks, establishing security baselines, and aligning plans with business goals and compliance needs.
>
> In line with SPVS principles, planning is not a one-time activity — it incorporates feedback loops, postmortems, threat modeling, and lessons learned from previous iterations, incidents, or audits. This ensures continuous improvement in both product quality and security posture over time.

### **Sub-Categories**

#### **V1.1 Identity and Access Management**

Plan and govern access control policies for development and administrative roles. Ensure identity federation, least privilege, and periodic access reviews are in place to protect sensitive systems from unauthorized access during all stages of development.

#### **V1.2 Hardening User Machines**

Apply security controls to developer and administrative workstations to reduce the attack surface. This includes OS hardening, secure configurations, endpoint protection, and enforcement of minimum security baselines for all user-accessible systems involved in the development lifecycle.

#### **V1.3 Security Requirements and Risk Assessment**

Identify and document security requirements alongside functional requirements. Perform risk assessments and threat modeling to anticipate potential vulnerabilities, drive architectural decisions, and prioritize mitigations based on impact.

#### **V1.4 Developer Tool Operation**

Establish policies for approved development tools, plugins, and IDE configurations to prevent the use of insecure or unvetted software. Enforce secure defaults and define usage standards that align with organizational security policies.

#### **V1.5 Source Code Management Hardening**

Define and enforce security controls for the source code management (SCM) platform. This includes repository access restrictions, branch protection rules, enforced reviews, audit logging, and secrets scanning policies to ensure code integrity and traceability.

---

## **V2 – Develop**

> During the develop stage, developers focus on writing code with security built in from the start, adopting both a security-first mindset and toolset.
>
> The SPVS promotes secure coding standards, continuous code reviews, and the integration of tools that automatically detect vulnerabilities as code is written—ensuring issues are addressed early and efficiently within the development workflow.

### **Sub-Categories**

#### **V2.1 Secure Coding Practices**

Apply secure coding guidelines and standards throughout development to prevent common vulnerabilities like SQL injection, cross-site scripting (XSS), and others. Following these best practices early helps ensure a more secure codebase before it enters the pipeline.

#### **V2.2 Software Quality**

Consistently run quality, linting, and style checks during development, as unresolved technical debt can quickly evolve into security debt. Addressing these issues early helps maintain clean, secure, and maintainable code before it enters the pipeline.

#### **V2.3 Code Review and Analysis**

Conduct regular code reviews and leverage static code analysis tools during development to catch and remediate security issues early. Identifying problems at this stage strengthens security and reduces risk before the code reaches the pipeline.

#### **V2.4 Perform Security Checks**

Before committing code, developers should use security tools like SAST, SCA, IaC scanners, container analysis, and secret scanning within their development environment. Running these tools locally helps catch vulnerabilities early, reduces noise in the pipeline, and ensures more secure code is delivered from the start.

#### **V2.5 Credential Hygiene**

Credential hygiene during development involves securely handling secrets like passwords, tokens, and keys on the developer’s local system. Avoid hardcoding, use secure storage or environment variables, and ensure credentials aren’t committed. Regularly rotate and remove unused credentials to maintain security.

#### **V2.6 3rd Party Library Audit**

Before committing code, developers should review third-party libraries for common security risks. Outdated, deprecated, or unnecessary libraries—like unused logging tools—can introduce vulnerabilities and expand the attack surface. By identifying and mitigating these issues early, developers reduce the risk of supply chain attacks and improve overall security before the code enters the pipeline.

#### **V2.7 Unit Testing**

Before code is pushed, each push should pass local unit tests to ensure application interfaces can withstand specific malicious activity (e.g., specific findings from a pentest that are not discovered by automated security scanners).

---

## **V3 – Integrate**

> At this stage of the development pipeline, code enters a system where new features are integrated into the main codebase and must pass predefined security checkpoints before moving toward deployment.
>
> Security is tightly woven into the process through automated validation, artifact integrity checks, and protection of the build environment against tampering. The SPVS framework reinforces this by introducing structured, repeatable security tests and scans, ensuring early detection of vulnerabilities and consistent alignment with compliance standards.

### **Sub-Categories**

#### **V3.1 Security of Pipeline Environment**

Ensure your pipeline system is hardened, built with security by design, and aligned with industry best practices.

#### **V3.2 Credential Hygiene**

Credential hygiene in pipelines involves securely creating, storing, and managing authentication mechanisms like passwords, tokens, and keys. Regularly rotate credentials and retire unused ones to enhance security.

#### **V3.3 Continuous Security Checks**

Continuously integrate automated security testing and vulnerability scanning into the build and integration pipeline to detect and address issues early. This process ensures security best practices are enforced at every stage, enabling teams to identify risks before deployment and maintain a secure development workflow.

#### **V3.4 Integrity of Artifacts**

Implement measures to ensure the integrity of build artifacts, such as cryptographic signing and checksum validation.

---

## **V4 – Release**

> The Release stage ensures software is production-ready and securely deployed.
> It includes final security validations, compliance checks, and approvals in staging or pre-production environments.
> Once validated, automated and auditable deployment pipelines deliver the release to production with minimal risk.
> SPVS emphasizes artifact integrity, change control, and secure rollout strategies to maintain trust and stability during deployment.

### **Sub-Categories**

#### **V4.1 Final Security Assessments**

Conduct comprehensive security evaluations in pre-production environments, including penetration tests, vulnerability scans, and manual reviews. These assessments confirm that the release meets all security requirements before going live.

#### **V4.2 Compliance Checks**

Validate that the software complies with all relevant internal policies, regulatory frameworks, and industry standards. This includes verifying security controls, audit readiness, and documentation before release.

#### **V4.3 Secure Deployment Practices**

Use automated and repeatable deployment methods to securely release software into production. Minimize manual steps, enforce validation gates, and apply secure configurations to reduce the risk of deployment-time vulnerabilities.

#### **V4.4 Transition Security**

Apply controls to secure the transition from staging to production. This includes the use of encrypted transfers, validated runtime configurations, and protocols that ensure integrity and confidentiality during the deployment process.

---

## **V5 – Operate**

> Operate covers the ongoing management, monitoring, and protection of systems in production.
> This includes incident response, performance monitoring, patch management, access control, and continuous security enforcement.
> SPVS advocates for real-time visibility, anomaly detection, and operational resilience to ensure sustained reliability, compliance, and a strong security posture over time.

### **Sub-Categories**

#### **V5.1 Access Audit**

Routinely perform audits on who has user, elevated, or privileged access to ensure only authorized individuals retain access.

#### **V5.2 Security Standard Enforcement**

Ensure production systems continuously adhere to established security standards and compliance policies. This includes automated checks, runtime controls, and configuration enforcement to prevent drift or deviation from approved security baselines.

#### **V5.3 Secure Maintenance Practices**

Maintain operational systems securely by applying patches, performing updates, and managing administrative access using secure procedures. Emphasize minimal downtime, traceability, and risk mitigation during maintenance windows.

#### **V5.4 Detection & Monitoring**

Continuously observe production environments using real-time monitoring tools and telemetry. Detect anomalous behavior, potential intrusions, or system misconfigurations as they occur, and route alerts to appropriate responders.

#### **V5.5 Incident Response & Recovery**

Develop, document, and practice incident response procedures for production environments. Ensure teams can rapidly triage, contain, and recover from security events while maintaining audit trails and minimizing business impact.

---