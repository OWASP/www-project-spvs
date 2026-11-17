# Secure Pipeline Verification Standard (SPVS) 2.0 Categories Overview

This document outlines the stages and subcategories of the Secure Pipeline Verification Standard (SPVS) 2.0, designed to integrate security throughout the software development lifecycle, including the AI systems and agents that now operate inside it.

---

## Column Descriptions

| Column Name | Description |
|---|---|
| **category_id** | Unique identifier of the top-level SPVS category. Valid values are V1, V2, V3, V4, V5. See the list below for the corresponding names. |
| **category_name** | Human readable name of the category that pairs with category_id. Valid values are Plan, Develop, Integrate (CI\*), Release (CD\*), Operate. |
| **sub-category_id** | Identifier of the sub-category within the category. Format is V#.# where the first number matches category_id and the second number may be one or two digits (for example V3.13). See the lists below for valid values. |
| **sub-category_name** | Human readable name of the sub-category that pairs with sub-category_id. Use the names listed below for each category. |
| **req_id** | Unique requirement identifier under a given sub-category. Format is V#.#.# for example V1.2.3 or V3.13.14. This provides traceability across documents and versions. |
| **req_name** | Short title of the verification requirement. Keep it concise and specific so it is usable in reports and dashboards. |
| **req_description** | Complete statement of the verification requirement, written as a "Verify that..." statement describing an objective condition that can be tested. |
| **level 1** | Marked with X when the requirement first applies at SPVS Level 1 (Foundational). |
| **level 2** | Marked with X when the requirement first applies at SPVS Level 2 (Standard). |
| **level 3** | Marked with X when the requirement first applies at SPVS Level 3 (Advanced). |
| **tags** | One or more tags from the controlled vocabulary below, used to filter requirements by control domain across categories. |
| **source_version** | SPVS version in which the requirement originated. Valid values are 1.0, 1.5, 1.6, 2.0. |
| **source_req_id** | Requirement identifier in the source_version. Blank for requirements new in 2.0. Preserves traceability across sub-category renumbering. |
| **NIST 800-53 (Rev. 5, Release 5.2.0)** | One or more NIST SP 800-53 Rev. 5 control identifiers that map to the requirement, including control enhancements. Examples: AC-6, IA-2(1), SI-7(6). |
| **NIST SSDF (SP 800-218 v1.1)** | One or more NIST Secure Software Development Framework practice/task identifiers that map to the requirement. Examples: PO.5.1, PW.4.4, PS.3.2, RV.1.1. May be blank where no SSDF task applies. |
| **OWASP_CICD_Top10** | One or more OWASP Top 10 CI/CD Security Risks identifiers relevant to the requirement. Valid values are CICD-SEC-1 through CICD-SEC-10. May be blank where no CI/CD risk applies. |

### Tag Vocabulary

| Tag | Tag | Tag | Tag |
|---|---|---|---|
| access-control | ai | ai-agent | artifacts |
| build | change-control | configuration | dependencies |
| deployment | developer-tools | endpoint | governance |
| identity | incident-response | integrity | inventory |
| logging | monitoring | network | provenance |
| secrets | security-scanner | source-control | testing |

### Conventions

- Category and sub-category fields must use one of the valid values listed below.
- Each req_id belongs to exactly one category and one sub-category, and its prefix matches the sub-category_id.
- Levels are cumulative. Mark only the lowest level at which a requirement applies; higher levels include all controls from lower levels unless explicitly scoped otherwise.
- Separate values in multi-value fields (tags, NIST 800-53, NIST SSDF, OWASP_CICD_Top10) with a semicolon followed by a space (for example `AC-6; IA-5`). Commas are not used because they conflict with CSV delimiters.
- Every requirement scoped to AI systems carries the `ai` tag. Requirements scoped to AI agents also carry `ai-agent`.
- Requirements carried forward from earlier versions keep their source_version and source_req_id.
- Keep naming stable to preserve traceability across versions.

\* The CI and CD labels on the Integrate and Release categories indicate that these stages typically map to Continuous Integration and Continuous Delivery/Deployment tooling.

---

## **Categories (category_id and category_name)**

* **V1 / Plan**
* **V2 / Develop**
* **V3 / Integrate (CI\*)**
* **V4 / Release (CD\*)**
* **V5 / Operate**

### Requirement Summary

| Category | Sub-Categories | Requirements | Level 1 | Level 2 | Level 3 |
|---|---|---|---|---|---|
| V1 / Plan | 9 | 64 | 28 | 28 | 8 |
| V2 / Develop | 7 | 39 | 13 | 25 | 1 |
| V3 / Integrate (CI\*) | 13 | 101 | 32 | 49 | 20 |
| V4 / Release (CD\*) | 10 | 42 | 7 | 22 | 13 |
| V5 / Operate | 9 | 45 | 5 | 22 | 18 |
| **Total** | **48** | **291** | **85** | **146** | **60** |

Because levels are cumulative, 85 requirements apply at Level 1, 231 at Level 2, and all 291 at Level 3.

By origin: 101 requirements from 1.0, 127 from 1.5, 50 from 1.6, and 13 new in 2.0. 127 requirements carry the `ai` tag.

---

## **Sub-Categories (by category, used in sub-category_id and sub-category_name)**

### **Plan (V1)**

* V1.1 Security Requirements and Risk Assessment
* V1.2 Developer Security Training
* V1.3 Identity and Access Management
* V1.4 NHI (Non-Human Identity) Governance for AI Agents
* V1.5 Hardening User Machines
* V1.6 Developer Tool Operation
* V1.7 AI Asset Discovery and Inventory Governance
* V1.8 Source Code Management Hardening
* V1.9 AIBOM (AI Bill of Materials) Governance

### **Develop (V2)**

* V2.1 Software Quality
* V2.2 Code Review and Analysis
* V2.3 Perform Security Checks
* V2.4 AI-Assisted Secure Development Controls
* V2.5 Credential Hygiene
* V2.6 3rd Party Library Audit
* V2.7 Unit Testing

### **Integrate (V3)**

* V3.1 Security of Pipeline Environment
* V3.2 Agent Runtime Isolation
* V3.3 Network and Dependency Control
* V3.4 Credential Hygiene
* V3.5 Agent Identity Enforcement
* V3.6 Secret Isolation for Agents
* V3.7 Continuous Security Checks
* V3.8 Prompt Input Classification and Sanitization
* V3.9 Deterministic Tool Authorization
* V3.10 Multi-Agent Delegation Controls
* V3.11 Retrieval Data Governance
* V3.12 MCP and Tool Server Security
* V3.13 Integrity of Artifacts

### **Release (V4)**

* V4.1 Final Security Assessments
* V4.2 Adversarial Testing and AI Red Teaming
* V4.3 Compliance Checks
* V4.4 Secure Deployment Practices
* V4.5 Agentic Release Assurance and Change Control
* V4.6 Transition Security
* V4.7 Model Supply Chain Integrity
* V4.8 Model Change Control
* V4.9 System Prompt Integrity and Governance
* V4.10 AIBOM Generation and Validation

### **Operate (V5)**

* V5.1 Access Audit
* V5.2 Security Standard Enforcement
* V5.3 Secure Maintenance Practices
* V5.4 Detection & Monitoring
* V5.5 Agent Observability and Logging
* V5.6 Blast Radius and Runtime Safeguards
* V5.7 AIBOM Drift and Runtime Reconciliation
* V5.8 Incident Response & Recovery
* V5.9 Incident Response for Agent Compromise

---

# **Category Details**

---

## **V1 – Plan**

> This stage focuses on defining the scope, objectives, and security requirements for the upcoming iteration. It includes assessing potential risks, establishing security baselines, and aligning plans with business goals and compliance needs.
>
> In line with SPVS principles, planning is not a one-time activity. It incorporates feedback loops, postmortems, threat modeling, and lessons learned from previous iterations, incidents, or audits. This ensures continuous improvement in both product quality and security posture over time.
>
> Planning now also covers AI governance: registering AI agents as non-human identities, inventorying AI assets before they reach the pipeline, and defining the AIBOM policy that later stages generate and enforce against.

### **Sub-Categories**

#### **V1.1 Security Requirements and Risk Assessment**

Document the software pipeline and establish the policies every later stage depends on: a secure development policy covering the OWASP Top 10 CI/CD Security Risks, a secure coding standard for the languages and frameworks in use, a secure open source software policy, and a secrets and credentials policy. Confirm developers have reviewed the secure development policy. Define a documented exception process and risk acceptance record for AI assets that cannot meet standard governance requirements, with compensating controls, risk owner sign-off, and expiration dates. At Level 3, run build, signing, and publish as separate stages on independently managed systems.

#### **V1.2 Developer Security Training**

Ensure developers and pipeline administrators complete role-specific secure development training at an organization-defined interval, so the people writing code and operating the pipeline understand the policies and threats they are expected to defend against.

#### **V1.3 Identity and Access Management**

Plan and govern access for every identity that touches the pipeline, human and programmatic. Manage all identities through a centralized identity provider, enforce MFA on developer endpoints, critical systems, and the version control system, and require phishing-resistant MFA on every account with package publish rights, enforced per package. Apply least privilege through documented role-to-permission matrices, team-scoped repository read access, read-only default workflow permissions, and single-purpose write credentials. Encrypt secrets at rest and in transit, disable stale identities, and audit VCS administrators and service account token permissions on a defined cadence.

#### **V1.4 NHI (Non-Human Identity) Governance for AI Agents**

Register every AI agent operating within the SDLC as a non-human identity with a documented owner, purpose, and approved scope. Define onboarding and offboarding procedures, a policy for maximum allowable permission scopes, automated credential expiration, a permission review cadence, and automatic disablement of inactive agent identities.

#### **V1.5 Hardening User Machines**

Apply security controls to developer and administrative workstations to reduce the attack surface. This includes endpoint protection that updates routinely, full disk encryption, patch management, automatic screen lock after inactivity, and, at Level 3, the applicable CIS Benchmark controls for OS hardening.

#### **V1.6 Developer Tool Operation**

Establish policies for approved IDEs, code editors, plugins, extensions, and AI coding assistants to prevent the use of insecure or unvetted software. Approved AI coding assistants must have documented data handling practices covering code transmission, training data use, and retention. Keep approved tools on vendor-supported versions, require encrypted communications, and restrict extensions to a centrally approved, version-pinned, checksum-verified list. Block automatic code execution when a repository is opened until the user explicitly trusts the workspace, and monitor tool and extension inventory for unauthorized changes. At Level 3, govern extension egress destinations and isolate the developer toolchain from host credentials, configuration files, and network resources.

#### **V1.7 AI Asset Discovery and Inventory Governance**

Record AI tools, agent frameworks, model integrations and endpoints, MCP and tool servers, and retrieval sources in an AI asset inventory before production pipeline use. Each entry captures ownership, risk classification, approved usage scope, and data sensitivity impact. Run a documented discovery process to find unauthorized or ungoverned AI tooling, and block production pipeline integration of any AI asset that lacks a completed governance review.

#### **V1.8 Source Code Management Hardening**

Define and enforce security controls for the version control system. This includes role-based access control with documented role definitions, ignore files that keep sensitive content out of commits, pipeline-side verification of commit authorship that does not rely on warnings in the VCS web interface, and, at Level 3, an enforced branch naming convention.

#### **V1.9 AIBOM (AI Bill of Materials) Governance**

Define the AIBOM policy before AIBOMs are generated. The policy sets required scope (models, datasets, prompts, agent frameworks and SDKs, tool servers, retrieval sources, and external endpoints), approved schemas and machine-readable formats, mandatory fields, and retention and access control requirements. Assign an accountable AIBOM owner to each pipeline-integrated AI system and define the changes that trigger regeneration. At Level 3, define signing or integrity protection requirements and tier AIBOM depth by AI system criticality.

---

## **V2 – Develop**

> During the develop stage, developers focus on writing code with security built in from the start, adopting both a security-first mindset and toolset.
>
> The SPVS promotes secure coding standards, continuous code reviews, and the integration of tools that automatically detect vulnerabilities as code is written, ensuring issues are addressed early and efficiently within the development workflow.
>
> AI-generated code is held to the same bar as human-written code, with no review or scanning bypass for AI tool or agent identities.

### **Sub-Categories**

#### **V2.1 Software Quality**

Run linting with code style, formatting, and syntax bug rules before each commit, and remediate findings at or above an organization-defined severity before commit. Unresolved technical debt quickly becomes security debt, so addressing it here keeps code clean and maintainable before it enters the pipeline.

#### **V2.2 Code Review and Analysis**

Define a security code review policy that designates which changes require security review, and require approval from a human application security specialist or trained security champion before those changes merge. Automated static analysis is covered in V2.3 (pre-commit) and V3.7 (CI).

#### **V2.3 Perform Security Checks**

Before committing code, developers run first-party code scanning (SAST), dependency scanning (SCA), secret detection, and IaC scanning in their development environment, along with every other scan type the security policy requires. Each tool runs a vendor-supported version with the latest rulesets or vulnerability database, and the IaC tool checks the organization's IaC security policies. Third-party libraries are updated to patched versions within severity-tiered timeframes. Running these checks locally catches vulnerabilities early and reduces noise in the pipeline.

#### **V2.4 AI-Assisted Secure Development Controls**

Ensure AI-generated changes cannot bypass mandatory peer review or branch protection. AI-generated code, dependencies, secrets exposure, and IaC pass through the same automated SAST, dependency and license analysis, secret detection, and misconfiguration analysis as all other changes before merge, with no bypass for AI tool or agent identities.

#### **V2.5 Credential Hygiene**

Handle secrets securely on the developer's local system. Never hardcode credentials in code repositories or pipeline configuration files, and never store secrets in plaintext local environment files; use a secrets manager or encrypted storage instead. Review system prompts authored during development for embedded secrets, credentials, API keys, and sensitive organizational data before committing them.

#### **V2.6 3rd Party Library Audit**

Control which third-party packages reach development and build environments. Fetch dependencies only from approved sources through a private registry proxy, pin exact versions, verify cryptographic hashes, and check lockfiles for unexpected changes before a build trusts them. Disable package install scripts by default, block packages that fail screening for defined risk indicators (install scripts, low maintainer count, recent ownership change, no linked source repository) or that have not reached a minimum publish age, and require review for package names that closely match existing ones. Enforce the open source software policy with an automated check that fails violating changes. At Level 3, review dependency count and transitive depth on a defined interval and record a keep or remove decision for each flagged dependency.

#### **V2.7 Unit Testing**

Automate unit tests to run on every code change, and ensure they cover security-relevant code paths, such as regression tests for penetration test findings that automated security scanners do not detect.

---

## **V3 – Integrate (CI\*)**

> At this stage of the development pipeline, code enters a system where new features are integrated into the main codebase and must pass predefined security checkpoints before moving toward deployment.
>
> Security is tightly woven into the process through automated validation, artifact integrity checks, and protection of the build environment against tampering. The SPVS framework reinforces this by introducing structured, repeatable security tests and scans, ensuring early detection of vulnerabilities and consistent alignment with compliance standards.
>
> This stage also governs AI agents executing inside the pipeline: their runtime isolation, identity, secrets, network access, and tool authorization, along with the handling of untrusted content that enters prompt context.

### **Sub-Categories**

#### **V3.1 Security of Pipeline Environment**

Harden build servers to platform guidance, patch them regularly, restrict and monitor access, and review them for misconfiguration. Never interpolate external text such as branch names, commit messages, or pull request titles into pipeline commands, and scan every pipeline definition change for unsafe triggers, unescaped input, and excess permissions. Install dependencies exactly as listed in the lockfile, pin container base images by digest, and run build and publish as separate stages with the artifact held for review between them. Use ephemeral or regularly re-imaged runners, run install and build in egress-restricted isolation, and enforce CPU, memory, execution time, and API quota limits on AI agent execution.

#### **V3.2 Agent Runtime Isolation**

Run AI agents in isolated, ephemeral runtime environments matched to task sensitivity and destroyed after job completion. Confine filesystem access to the designated workspace and block access to host mounts and credential directories. At Level 3, prevent agents from modifying their runtime configuration or tool bindings during execution, creating new identities, or spawning processes with broader permissions than the invoking agent.

#### **V3.3 Network and Dependency Control**

Restrict outbound network access from agent execution environments to an approved allowlist, and block connections to unapproved endpoints through network or policy enforcement. Dependencies retrieved during agent execution must come from approved registries and be integrity-validated by hash, signature, or pinning before use.

#### **V3.4 Credential Hygiene**

Use built-in credential management or a secrets manager rather than hardcoded credentials, restrict who can view pipeline secrets, mask secrets in pipeline logs, and scan logs after each run for secret patterns, including encoded forms. Scope each secret to a single stage or environment, to a single project, and to only the job that needs it in reusable pipelines. Rotate secrets as the secrets policy requires, and remove static tokens left as a silent fallback beside short-lived OIDC credentials.

#### **V3.5 Agent Identity Enforcement**

Authenticate AI agents with federated workload identity and prohibit long-lived static credentials such as PATs and API keys. Enforce a maximum credential TTL and log every credential issuance event. At Level 3, restrict agent credentials to an intended audience and bind them to a single pipeline execution so they cannot be reused across invocations.

#### **V3.6 Secret Isolation for Agents**

Serve agent secrets only from a dedicated NHI secret store, deny agent secret access by default, and technically block agents from human user secret namespaces. Keep secrets out of prompts, logs, issue comments, pull request text, and every other model context channel. At Level 3, allowlist agent secret access per secret and job scope.

#### **V3.7 Continuous Security Checks**

Run first-party code scanning, dependency scanning, secret detection, IaC scanning, and linting on every change in the CI pipeline before merge, with each tool on a vendor-supported version and current rules or vulnerability data. Run DAST against running applications, enforce IaC security policies, and remediate lint findings at or above the defined severity before merge. Enforce branch protection on all repositories, restrict and review auto-merge rules, require manual approval for sensitive operations, and include security test cases in integration testing. At Level 3, verify the integrity of the security scanning tools before they run, and instrument dependency install and build steps to alert on unexpected child processes, interpreter launches, or network connections.

#### **V3.8 Prompt Input Classification and Sanitization**

Classify issues, pull request text, comments, and other external inputs as untrusted by default, sanitize them before they enter agent prompt context, and alert on known or suspected injection patterns. Treat model output and agent-provided instructions as untrusted, and validate them deterministically before they invoke a tool, execute a command, or trigger a downstream pipeline action. Bound prompt context size and token consumption to prevent context overflow, token stuffing, and safety control bypass.

#### **V3.9 Deterministic Tool Authorization**

Model output alone never authorizes a privileged action. Restrict agent tool invocation to an explicit allowlist, enforce deterministic policy before any privileged action, and require a separate authorization gate for privileged tools.

#### **V3.10 Multi-Agent Delegation Controls**

Define trust between orchestrator agents and sub-agents explicitly in policy rather than allowing it to be inherited, and apply the same prompt injection controls to inter-agent input as to external input. At Level 3, bound sub-agents to the permissions delegated at invocation, require explicit approval at every repository or environment trust boundary crossing, and contain the blast radius so compromise of one agent cannot grant the full orchestrator permission scope.

#### **V3.11 Retrieval Data Governance**

Classify retrieval data sources and review their access controls before use, and restrict retrieval to an approved allowlist enforced at the access control layer. Treat retrieved content as untrusted input subject to injection controls. At Level 3, capture retrieval queries and returned content in execution provenance sufficient for forensic reconstruction.

#### **V3.12 MCP and Tool Server Security**

Restrict MCP and tool server endpoints to an approved allowlist, and authenticate every connection, blocking unauthenticated servers. At Level 3, integrity-check tool definitions and capability manifests before use, and detect and block runtime substitution of tool definitions.

#### **V3.13 Integrity of Artifacts**

Validate artifact checksums before deployment, cryptographically sign build artifacts, and make published release tags and version references immutable. Generate a machine-readable SBOM for every build, validate it before deployment, and produce a signed provenance attestation that binds each artifact to its source, builder identity, and build parameters. Pin the direct dependencies of external build steps and plugins, and sign or checksum CI/CD cache contents at write time with the integrity value stored outside the cache, verifying it on restore. At Level 3, verify signatures between pipeline stages, validate builder identity and isolation state in provenance attestations, reconcile published artifacts against release pipeline output, confirm pinned commits are reachable on a real branch, and pin all transitive dependencies of external build steps.

---

## **V4 – Release (CD\*)**

> The Release stage ensures software is production-ready and securely deployed.
> It includes final security validations, compliance checks, and approvals in staging or pre-production environments.
> Once validated, automated and auditable deployment pipelines deliver the release to production with minimal risk.
> SPVS emphasizes artifact integrity, change control, and secure rollout strategies to maintain trust and stability during deployment.
> For AI systems, release adds adversarial testing, model supply chain integrity, change control for models, frameworks, and system prompts, and AIBOM generation as a release gate.

### **Sub-Categories**

#### **V4.1 Final Security Assessments**

Run every security assessment type the documented security policy requires against the release candidate before release, such as penetration tests, vulnerability scans, and manual reviews. At Level 3, run AI behavioral regression tests against documented baselines before promoting any model version, configuration, or system prompt change to production.

#### **V4.2 Adversarial Testing and AI Red Teaming**

Test pipeline-integrated agents for prompt injection, jailbreak attempts, and sensitive data extraction before production deployment. At Level 3, run adversarial testing on a documented cadence with remediation SLAs, cover non-text inputs such as files, images, and structured data, and feed results into prompt controls, tool allowlists, and system prompt hardening before promotion.

#### **V4.3 Compliance Checks**

Formally document pipeline-related policies, maintain them as compliance artifacts, and review them periodically for accuracy and relevance, so the release can be shown to meet internal policies, regulatory frameworks, and industry standards.

#### **V4.4 Secure Deployment Practices**

Use automated deployment scripts that are reviewed for security vulnerabilities, follow change control, and check for unauthorized changes before execution. Isolate production from development and testing environments, and store production configuration secrets in a secrets manager or in encrypted files whose keys are held in a separate KMS or HSM. Signature and attestation checks cannot be bypassed outside a documented break-glass process that alerts immediately, and identities that publish more than one package are rate limited or automatically blocked on bulk releases. At Level 3, accept only release-specific credentials in the release stage, roll out AI agent changes through staged or canary deployment, and treat fine-tuning, quantization, and other derived model artifacts as model version changes.

#### **V4.5 Agentic Release Assurance and Change Control**

Prevent AI agents from approving, merging, or altering the protection rules that govern review of their own output, and from triggering production deployments without an explicit human-authorized approval gate. Require elevated approval when an agent modifies pipeline definition files, and designated security owner approval for changes to agent permissions, capability allowlists, or tool integrations.

#### **V4.6 Transition Security**

Use secure transfer protocols during deployment to protect integrity and confidentiality as software moves from staging to production.

#### **V4.7 Model Supply Chain Integrity**

Source AI models and agent frameworks only from approved registries with documented provenance, and risk-assess and explicitly allowlist externally hosted model endpoints before use. At Level 3, pin model references by cryptographic digest and block unpinned references.

#### **V4.8 Model Change Control**

Treat changes to model version, model configuration, and agent framework or SDK version as pipeline changes subject to the same review and approval controls as code.

#### **V4.9 System Prompt Integrity and Governance**

Version-control system prompts used by pipeline-integrated agents, subject them to peer review and change approval, and keep secrets, credentials, and sensitive organizational data out of them. At Level 3, validate system prompt integrity at agent initialization, block execution on deviation from the approved configuration, and record the active prompt version in execution provenance.

#### **V4.10 AIBOM Generation and Validation**

Generate an AIBOM for each pipeline-integrated AI system or agent before production release and store it as a release artifact. Reject AIBOMs that fail schema conformance, and block release when required fields are missing. Required content covers model components (identifiers, versions, lineage, supplier, and integrity metadata), system prompt versions, agent frameworks and SDKs, and external endpoints with allowlist status recorded. At Level 3, include dataset and retrieval source fields, validate AIBOM integrity at the release gate, and automate AIBOM regeneration in the same CI/CD workflow as the change that triggers it.

---

## **V5 – Operate**

> Operate covers the ongoing management, monitoring, and protection of systems in production.
> This includes incident response, performance monitoring, patch management, access control, and continuous security enforcement.
> SPVS advocates for real-time visibility, anomaly detection, and operational resilience to ensure sustained reliability, compliance, and a strong security posture over time.
> For AI agents, operation adds observability, blast radius limits, AIBOM drift reconciliation, and incident response for agent compromise.

### **Sub-Categories**

#### **V5.1 Access Audit**

Review user access entitlements to version control, CI/CD platforms, artifact registries, and secret stores on a documented cadence. Maintain and periodically review access logs, and implement and monitor privileged access management.

#### **V5.2 Security Standard Enforcement**

Ensure every software component running in production traces to a current, pinned SBOM generated and validated by the build pipeline, confirming nothing was installed outside the approved build process. At Level 3, enforce production security policies through an automated mechanism that blocks violating deployments and configuration changes, and review operational practices against documented security policies on a defined cadence.

#### **V5.3 Secure Maintenance Practices**

Apply security patches to CI/CD servers, build agents, and runtime hosts within documented severity-based timeframes. Continuously monitor third-party components in production software against vulnerability feeds, and remediate newly disclosed vulnerabilities within organization-defined timeframes.

#### **V5.4 Detection & Monitoring**

Monitor pipelines in real time for anomalies, routinely review security logs for anything automation misses, and triage alerts promptly. Alert on every pipeline definition change with the identity of the actor, notify on every automated package publish and investigate any publish the team did not expect, monitor runner egress, restrict cloud metadata endpoint access on build agents, and log prompt injection detection events with full context. At Level 3, alert on cross-process memory reads on build agents, check workloads in shared cluster namespaces against an approved list, and alert on anomalous behavior from developer endpoint extensions and tools.

#### **V5.5 Agent Observability and Logging**

Log every agent action with identity context, permission scope, tool usage, and outcome. Log agent secret access attempts, egress destinations, and tool invocations, including MCP and tool server calls, in enough detail to reconstruct requests and responses. At Level 3, log inter-agent communications as distinct events that reconstruct the full delegation chain, and store agent activity logs in tamper-evident or append-only systems.

#### **V5.6 Blast Radius and Runtime Safeguards**

Require explicit out-of-band human approval before agents perform irreversible high-impact operations, enforce execution rate limits and action quotas per agent identity, and apply data classification controls to prompt logs. At Level 3, enforce a permission ceiling that agent-initiated requests cannot expand, exclude sensitive data from agent context when the task does not require it, monitor outbound data volume, reconcile agent credential usage against logged task scope, and detect anomalous agent behavior at runtime.

#### **V5.7 AIBOM Drift and Runtime Reconciliation**

Retain AIBOM records, including historical versions aligned to releases and deployments, in a queryable form for audits and forensics. Continuously monitor AIBOM components against vulnerability feeds and trigger remediation or block execution based on severity. At Level 3, reconcile deployed AI components against the approved AIBOM and alert on drift.

#### **V5.8 Incident Response & Recovery**

Maintain incident response plans with procedures specific to pipeline security incidents. When rotating a credential because of an incident, revoke the compromised credential before activating its replacement, within a defined SLO. At Level 3, test response plans regularly, demonstrate recovery within the documented RTO, and include prompt controls, tool allowlists, system prompts, AIBOM entries, and detection thresholds in post-incident reviews of AI agent compromise.

#### **V5.9 Incident Response for Agent Compromise**

Maintain playbooks for AI agent compromise and prompt injection scenarios, and ensure responders can suspend agent identities and rotate their credentials without a full pipeline shutdown. At Level 3, preserve forensic evidence of agent inputs, tool calls, accessed data classes, outputs, and downstream effects with data classification controls, and exercise the playbooks on a documented cadence with gaps tracked to remediation.

---

# **Appendix: Changes from the Previous Overview**

### Column Changes

| Change | Column |
|---|---|
| Added | tags, source_version, source_req_id, NIST SSDF (SP 800-218 v1.1) |
| Renamed | NIST to NIST 800-53 (Rev. 5, Release 5.2.0); Category_ID to category_id |
| Removed | cwe_mapping, cwe_description |
| Changed | Multi-value separator from comma to semicolon |
| Changed | category_name values for V3 and V4 to Integrate (CI\*) and Release (CD\*) |

### Sub-Category Renumbering

| Previous ID | Sub-Category | 2.0 ID | Notes |
|---|---|---|---|
| V1.1 | Identity and Access Management | V1.3 | |
| V1.2 | Hardening User Machines | V1.5 | |
| V1.3 | Security Requirements and Risk Assessment | V1.1 | Now also holds the secure coding standard (V1.1.9) |
| V1.4 | Developer Tool Operation | V1.6 | |
| V1.5 | Source Code Management Hardening | V1.8 | Branch protection moved to V3.7.17 |
| V2.1 | Secure Coding Practices | Removed | Standard moved to V1.1.9; OSS policy enforcement moved to V2.6.11 |
| V2.2 | Software Quality | V2.1 | |
| V2.3 | Code Review and Analysis | V2.2 | |
| V2.4 | Perform Security Checks | V2.3 | |
| V2.5 | Credential Hygiene | V2.5 | |
| V2.6 | 3rd Party Library Audit | V2.6 | |
| V2.7 | Unit Testing | V2.7 | |
| V3.1 | Security of Pipeline Environment | V3.1 | |
| V3.2 | Credential Hygiene | V3.4 | |
| V3.3 | Continuous Security Checks | V3.7 | |
| V3.4 | Integrity of Artifacts | V3.13 | |
| V4.1 | Final Security Assessments | V4.1 | |
| V4.2 | Compliance Checks | V4.3 | |
| V4.3 | Secure Deployment Practices | V4.4 | |
| V4.4 | Transition Security | V4.6 | |
| V5.1 | Access Audit | V5.1 | |
| V5.2 | Security Standard Enforcement | V5.2 | |
| V5.3 | Secure Maintenance Practices | V5.3 | |
| V5.4 | Detection & Monitoring | V5.4 | |
| V5.5 | Incident Response & Recovery | V5.8 | |

### New Sub-Categories

| 2.0 ID | Sub-Category | Requirements Originated In |
|---|---|---|
| V1.2 | Developer Security Training | 2.0 |
| V1.4 | NHI (Non-Human Identity) Governance for AI Agents | 1.5 |
| V1.7 | AI Asset Discovery and Inventory Governance | 1.5 |
| V1.9 | AIBOM (AI Bill of Materials) Governance | 1.5 |
| V2.4 | AI-Assisted Secure Development Controls | 1.5 |
| V3.2 | Agent Runtime Isolation | 1.5 |
| V3.3 | Network and Dependency Control | 1.5 |
| V3.5 | Agent Identity Enforcement | 1.5 |
| V3.6 | Secret Isolation for Agents | 1.5 |
| V3.8 | Prompt Input Classification and Sanitization | 1.5 |
| V3.9 | Deterministic Tool Authorization | 1.5 |
| V3.10 | Multi-Agent Delegation Controls | 1.5 |
| V3.11 | Retrieval Data Governance | 1.5 |
| V3.12 | MCP and Tool Server Security | 1.5 |
| V4.2 | Adversarial Testing and AI Red Teaming | 1.5 |
| V4.5 | Agentic Release Assurance and Change Control | 1.5 |
| V4.7 | Model Supply Chain Integrity | 1.5 |
| V4.8 | Model Change Control | 1.5 |
| V4.9 | System Prompt Integrity and Governance | 1.5 |
| V4.10 | AIBOM Generation and Validation | 1.5 |
| V5.5 | Agent Observability and Logging | 1.5 |
| V5.6 | Blast Radius and Runtime Safeguards | 1.5 |
| V5.7 | AIBOM Drift and Runtime Reconciliation | 1.5 |
| V5.9 | Incident Response for Agent Compromise | 1.5 |