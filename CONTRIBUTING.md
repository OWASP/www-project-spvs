# Contributing Guidelines
## This is a Work In Progress
Thank you for your interest in contributing to an OWASP project. We welcome all contributions and appreciate your efforts to improve our projects.

## Getting Started

To get started with contributing to any OWASP project, please follow these steps:

1. [Join](http://owasp.org/slack/invite) the [OWASP Slack workspace](https://owasp.slack.com) to connect with the OWASP community and get help with any questions you may have.

2. Review the [OWASP Projects](https://owasp.org/projects/) page to browse the list of OWASP projects and find a project that aligns with your interests and skills.

3. Visit the project's individual page and repository to familiarize yourself with the project goals and objectives.

4. Fork the repository and clone it to your local machine.

5. Install any necessary dependencies and set up your development environment.

6. Make your changes and test them locally to ensure they work as expected.

7. Submit a pull request with your changes.

## Pull Request Guidelines

Before submitting a pull request, please make sure:

1. Your changes are consistent with the project's goals and objectives.

2. Your changes are well-documented and follow the project's coding standards.

3. Your changes do not introduce new bugs or break existing functionality.

4. Your changes are accompanied by tests, if applicable.

5. Your pull request includes a clear and concise description of the changes you have made.

## Code of Conduct

We ask that all contributors to OWASP projects abide by our [Code of Conduct](https://owasp.org/www-policy/operational/code-of-conduct). This code outlines our expectations for behavior within the project community and helps us maintain a welcoming and inclusive environment for all contributors.

Thank you for your interest in contributing to an OWASP project. We appreciate your efforts to help us improve and grow our projects.

**This document applies to all those who want to contritubte to this project from 2024 and may change at a future date.**

<!--

## General description

open issue > discuss, if agreed > pull request


## Versions

for what versions what kind of changes are allowed

definition of breaking change


## Opening issue

expectation from issue


## Pull-request

expectation from PR
-->

### Introduction

The current status of the SPVS project is as follows:

> The SPVS project is in a planning stage, still in phase 1 of our roadmap.


### How to make changes this project

> Once we have uploaded our inital set of standards you may contribute by opening a issue and we will dsicuss via the issues, if agreed we will need a pull request with changes.

### Standard for changes

#### Keep all current numbers

* New requirements must be placed at the end of sub-category
* Deleted requirements must keep "placeholder" to avoid some other requirements to be added/moved to that number, examples:


#### Use tags to describe the change

The following tags should be added to any modified requirement as appropriate. These tags should all be relative to how the requirement appeared in v4.0.3.

* `[ADDED]` - New requirement (should only be added at the end of a sub-section.)
* `[ADDED, SPLIT FROM x.y.z]` - New requirement which was previously part of another requirement
* `[MODIFIED]` - Requirement description has been modified
* `[MOVED FROM x.y.z]` - Requirement has been moved to a different sub-section but **not** modified. (should only be added at the end of a sub-section.)
* `[MODIFIED, MOVED FROM x.y.z]` - Requirement description has been modified **and** requirement has been moved to a different sub-section.
* `[MOVED TO x.y.z]` - Placeholder to keep number, requirement has been moved to another category (but not modified).
* `[DELETED]` - Placeholder to keep number, requirement has been deleted
* `[DELETED, MERGED TO x.y.z]` - Placeholder to keep number, requirement has been merged into another requirement, e.g. to solve a duplicate
* `[LEVEL L1 > L2]` - Requirement's level has changed

CWE and/or NIST mapping changes do not require labels.

Tags must be placed before verification description, example:

```
| **12.4.2** | [MODIFIED] Verify that files obtained from untrusted sources are scanned by antivirus scanners to prevent upload and serving of known malicious content. | ✓ | ✓ | ✓ | 509 |
```