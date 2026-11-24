# Contributing Guidelines

Thank you for your interest in contributing to SPVS. We welcome all contributions and appreciate your efforts to improve the standard.

## Contributing to SPVS

### Types of Contributions

- **New controls:** Proposing a control that does not exist in the current standard. These go into the [community controls file](community-controls/OWASP_SPVS_Community_Controls.csv), **not** into a release.
- **Control edits:** Corrections to existing released controls (wording, mappings, level assignment)
- **Documentation:** README, contributing guide, or other non-control content

### Proposing a New Control

New controls are collected in [`community-controls/OWASP_SPVS_Community_Controls.csv`](community-controls/OWASP_SPVS_Community_Controls.csv). Approved proposals are merged there on a rolling basis. Maintainers then promote them into future releases. This keeps the published requirements stable while community ideas keep coming in.

> Do **not** add new controls to the release requirements files (`1.0/`, `2.0/`, etc.). PRs that do will be asked to move the control into the community controls file.

1. Fork this repository and create a branch named descriptively (e.g., `propose-signed-sbom-control`).

2. Open [`community-controls/OWASP_SPVS_Community_Controls.csv`](community-controls/OWASP_SPVS_Community_Controls.csv). It is split into the same stages and sub-categories as the SPVS 2.0 requirements: V1 Plan, V2 Develop, V3 Integrate, V4 Release, V5 Operate. Find the section marker row for the sub-category your control belongs in. If none fits, use the stage's `V#.NEW` section.

3. Add one row directly below that marker, after any proposals already there:
   - Copy the category and sub-category columns from the marker row
   - Set `proposal_id` to the next number in that section, e.g. `CC-V3.13-001`
   - Fill in the control name, description, level, tags, mappings, `rationale`, and `submitted_by`
   - Leave `pr_link`, `status`, and `adopted_as` blank. Maintainers fill these in.

   See the [community controls README](community-controls/README.md) for column details and an example.

4. Open a pull request against the `main` branch. One control per PR is preferred. Your description should address:
   - What the control verifies
   - Which pipeline phase it belongs to and why
   - The threat or risk it addresses (OWASP CICD Top 10 reference preferred)
   - Suggested level (1 = baseline, 2 = standard, 3 = advanced) with rationale
   - NIST 800-53, NIST SSDF, and OWASP CICD Top 10 mappings (best effort is fine)

5. If your control doesn't fit cleanly into an existing sub-category, say so in the PR. That's useful signal for the maintainers.

### Editing an Existing Control

For corrections to a released control, edit that edition's requirements file, e.g. [the 2.0 requirements CSV](2.0/OWASP_SPVS_2.0_-en_Requirements.csv). Keep the column order and formatting consistent with the existing rows, and explain the change in your PR.

### Example: New Control Submission

**CSV row added under the `V3.13 Integrity of Artifacts` section:**
```
"V3","Integrate (CI*)","V3.13","Integrity of Artifacts","CC-V3.13-001","Signed SBOM per Build","Verify that a Software Bill of Materials (SBOM) is generated and stored as a signed pipeline artifact on every build.","","","X","sbom; integrity","SA-12; SR-4","PS.3.2","CICD-SEC-3","Without a signed SBOM, downstream consumers cannot verify what is in a release or scope a compromised dependency.","your-github-handle","","",""
```

**PR description:**

> **What this verifies:** That every build produces a machine-readable SBOM (e.g., CycloneDX or SPDX format) and that it's cryptographically signed alongside the build artifact.
>
> **Why this belongs in SPVS:** SBOM generation is implied by dependency auditing and artifact integrity controls but never explicitly required as a pipeline output. Without it, downstream consumers can't verify what's in a release.
>
> **Threat:** CICD-SEC-3. If a build-time dependency is compromised, the SBOM gives you the data to scope the blast radius.
>
> **Level:** Proposing L3. Most orgs aren't doing signed SBOMs yet. Open to L2 if the community disagrees.
>
> **Mappings:** NIST SA-12, SR-4; SSDF PS.3.2; CICD-SEC-3.

### Maintainers: Promoting Controls into a Release

When preparing a new release, maintainers select `accepted` rows from the community controls file and add them to the release requirements CSV. Afterward, they set each row's `status` to `adopted` and record its new ID in `adopted_as` (e.g. `2.1: V3.13.15`). The following rules apply to release requirements files.

#### Numbering Rules

- New controls must be placed at the end of their sub-category
- Deleted controls must retain a placeholder row to prevent number reuse

#### Change Tags

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

---

Questions before you open a PR? Join [#owasp-spvs](https://owasp.slack.com/archives/C0AQW879656) on OWASP Slack.

## Code of Conduct

We ask that all contributors to OWASP projects abide by our [Code of Conduct](https://owasp.org/www-policy/operational/code-of-conduct).
This code outlines our expectations for behavior within the project community and helps us maintain a welcoming and inclusive environment for all contributors.

Thank you for your interest in contributing to an OWASP project. We appreciate your efforts to help us improve and grow our projects.
