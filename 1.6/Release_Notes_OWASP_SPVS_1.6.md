# 1.6 RELEASE
# Release Announcement: SPVS 1.6 — Supply Chain Attack Response (Community Edition)

We're releasing SPVS 1.6 as a second community feedback edition, this time built
directly from the supply chain attacks that hit the ecosystem over the past several
months.

If your team spent time this year responding to TeamPCP, Shai-Hulud, the Axios/OpenAI
cascade, the Miasma campaign, Mastra, jscrambler, or the IDE extension breaches, this
release exists because of those incidents. We went back through what actually
happened in each one, traced the exact technique used, and wrote controls that would
have caught it or contained it.

This is not a theoretical control set. Every requirement in 1.6 traces back to a
named, real incident.

## Why This Release Exists

1.5 gave the community AI pipeline controls to react to and build on. 1.6 does the
same for supply chain attacks, because the gap was too urgent to sit on until 2.0.
Attackers moved fast this year. Worm-style propagation through package registries,
maintainer account takeovers, build stage cascades, and IDE extension compromises
all had real, dated incidents attached to them. We'd rather ship controls that
address what already happened than wait and hope 2.0's timeline covers it.

This is also a working draft. Push back on it. If you were part of incident response
on any of the attacks referenced here and think we got the control wrong, that
feedback is exactly what this release is for.

## The Roadmap

**1.6 (now):** Supply chain attack controls, mapped directly to real incidents.
Community feedback edition.

**1.7 (early September, tentative):** Likely to focus on artifacts, dependency
management, pipeline consistency, and artifact generation controls, among other
areas. Scope is still being finalized based on feedback from 1.5 and 1.6. This is
possibly our final community feedback release before 2.0.

**2.0 (October, at LASCON):** The next major release, folding together AI, supply
chain, artifact, and dependency controls from 1.5, 1.6, and 1.7 into a cohesive
standard. Cameron and Farshad will be presenting SPVS 2.0 at LASCON. Development
continues past 2.0.

If you have opinions on where 1.7 should focus, now is the time to weigh in.

# Check out SPVS 1.6!

- [SPVS 1.6 Supply Chain Controls](../1.6/OWASP_SPVS_1_6_-en_Requirements.csv)
- [SPVS 1.5 AI Controls](../1.6/OWASP_SPVS_1.5_-en_Requirements.csv)
- [SPVS 1.0 Controls for Reference](../1.6/OWASP_SPVS_1.0_-en_Requirements.csv)
- [How to Contribute to SPVS](../CONTRIBUTING.md)
- [How to Join the SPVS Team](../MAINTAINERS.md)

---

# **SPVS 1.6 Release Notes**

* **Controls Mapped to Real Incidents:**
  Every control in 1.6 is tagged with the specific attack it addresses, including
  TeamPCP, Shai-Hulud, the Axios/OpenAI cascade, Miasma, Mastra, jscrambler, the
  IDE extension breach, Tasksjacker/Polinrider, and the Drift protocol incident.
  No hypothetical threats. Every control has a receipt.

* **New Risk Metadata Model:**
  1.6 introduces threat category, incident anchor, mitigation effect (Prevent,
  Detect, Contain), risk-if-absent, severity, and attack technique fields for every
  control, alongside the existing NIST 800-53, NIST SSDF, and CWE mappings. This is
  the most detailed metadata model SPVS has shipped to date.

* **Maintainer and Publishing Account Compromise (V1.1):**
  New controls require phishing-resistant MFA on package-publishing accounts, ban
  single credentials with write access to more than one repository or package, and
  restrict organization-wide repository read access by default. Directly responds
  to the credential-based account takeovers behind jscrambler, Shai-Hulud, and the
  TeamPCP cascade.

* **Build/Sign/Publish Stage Separation (V1.2, V3.1, V3.4):**
  New controls require build, signing, and publish to run as independently managed
  stages, with held artifacts reviewed between build and publish. This directly
  targets the single-stage compromise pattern used in the TeamPCP cascade, where one
  broken stage cascaded into full build-to-publish control.

* **Developer Tool and IDE Extension Hardening (V1.3):**
  New controls address the IDE extension breach incident directly: extensions
  restricted to a centrally approved, pinned, checksummed list, auto-update
  disabled or gated, workspace trust required before any auto-execution on repo
  open, and toolchain execution isolated from host credentials.

* **Install-Time Execution Controls (V2.2, V3.1, V3.3):**
  New controls disable preinstall/postinstall scripts by default, require new
  packages to pass risk screening including install-script presence and maintainer
  count before trust, and require install/build steps to run in instrumented,
  network-restricted environments. Addresses the install-script execution vector
  used across jscrambler, Mastra, Miasma, Shai-Hulud, and the Axios/OpenAI cascade.

* **Typosquat and Slopsquat Screening (V2.2):**
  New control requires package names to be screened against known-good names before
  first resolution, with near-matches or previously unused names requiring review.
  Directly addresses name-confusion attacks, including AI-hallucinated package names.

* **Dependency Confusion and Public Registry Controls (V2.2):**
  New controls require public registry consumption through a private proxy or
  mirror, with direct public installs blocked in CI/CD.

* **Pipeline Input Injection Controls (V3.1):**
  New control prohibits untrusted external text, including branch names, commit
  messages, and PR titles, from being interpolated directly into pipeline commands.
  Responds to the script injection technique used in the TeamPCP cascade.

* **Runner and Build Environment Isolation (V3.1):**
  New controls require ephemeral or scheduled-reimage CI/CD runners, deny-by-default
  egress during dependency install and build, and pinned container base images
  verified by digest rather than tag.

* **Reusable Pipeline and Secret Scoping (V3.2):**
  New controls limit secrets in shared or reusable pipelines to the single job that
  needs them, prohibit org-wide shared secrets, and require removal of static token
  fallbacks when short-lived OIDC credentials are configured.

* **Scanning Tool Integrity (V3.3):**
  New control requires security scanning tools themselves to be integrity-checked
  before they run, directly responding to the TeamPCP vector where a compromised
  scanner marked its own malicious output as clean.

* **Artifact and Attestation Integrity (V3.4):**
  New controls require published artifacts to be automatically diffed against
  release pipeline output, signed provenance attestations binding artifacts to
  source and builder identity, stage-to-stage signature verification, shadow/orphan
  commit detection, cache content signing, attestation validation against builder
  identity and isolation state, immutable release tags, and pinned transitive
  dependencies for build actions.

* **Release Stage Credential and Blast Radius Controls (V4.1):**
  New controls prevent break-glass bypass of deployment verification without alert
  and review, prohibit carrying credentials over from earlier pipeline stages into
  release, and rate-limit and gate rapid successive publishes by a single identity.
  This last control directly addresses the worm-style propagation pattern seen in
  Shai-Hulud, Miasma, Mastra, and jscrambler, where detection alone could not outpace
  machine-speed republishing.

* **Production Traceability and Monitoring (V5.1, V5.2):**
  New controls require every production component to trace to a pinned, validated
  SBOM, monitor outbound runner traffic for unauthorized destinations, alert on
  unexpected cloud metadata/IMDS queries, flag cross-process memory reads on build
  agents, alert on unexpected package publishes, verify runtime workloads against an
  approved list, log pipeline definition changes with actor identity, and detect
  anomalous developer endpoint behavior tied to installed extensions.

* **Incident Response Credential Rotation Ordering (V5.3):**
  New control requires compromised credentials to be revoked before their
  replacement is activated during incident rotation, within a defined SLO.

---

## Community and Project Updates

* **CONTRIBUTING.md and MAINTAINERS.md remain current:**
  No changes since 1.5. If you haven't reviewed the contribution process or the
  path to joining the SPVS team, they're linked below.

* **SPVS Slack Remains Active:**
  Join [#owasp-spvs](https://owasp.slack.com/archives/C0AQW879656) on OWASP Slack.
  This is where incident-mapped controls like these get debated before they land.

---

## How to Get Involved

This is a community feedback release, same as 1.5. If you were involved in
responding to any of the incidents referenced in this control set and think we
mapped something wrong, missed a technique, or over/under-scoped a control, open
an issue or a PR.

With 1.7 tentatively landing in early September as likely our last community
feedback release, and 2.0 shipping at LASCON in October, this is the window to
shape where the standard goes next.

1. **Review the 1.6 controls** against your own incident experience
2. **Read [CONTRIBUTING.md](../CONTRIBUTING.md)** for the PR process
3. **Read [JOINING_THE_TEAM.md](../JOINING_THE_TEAM.md)** if you want a deeper role heading
   into 2.0
4. **Join [#owasp-spvs](https://owasp.slack.com/archives/C0AQW879656)** on OWASP
   Slack

🐛 Why did the worm get stopped at the registry? -> Rate limiting finally caught up
to it.

## Code of Conduct

We ask that all contributors to OWASP projects abide by our
[Code of Conduct](https://owasp.org/www-policy/operational/code-of-conduct).
This code outlines our expectations for behavior within the project community
and helps us maintain a welcoming and inclusive environment for all contributors.

Thank you for your interest in contributing to an OWASP project. We appreciate
your efforts to help us improve and grow our projects.