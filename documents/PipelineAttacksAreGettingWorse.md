# Pipeline Attacks Are Getting Worse. Here's How to Prepare.

## The Shift Attackers Already Made

For years, attackers focused on applications. Find an injection vulnerability, exploit a misconfiguration, compromise a server.

That's changing. Attackers realized something: why hack applications one at a time when you can compromise the pipeline that builds them all?

The numbers tell the story. Sonatype tracked over 512,000 new malicious packages in 2024 alone, a 156% increase over the previous year. The total count of known malicious packages across npm, PyPI, and Maven Central now exceeds 845,000. And the attacks are getting more sophisticated.

This isn't theoretical. It's already happening.

## What Recent Attacks Teach Us

**SolarWinds (2020)** showed what's possible. Attackers compromised the build environment, injected malicious code during compilation, and distributed backdoored updates to 18,000 customers, including U.S. government agencies. The attack went undetected for nine months.

**Codecov (2021)** was simpler but equally devastating. A misconfigured Docker image let attackers modify a bash uploader script. One malicious line exfiltrated CI environment variables, including secrets, to an attacker-controlled server. Over 23,000 customers were potentially affected.

**CircleCI (2023)** introduced session hijacking. Malware on an engineer's laptop captured a session cookie, letting attackers impersonate the employee and generate production access tokens. Every customer was advised to rotate every secret.

**XZ Utils (2024)** was a multi-year social engineering campaign. An attacker built maintainer credibility over two years before injecting a backdoor that would have enabled remote code execution on most Linux systems. A Microsoft developer caught it by accident while investigating performance issues.

**tj-actions (2025)** showed how GitHub Actions supply chains cascade. Attackers compromised an upstream project, pivoted through multiple organizations, and ultimately poisoned a component used by 23,000+ repositories. The payload dumped secrets directly to public workflow logs.

Each attack exploited a different part of the pipeline. Build environments. CI/CD tools. Dependencies. Developer credentials. Maintainer trust.

## What's Coming Next

Based on current trends, here's what to expect:

**AI-enabled attacks at scale.** CrowdStrike confirmed that AI-generated malware is now operational, not theoretical. Researchers documented "slopsquatting" attacks where adversaries register package names that AI coding assistants hallucinate. When developers trust AI suggestions, they pull malicious packages.

**More GitHub Actions exploitation.** Research found over 7,000 workflows vulnerable to untrusted input injection and only 913 of 19,113 custom Actions created by verified users. The average security score for Actions in the marketplace is 4.23 out of 10. Attackers know this.

**Secrets as the primary target.** GitGuardian found 23.7 million new hardcoded secrets in public GitHub repos in 2024. Private repos are 8x more likely to contain secrets than public ones. The CircleCI, Codecov, and tj-actions attacks all succeeded primarily by harvesting credentials from CI/CD environments.

**Nation-state involvement.** The XZ Utils backdoor showed intelligence-service-level tradecraft. North Korea's Lazarus Group published 234 malicious npm and PyPI packages in 2024. State actors view open source infrastructure as strategic targets.

## How to Prepare

You can't prevent every attack, but you can make your pipeline harder to compromise and faster to recover.

**Pin dependencies to commit SHAs, not version tags.** The tj-actions attack worked because version tags were retroactively modified. Commit SHAs are immutable.

**Treat secrets like they're already compromised.** Use short-lived credentials. Rotate regularly. Never store secrets in environment variables if you can use OIDC federation instead. Scan for exposed secrets in code, logs, and collaboration tools.

**Harden your GitHub Actions workflows.** Set permissions to read-only by default. Don't use self-hosted runners with public repositories. Audit third-party Actions before using them.

**Generate SBOMs now.** The EU Cyber Resilience Act takes full effect in 2027. U.S. federal requirements are already in place. Start generating Software Bills of Materials in your CI/CD pipeline today.

**Verify your entire pipeline, not just one piece.** This is where most organizations struggle. They scan dependencies but ignore release governance. They sign artifacts but don't threat model their pipeline architecture. They monitor production but not their build environments.

Pipeline security requires end-to-end coverage: how you plan, develop, integrate, release, and operate.

## A Standard for Pipeline Security

This is why Cameron Walters and I created OWASP SPVS, the Secure Pipeline Verification Standard.

SPVS provides a comprehensive framework for verifying pipeline security across all five stages. It gives you a way to assess where you are, identify gaps, and build a roadmap for improvement.

We're not claiming SPVS prevents every attack. No framework does. But having a structured approach to pipeline security is better than piecing together controls ad hoc.

**Check it out:**

- OWASP Project: https://owasp.org/www-project-spvs/
- GitHub: https://github.com/OWASP/www-project-spvs

The attacks are getting worse. The time to prepare is now.