# SPVS Community Controls

[`OWASP_SPVS_Community_Controls.csv`](OWASP_SPVS_Community_Controls.csv) is where the community proposes new SPVS controls. It is **not part of any SPVS release**.

Approved proposals are merged here on a rolling basis. When maintainers plan a new release, they choose controls from this file and promote them into that release's requirements file. Released requirements (`1.0/`, `2.0/`, etc.) are never changed by community proposals.

## File Layout

The file uses the same stages and sub-categories as the [SPVS 2.0 requirements](../2.0/OWASP_SPVS_2.0_-en_Requirements.csv):

| Stage | Sub-categories |
|---|---|
| V1 Plan | V1.1 – V1.9, V1.NEW |
| V2 Develop | V2.1 – V2.7, V2.NEW |
| V3 Integrate (CI*) | V3.1 – V3.13, V3.NEW |
| V4 Release (CD*) | V4.1 – V4.10, V4.NEW |
| V5 Operate | V5.1 – V5.9, V5.NEW |

Each sub-category starts with a **section marker row**: its `proposal_id` is empty and its `req_name` is `-- section: add proposals below --`. Add your proposal directly below the matching marker, after any proposals already there. Do not edit or remove marker rows.

If a control doesn't fit any existing sub-category, add it under the stage's `V#.NEW` section. Put your suggested sub-category name at the start of `rationale`.

## Columns

| Column | What to enter |
|---|---|
| `category_id`, `category_name`, `sub-category_id`, `sub-category_name` | Copy these from the section marker you are adding under |
| `proposal_id` | `CC-<sub-category_id>-NNN`, using the next number in that section (e.g. `CC-V3.13-001`). Numbers are never reused. |
| `req_name` | Short control name |
| `req_description` | Starts with "Verify that ..." |
| `level 1` / `level 2` / `level 3` | `X` in the column for the proposed level (1 = baseline, 2 = standard, 3 = advanced) |
| `tags` | Semicolon-separated tags, e.g. `dependencies; integrity` |
| `NIST 800-53 ...`, `NIST SSDF ...`, `OWASP_CICD_Top10` | Mappings, best effort; semicolon-separated |
| `rationale` | Why the control is needed and which threat it addresses |
| `submitted_by` | Your GitHub handle |
| `pr_link` | Leave blank; a maintainer fills it in |
| `status` | Leave blank; a maintainer fills it in |
| `adopted_as` | Leave blank; a maintainer fills it in |

Wrap every field in double quotes, as the rest of the file does.

## Status Lifecycle

| Status | Meaning |
|---|---|
| *(blank)* | Proposed in an open PR |
| `accepted` | Approved and merged; a candidate for a future release |
| `adopted` | Promoted into a release; `adopted_as` records where (e.g. `2.1: V3.13.15`) |
| `deferred` | Reviewed during release planning and held for later |
| `rejected` | Reviewed during release planning and not adopted; reason given in `rationale` or the PR |

Rows are never deleted, so the file keeps the full history of community proposals.

## Example

```
"V3","Integrate (CI*)","V3.13","Integrity of Artifacts","CC-V3.13-001","Signed SBOM per Build","Verify that a Software Bill of Materials (SBOM) is generated and stored as a signed pipeline artifact on every build.","","","X","sbom; integrity","SA-12; SR-4","PS.3.2","CICD-SEC-3","Without a signed SBOM, downstream consumers cannot verify what is in a release or scope a compromised dependency.","your-github-handle","","",""
```

## For Maintainers: Promoting Controls into a Release

1. Select `accepted` rows to include in the new release.
2. Add each one to the release requirements CSV at the end of its sub-category, with a real `Vx.y.z` ID and the `[ADDED]` change tag (see [CONTRIBUTING.md](../CONTRIBUTING.md#maintainers-promoting-controls-into-a-release)).
3. Back in this file, set `status` to `adopted` and fill in `adopted_as`. Mark any reviewed-but-skipped rows as `deferred` or `rejected`.
