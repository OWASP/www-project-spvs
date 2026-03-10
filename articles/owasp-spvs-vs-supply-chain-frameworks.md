![SPVS-vs-Others](https://github.com/user-attachments/assets/b5037095-1809-4ff8-aa3e-26e464202e02)

# OWASP SPVS vs. Other Supply Chain Frameworks

## A Crowded Landscape With Different Focuses

Supply chain security has no shortage of frameworks. SLSA, S2C2F, SCVS, SCITT, NIST C-SCRM... each one addresses real problems and does its job well.

But each has a specific scope. When I sit down with a DevOps team and ask "show me how you verify your pipeline security end-to-end," the answer often involves piecing together multiple frameworks.

That's why Cameron Walters and I created OWASP SPVS, the Secure Pipeline Verification Standard.

SPVS isn't meant to replace the other frameworks. It has a different scope. Here's how they compare.

## The Existing Frameworks

**SLSA (Supply-chain Levels for Software Artifacts)** Focused on build integrity and provenance. SLSA helps you prove that artifacts were built as expected with cryptographic evidence. It's essential for software producers and does this job well. Its scope is intentionally focused on the build and artifact layer.

**S2C2F (Secure Supply Chain Consumption Framework)** Microsoft's framework for securely consuming open-source dependencies. It covers ingestion, inventory, scanning, and updating of OSS packages. If you're managing OSS at scale, S2C2F provides a solid maturity model for that specific problem.

**SCVS (Software Component Verification Standard)** OWASP's standard for component verification and SBOM generation. Strong for procurement and supplier evaluation. It's designed to be component-centric, which makes it valuable for supply chain transparency and vendor assessments.

**SCITT (Supply Chain Integrity, Transparency and Trust)** An IETF standard for transparency infrastructure. It defines how to build append-only ledgers and cryptographic receipts for supply chain claims. Think of it as plumbing that enables transparency across supply chains.

**NIST C-SCRM (SP 800-161r1)** Enterprise guidance for supply chain risk management. Essential for governance and policy, operating at the organizational level. It helps leadership build C-SCRM programs and integrate supply chain risk into enterprise decisions.

## Where SPVS Fits

SPVS has a different scope: the entire pipeline lifecycle.

| Framework | Focus                            |
| --------- | -------------------------------- |
| SLSA      | Build provenance                 |
| S2C2F     | Dependency consumption           |
| SCVS      | Component verification           |
| SCITT     | Transparency infrastructure      |
| C-SCRM    | Enterprise governance            |
| **SPVS**  | **End-to-end pipeline security** |

SPVS is organized around five stages: Plan, Develop, Integrate, Release, and Operate. It provides tiered controls for each stage, so you can assess your current maturity, identify gaps, and build a roadmap.

Think of it as the ASVS for pipelines.

## How They Work Together

These frameworks complement each other:

- Use **SLSA** for build provenance (aligns with SPVS Integrate and Release stages)
- Use **S2C2F** for dependency management (feeds into SPVS Develop and Integrate)
- Use **SCVS** for component inventory and supplier evaluation
- Use **SCITT** when you need transparent, auditable supply chain records
- Use **C-SCRM** for enterprise governance
- Use **SPVS** to verify your pipeline security end-to-end

You don't have to choose one. Use what fits your priorities.

## Get Involved

SPVS 1.0 released in October 2025. We want the community to use it, challenge it, and help improve it.

What did we get right? What's missing? What doesn't work in practice?

**Check it out:**

- OWASP Project: https://owasp.org/www-project-spvs/
- GitHub: https://github.com/OWASP/www-project-spvs

Open an issue. Contribute. Tell us what you think.

------

