```markdown
# 1.5 RELEASE
# Release Announcement: SPVS 1.5 — AI Pipeline Security (Community Feedback Edition)

We're releasing SPVS 1.5 today as a community feedback edition.

We had a choice: sit on these AI controls for another six months while we debated
them internally, or get them in front of the community now and let real-world
practitioners tell us what we got right, what we missed, and what needs to change.
We chose the latter.

These controls are substantive and we believe they're directionally correct, but
1.5 is not a finalized standard. It's a working draft designed to generate
feedback, surface gaps, and give the community a seat at the table before we lock
things down in 2.0.

## The Roadmap

**1.5 (now):** AI and agentic pipeline security controls. Community feedback edition.
Get involved.

**1.6 (coming in the next few months):** Supply chain attack controls. We're filling
the gap on controls that would have applied to recent attacks including TeamPCP,
the Axios npm compromise, and similar incidents. If you have experience with these
attacks and an opinion on what controls should exist, that's exactly the kind of
contribution we're looking for.

**2.0 (targeting October 2026):** The major release. Focus areas include artifact
security, dependency management, chain of custody for dependencies, and a broader
set of control gaps we've been tracking. This follows the same October release
cadence we established with 1.0.

If you have opinions on any of these areas, now is the time to open a PR.

## Why AI Controls Now

We've had consistent requests from the community for AI-specific pipeline controls.
AI coding assistants, agentic CI/CD integrations, and multi-agent workflows are
already in production pipelines. The guidance on how to secure them is fragmented.
We'd rather have an imperfect standard in the community's hands than a perfect one
that arrives too late to influence how these systems get built.

These controls are not the final word. They're the opening position.

# Check out SPVS 1.5!

- [SPVS 1.5 AI Controls](OWASP_SPVS_1.5_-en_Requirements.csv)
- [SPVS 1.0 Controls for Reference](../1.0/OWASP_SPVS_1.0_-en_Requirements.csv)
- [How to Contribute to SPVS](../CONTRIBUTING.md)
- [How to Join the SPVS Team](../MAINTAINERS.md)

---

# **SPVS 1.5 Release Notes**

* **[AI-Focused Controls Released for Community Feedback:](OWASP_SPVS_1.5_-en_Requirements.csv)**
  SPVS 1.5 introduces controls across all five pipeline phases covering AI agent
  governance, agentic runtime security, model supply chain integrity, prompt security,
  and AI-specific incident response. These are community feedback controls. Review
  them, challenge them, and submit PRs.

* **NHI (Non-Human Identity) Governance:**
  V1.3 establishes requirements for registering, scoping, and lifecycle-managing AI
  agent identities. If your agent has permissions, it needs governance.

* **AIBOM (AI Bill of Materials) Governance:**
  V1.5 and V4.2 introduce end-to-end AIBOM requirements covering policy, generation,
  validation, signing, and drift detection. Know what's in your AI system the same
  way you know what's in your software supply chain.

* **AI Asset Discovery and Inventory:**
  V1.4 requires discovery processes for ungoverned AI tooling, mandatory inventory
  registration before production pipeline use, and governance review gates for
  unapproved assets.
  *Shadow AI is the new shadow IT.*

* **AI-Assisted Secure Development Controls:**
  V2.2 addresses AI-generated code in pipelines. Controls cover peer review bypass
  prevention, SAST, SCA, secrets detection, IaC misconfiguration analysis, and
  validation gates for AI-generated scripts before execution.

* **Deterministic Tool Authorization:**
  V3.2 establishes that model output alone cannot invoke privileged actions. Controls
  require explicit allowlists, separate authorization gates, and full audit logging
  for agent tool invocations.
  *The model suggests. Policy decides.*

* **Multi-Agent Delegation Controls:**
  V3.3 addresses agent chains and orchestration patterns. Controls prevent implicit
  trust inheritance, permission escalation across agents, and cross-boundary traversal
  without explicit approval at each hop.

* **MCP and Tool Server Security:**
  V3.5 covers Model Context Protocol and tool server security including inventory
  requirements, allowlisting, authentication enforcement, manifest integrity checking,
  and runtime substitution detection.

* **Prompt Injection Classification and Sanitization:**
  V3.10 formalizes controls for classifying untrusted input sources, sanitizing
  content before prompt inclusion, detecting injection patterns, and bounding context
  size to prevent token-stuffing and context overflow attacks.

* **Model Supply Chain Integrity:**
  V4.5 requires approved registry sourcing, cryptographic digest pinning for model
  references, and explicit risk assessment for externally hosted model endpoints.

* **Agentic Release Assurance and Change Control:**
  V4.4 establishes that AI agents cannot approve their own outputs, cannot trigger
  production deployments without human approval gates, and that agent permission
  changes require designated security owner sign-off.

* **Adversarial Testing Requirements:**
  V4.8 adds requirements for prompt injection testing, jailbreak testing, and
  sensitive data extraction testing prior to production deployment, with documented
  cadence and SLA-tracked remediation.

* **Agent Observability and Blast Radius Safeguards:**
  V5.3 and V5.4 introduce logging requirements for agent actions, inter-agent
  communications, and secret access attempts, alongside runtime controls for rate
  limiting, irreversible action gating, and anomaly detection.

* **AIBOM Drift and Runtime Reconciliation:**
  V5.5 requires deployed AI components to be reconciled against approved AIBOMs at
  runtime, with drift generating alerts and vulnerability feeds monitored continuously.

* **Incident Response for Agent Compromise:**
  V5.6 adds AI-specific incident response requirements including agent identity
  suspension, forensic preservation of agent activity, and compromise playbook
  exercise cadence.

---

## Community and Project Updates

* **CONTRIBUTING.md Updated:**
  The contributing guide has been overhauled with accurate file paths, correct Slack
  references, a real PR workflow, and example control submissions showing exactly
  what a well-formed contribution looks like. If you've tried to contribute before
  and found the process unclear, give it another look.

* **MAINTAINERS.md Added:**
  We've been asked regularly how to become an actual SPVS team member rather than
  just a contributor. [MAINTAINERS.md](../MAINTAINERS.md) documents the requirements,
  the application process, and what membership means in practice. The bar is real
  but the door is open.

* **SPVS Now Has a Dedicated Slack Channel:**
  Join us in [#owasp-spvs](https://owasp.slack.com/archives/C0AQW879656) on OWASP
  Slack. This is where we discuss controls, review contributions, and coordinate
  across releases. The team is active here weekly.

---

## How to Get Involved

This is a community feedback release. Getting involved is the point.

1. **Review the 1.5 controls** and open issues or PRs where you disagree, see gaps,
   or have real-world context that should inform the standard
2. **Watch for 1.6** if you have experience with TeamPCP, Axios, or similar supply
   chain attacks and want to help shape those controls
3. **Read [CONTRIBUTING.md](../CONTRIBUTING.md)** for the PR process
4. **Read [MAINTAINERS.md](../MAINTAINERS.md)** if you want a deeper role heading
   into 2.0
5. **Join [#owasp-spvs](https://owasp.slack.com/archives/C0AQW879656)** on OWASP
   Slack and introduce yourself

🤖 Why did the AI agent get rejected from the pipeline? -> It couldn't pass its own
peer review.

## Code of Conduct

We ask that all contributors to OWASP projects abide by our
[Code of Conduct](https://owasp.org/www-policy/operational/code-of-conduct).
This code outlines our expectations for behavior within the project community
and helps us maintain a welcoming and inclusive environment for all contributors.

Thank you for your interest in contributing to an OWASP project. We appreciate
your efforts to help us improve and grow our projects.
```