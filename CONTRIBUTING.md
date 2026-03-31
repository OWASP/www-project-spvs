# Contributing Guidelines

Thank you for your interest in contributing to SPVS. We welcome all contributions and appreciate your efforts to improve the standard.

## Contributing to SPVS

### Types of Contributions

- **New controls:** Proposing a control that does not exist in the current standard
- **Control edits:** Corrections to existing controls (wording, mappings, level assignment)
- **Documentation:** README, contributing guide, or other non-control content

### How to Submit

1. Fork this repository and create a branch named descriptively (e.g., `add-sbom-verification-control`, `fix-v1.1.3-nist-mapping`).

2. Add your proposed control(s) to `1.0/OWASP_SPVS_1.0_-en_Requirements.csv`. Keep the column order and formatting consistent with existing rows. If you're unsure of the category, pick the closest one and note it in your PR.

3. Open a pull request against the `main` branch. For new controls, your description should address:
   - What the control verifies
   - Which pipeline phase it belongs to and why
   - The threat or risk it addresses (OWASP CICD Top 10 reference preferred)
   - Suggested level (1 = baseline, 2 = standard, 3 = advanced) with rationale
   - NIST 800-53, OWASP CICD Risk, and CWE mappings (best effort is fine)

4. If you're proposing something that doesn't fit cleanly into an existing category, say so in the PR. That's useful signal for the maintainers.

### Numbering Rules

- New controls must be placed at the end of their sub-category
- Deleted controls must retain a placeholder row to prevent number reuse

### Change Tags

Add the appropriate tag before the requirement description when modifying existing controls:

- `[ADDED]` - New requirement (end of sub-category only)
- `[ADDED, SPLIT FROM x.y.z]` - New requirement split from an existing one
- `[MODIFIED]` - Requirement description has changed
- `[MOVED FROM x.y.z]` - Requirement moved to a different sub-category, not modified
- `[MODIFIED, MOVED FROM x.y.z]` - Requirement modified and moved
- `[MOVED TO x.y.z]` - Placeholder; requirement moved to another category
- `[DELETED]` - Placeholder; requirement removed
- `[DELETED, MERGED TO x.y.z]` - Placeholder; requirement merged into another
- `[LEVEL L1 > L2]` - Requirement level has changed

CWE and NIST mapping changes do not require tags.

### Example: New Control Submission

**CSV row being added:**
```
V3,Integrate (CI*),V3.4,Integrity of Artifacts,V3.4.3,Verify that a Software Bill of Materials (SBOM) is generated and stored as a signed pipeline artifact on every build,,,X,NIST 800-53: SA-12,CICD-SEC-3,CWE-1104;CWE-345,Use of Unmaintained Third Party Components;Insufficient Verification of Data Authenticity - SBOM integrity
```

**PR description:**

> **What this verifies:** That every build produces a machine-readable SBOM (e.g., CycloneDX or SPDX format) and that it's cryptographically signed alongside the build artifact.
>
> **Why this belongs in SPVS:** SBOM generation is currently implied by V2.6 (dependency auditing) and V3.4 (artifact integrity) but never explicitly required as a pipeline output. Without it, downstream consumers can't verify what's in a release.
>
> **Threat:** CICD-SEC-3. If a build-time dependency is compromised, the SBOM gives you the data to scope the blast radius.
>
> **Level:** Proposing L3. Most orgs aren't doing signed SBOMs yet. Open to L2 if the community disagrees.
>
> **Mappings:** NIST SA-12, CICD-SEC-3, CWE-1104, CWE-345.

---

Questions before you open a PR? Join [#owasp-spvs](https://owasp.slack.com/archives/C0AQW879656) on OWASP Slack.

## Code of Conduct

All contributors are expected to abide by the [OWASP Code of Conduct](https://owasp.org/www-policy/operational/code-of-conduct).