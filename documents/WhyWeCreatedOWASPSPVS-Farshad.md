# Why We Created OWASP SPVS

## A Conference Conversation That Turned Into a Framework

In October 2023, I was at LASCON sitting in a talk about threat modeling pipelines. I started chatting with Cameron Walters. Within minutes, we realized we shared the same frustration.

We both kept asking: where's the ASVS for pipelines?

OWASP ASVS changed application security. It gave practitioners a comprehensive, verifiable standard with actionable controls. Not just a list of risks like the OWASP Top 10, but specific requirements you could test against and build a program around.

Nothing like that existed for CI/CD pipelines.

Sure, we had the OWASP Top 10 CI/CD Risks. Helpful for awareness, but broad. We had SLSA for build provenance. Important, but narrow. We had S2C2F for dependency consumption. Useful, but only one piece of the puzzle.

What we didn't have was a standard that covered the entire pipeline lifecycle: how you plan, develop, integrate, release, and operate.

That conversation became two years of work.

## What SPVS Is

The Secure Pipeline Verification Standard (SPVS) is a comprehensive framework for verifying and improving pipeline security. We released version 1.0 in October 2025.

It's organized around five stages that map to how DevOps teams actually work:

**Plan** - Threat modeling, security requirements, lessons learned from previous iterations.

**Develop** - Secure coding practices, code review, automated vulnerability detection during development.

**Integrate** - Security checkpoints, artifact integrity, environment hardening, automated testing.

**Release** - Final validations, compliance checks, change control, secure rollout.

**Operate** - Continuous monitoring, incident response, patch management, access control.

Each stage has tiered controls so you can start at your current maturity level and progress over time. Controls map to CWE, NIST, and the OWASP CI/CD Top 10.

## Why This Matters

Your CI/CD pipeline is one of the most privileged systems in your organization. It touches source code, secrets, production credentials, and deployment infrastructure.

When I ask teams to show me their pipeline security controls, they often piece together bits from different frameworks. Or they have tribal knowledge that isn't documented. Or they focus on one area (like dependency scanning) while ignoring others (like release governance).

SPVS gives you a single standard to assess against. Where are you strong? Where are the gaps? What should you prioritize next?

## We Need Your Feedback

SPVS 1.0 is out, but we're just getting started.

We want practitioners to use it, stress-test it, and tell us what's missing. What controls don't make sense? What did we overlook? What's unclear?

This is a community project. The more people who use it and contribute, the better it gets.

**Check out SPVS:**

- OWASP Project: https://owasp.org/www-project-spvs/
- GitHub: https://github.com/OWASP/www-project-spvs

Try it on your pipeline. Open an issue. Start a discussion. We're listening.

------

*Farshad Abasi is CEO of Forward Security and co-author of OWASP SPVS. He leads the OWASP Vancouver chapter.*