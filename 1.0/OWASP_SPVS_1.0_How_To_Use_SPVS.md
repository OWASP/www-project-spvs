# How to Use OWASP SPVS

## Overview
The **OWASP Secure Pipeline Verification Standard (SPVS)** is a structured framework for evaluating and improving the security of software delivery pipelines.  
It is modeled after the **OWASP Application Security Verification Standard (ASVS)** but focuses on the security of build, deployment, and operational automation across software pipeline environments.

SPVS defines controls for each stage of the software pipeline:

1. **Plan** – Governance, risk management, secure configuration, and foundational policies.  
2. **Develop** – Secure development practices and code hygiene.  
3. **Integrate** – Build system hardening and artifact integrity.  
4. **Release** – Deployment and environment security.  
5. **Operate** – Continuous monitoring, maintenance, and incident management.

Each control in SPVS includes mappings to:
- **OWASP software pipeline Top 10** risks  
- **NIST 800-53** security controls  
- **CWE** (Common Weakness Enumeration) identifiers  

This allows SPVS to be used for both engineering and compliance assurance.

---

## Understanding SPVS Levels

SPVS defines **three verification levels** to represent increasing depth of security assurance.

| **Level** | **Purpose** | **Typical Users** | **Example Practices** |
|------------|--------------|------------------|-----------------------|
| **Level 1 – Foundational** | Establishes baseline pipeline hygiene. Focuses on simple, enforceable controls. | Small teams or organizations building their first secure pipeline. | MFA, endpoint protection, source control hardening, approved tooling. |
| **Level 2 – Standard** | Expands to automation, monitoring, and evidence of enforcement. | Mature DevSecOps teams managing regulated workloads. | Automated secret scanning, policy-as-code enforcement, release reviews. |
| **Level 3 – Advanced** | Demonstrates continuous verification, independence, and assurance at scale. | Enterprises or high-risk environments. | Automated gating, audit logging, verified builds, third-party attestations. |

Each requirement indicates the **level(s)** where it applies (for example, Level 1 only, or Level 2 and above).  
You should target the level appropriate to your risk profile and regulatory obligations.

## Example Usage Scenarios

| **Scenario** | **SPVS Application** |
|---------------|----------------------|
| Startup adopting GitHub Actions | Apply Plan → Develop → Integrate controls at Level 1. Focus on IAM, secret management, and source control protection. |
| Mid-sized SaaS with regulated customers | Target Level 2. Enforce signed builds, automated scanning, and reviewed deployments. |
| Enterprise pursuing audit-ready DevSecOps | Adopt Level 3. Require attestations, reproducible builds, and continuous verification. |

---

## How to Apply SPVS

### Step 1. Define Pipeline Scope
Map all components that make up your software pipeline:
- Source repositories and access controls  
- Build, integration, and deployment systems  
- Infrastructure-as-code, containers, and environments  
- Monitoring and operational processes

This helps align SPVS categories with actual tools and workflows.

---

### Step 2. Choose the Target Level
Select the SPVS level that best matches your organization’s maturity and assurance goals.
- **Start with Level 1** if you’re establishing basic security hygiene.  
- **Progress to Level 2** once automation and verification are common practice.  
- **Adopt Level 3** for pipelines requiring external assurance or regulatory compliance.

---

### Step 3. Assess Current Controls
For each category and sub-category:
- Review your current controls against SPVS requirements.  
- Mark each control as **implemented**, **partially implemented**, or **not implemented**.  
- Document supporting evidence and responsible owners.

Use the SPVS control IDs to maintain traceability and facilitate audits.

---

### Step 4. Implement Improvements
Focus first on missing controls at your target level:
- Define remediation tasks in backlog or pipeline security epics.  
- Prioritize by impact and feasibility.  
- Track progress over time.

SPVS can be used as an **internal checklist** or **external audit baseline**.

---

### Step 5. Integrate SPVS Into Your Processes
While SPVS itself is not an automated tool, it can inform automation:
- Represent controls as **policy-as-code rules** in systems like OPA, Jenkins, GitHub Actions, or GitLab CI.  
- Use SPVS requirements to drive **pipeline checks** such as secret scanning, dependency validation, or enforcement of signed artifacts.  
- Integrate SPVS status tracking into dashboards or compliance reporting tools.

This makes SPVS “live” within your software pipeline workflows.

---

### Step 6. Review and Improve
Reassess your SPVS implementation regularly:
- After major architectural or tool changes  
- At least annually, or before compliance assessments  
- When new OWASP or NIST guidance is released

Document each verification review and update evidence as needed.

---

## Best Practices
- Treat **Level 1** as your minimum viable baseline before expanding coverage.  
- Ensure **MFA and IAM** controls are unified across all pipeline systems.  
- Use **CWE mappings** to analyze technical weaknesses underlying failed controls.  
- Reference **ASVS** for application-layer security alignment.  
- Focus on **evidence and repeatability**; SPVS should demonstrate consistent enforcement, not one-time checks.

---

## References
- [OWASP SPVS Project Page](https://owasp.org/www-project-spvs/)  
- [OWASP SPVS GitHub Repository](https://github.com/OWASP/www-project-spvs/)  
- [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/)  
- [OWASP CI/CD Top 10](https://owasp.org/www-project-top-10-ci-cd-security-risks/)  
- [NIST SP 800-53 Rev. 5](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)  
- [Common Weakness Enumeration (CWE)](https://cwe.mitre.org/)  
