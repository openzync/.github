# Security policy

## Supported versions

OpenZync 1.x receives security fixes. Fixes are released on the 1.x line and land on the default
branch of the repository concerned (`master` for `openzync-core`, `main` elsewhere). Older
pre-1.0 tags are not maintained.

| Version | Supported |
|---|---|
| 1.x | yes |
| pre-1.0 tags | no |

## Reporting a vulnerability

Email **rohnsha0@gmail.com**. Do not open a public issue, pull request, or discussion for a
suspected vulnerability: a public report points every self-hosted deployment at the weakness
before a patch exists.

Include:

- the component and version (commit SHA, image tag, or PyPI version)
- the affected endpoint, setting, or dependency
- reproduction steps or a proof of concept
- the impact you believe it has
- how you want to be credited, if at all

## What to expect

Acknowledgement is best-effort. There is no SLA, no guaranteed response time, and no bug bounty.
Once a report is reproduced, a fix is written privately and a release is coordinated with you
before disclosure. If you want a CVE reserved, say so in your first email.

## Self-hosted deployments

`openzync-core` is AGPL-3.0 and runs on your own infrastructure, where you hold the credentials
and the data. Patching a deployment is the operator's responsibility: upgrade to the release that
carries the fix and read the `CHANGELOG.md` entry for it. We have no access to your deployment and
cannot patch it for you.

## Scope

In scope: the code in the [openzync](https://github.com/openzync) organization — API and workers,
Python SDK, MCP server, dashboard, landing site, and the published images under `ghcr.io/openzync`.

Out of scope: your deployment's configuration and host hardening, third-party LLM or database
providers, and issues that require valid credentials with the privileges needed to exploit them.
