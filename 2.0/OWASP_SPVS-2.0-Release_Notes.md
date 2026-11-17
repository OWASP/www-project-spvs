# 2.0 RELEASE
# Release Announcement: SPVS 2.0
We're thrilled to announce the official release of SPVS (Secure Pipeline Verification Standard) 2.0!

2.0 combines SPVS 1.0 and our two community feedback releases, 1.5 (AI and agentic pipelines) and 1.6 (supply chain attacks), into one consistent standard. Instead of three separate requirement files with different columns and overlapping controls, there is now one requirements file, one numbering scheme, and one structure across all 291 controls.

Thank you to everyone who reviewed, debated, and contributed to the community releases. A lot of what changed in 2.0 came directly from that feedback.

# Check out SPVS 2.0!
- [Check out 2.0 Controls/Requirements](OWASP_SPVS_2.0_-en_Requirements.csv)
- [How to Contribute to the SPVS](../JOINING_THE_TEAM.md)
- [How to Join the SPVS Team](../JOINING_THE_TEAM.md)
---
# **SPVS 2.0 Release Notes**

* **[Official 2.0 Requirement List Added:](OWASP_SPVS_2.0_-en_Requirements.csv)** Released the official list of 291 requirements for SPVS 2.0, organized across the same five pipeline phases introduced in 1.0.
  *One file to rule them all.*

| Phase | Requirements |
|---|---|
| V1 Plan | 64 |
| V2 Develop | 39 |
| V3 Integrate (CI) | 101 |
| V4 Release (CD) | 42 |
| V5 Operate | 45 |

* **1.0, 1.5, and 1.6 Combined:** The original 1.0 standard, the 1.5 AI controls, and the 1.6 supply chain controls are now one document. AI and supply chain controls are no longer separate add-ons. Each one has been placed in the phase and sub-category where it applies, next to the related 1.0 controls. For example, AI agent secret isolation now sits in the Integrate phase alongside pipeline credential hygiene.
  *Three CSVs walked into a bar. One walked out.*

| Source | Requirements in 2.0 |
|---|---|
| From 1.0 | 101 |
| From 1.5 | 127 |
| From 1.6 | 50 |
| New in 2.0 | 13 |

* **Categories Restructured:** Sub-categories were reorganized and renumbered so related controls are grouped together. 2.0 has 48 sub-categories across the five phases. Two new sub-categories were added: Developer Security Training (V1.2) and Transition Security (V4.6). Because of the renumbering, control IDs from 1.0, 1.5, and 1.6 have changed. Use the source traceability columns below to find where your existing controls moved.
  *Everything in its right place.*

* **Control Names Added and Refined:** Every requirement now has a short name in a new `req_name` column, alongside the full verification statement. Names are written to be readable on their own, so a control can be referenced in a ticket, audit finding, or conversation without pasting the full description. Existing control descriptions were also rewritten where wording was vague or inconsistent.
  *"Package Publish-Age Cooldown" beats "V2.6.6" in a meeting.*

* **Tags Column Added:** Every requirement now has one or more tags in a new `tags` column, such as `ai`, `ai-agent`, `secrets`, `dependencies`, `provenance`, `access-control`, and `security-scanner`. Teams can filter the standard to the controls they own. For example, filtering on `ai` returns every AI-related control across all five phases.
  *Ctrl+F finally works.*

* **Source Traceability Added:** Two new columns, `source_version` and `source_req_id`, show which release each control came from and what its original ID was. If your team already mapped your program to 1.0, 1.5, or 1.6, you can use these columns to map each control to its new 2.0 ID. Controls new in 2.0 are marked with source version 2.0.
  *Already mapped to 1.0? You can find your controls.*

* **Redundant Controls Removed:** Combining three releases created duplicates and overlaps. These were merged or retired. Examples include the scanner controls that were repeated in both Develop and Integrate in 1.0, 1.0 controls replaced by stronger and more specific versions from 1.5 or 1.6, and separate inventory controls for retrieval sources and MCP servers that are now covered by the AI asset inventory controls.
  *Goodbye, duplicates. Again.*

* **New Requirements Added:** 13 new controls were added to close gaps found while combining the releases:
  - A documented secure coding standard required by the secure development policy (V1.1.9)
  - Role-specific secure development training for developers and pipeline administrators (V1.2.1)
  - Vendor-supported IDE and editor versions with defined update timeframes (V1.6.11)
  - Dependency hash verification before use (V2.6.2)
  - A minimum publish-age cooldown before new package versions reach development or build environments (V2.6.6)
  - Secret scanning of pipeline logs after each run, including encoded secrets (V3.4.4)
  - Lint enforcement on every pull request, with findings remediated before merge (V3.7.22, V3.7.23)
  - CI/CD cache integrity verification at restore (V3.13.5)
  - Full transitive dependency pinning for external build steps and plugins (V3.13.9)
  - SBOM generation for every build, and SBOM validation that blocks deployment when the SBOM is missing or invalid (V3.13.13, V3.13.14)
  - Continuous vulnerability monitoring of production dependencies (V5.3.2)

  *Out with the gaps, in with the secure.*

* **Compliance Mappings Updated:**
  - NIST 800-53 mapped against Rev. 5, Release 5.2.0 for all 291 requirements
  - NIST SSDF (SP 800-218 v1.1) mapping added for 220 requirements
  - OWASP CI/CD Top 10 mapped for 210 requirements
  - CWE mapping removed. The 1.0 CWE mappings were inconsistent and several did not match the control they were attached to. NIST SSDF is a better fit for a pipeline standard.

  *Auditors still get their tidy mappings. Now they're accurate.*

* **Level Mappings Rebalanced Across the Full Set:** Levels were reviewed across all 291 controls so that AI, supply chain, and original 1.0 controls follow the same maturity scale. Level 1 is the baseline every team should meet, Level 2 is the standard for most organizations, and Level 3 is for advanced or high-risk environments.

| Level | Requirements |
|---|---|
| Level 1 | 85 |
| Level 2 | 146 |
| Level 3 | 60 |

  *From "getting started" to "security sorcerer," now with agents.*

* **General Clean Up:** Wording was standardized so every control follows the same "Verify that..." format. Typos were fixed, abbreviations are spelled out on first use, and formatting is consistent across the file.
  *Now it actually reads like one standard.*
---
## How to Contribute
1. **Review Project Overview:** We recommend for those who want to contribute to please review [\www-project-spvs\README.md](https://github.com/OWASP/www-project-spvs/blob/main/README.md) file
2. **How to Contribute:** Follow steps in [JOINING_THE_TEAM.md](./../JOINING_THE_TEAM.md) file
3. **Join the Team:** See [MAINTAINERS.md](./../MAINTAINERS.md) and come say hi in [#owasp-spvs](https://owasp.slack.com/archives/C0AQW879656) on OWASP Slack

We look forward to debating the changes and seeing what possible changes come forward!

🔐 Why did SPVS merge three releases into one? -> Even our controls needed least privilege.

## Code of Conduct
We ask that all contributors to OWASP projects abide by our [Code of Conduct](https://owasp.org/www-policy/operational/code-of-conduct).
This code outlines our expectations for behavior within the project community and helps us maintain a welcoming and inclusive environment for all contributors.
Thank you for your interest in contributing to an OWASP project. We appreciate your efforts to help us improve and grow our projects.