# Security Policy

## Project security scope

This repository contains an offline Jupyter analysis, not a production fare service. It does not currently implement authentication, a network API, database access, or deployment infrastructure.

Security reports are still welcome for exposed credentials, unsafe repository automation, dependency vulnerabilities, or accidental publication of personal or restricted data.

## Supported version

Security fixes should target the latest state of the default `main` branch. No separate release support policy is currently defined.

## Reporting a vulnerability

Please report suspected vulnerabilities privately to the maintainer, Brajesh Kumar, through the private contact route on the GitHub profile. Do not open a public issue containing exploit details, private data, credentials, or working attack instructions.

A useful report includes:
- Affected file, workflow, dependency, or behavior.
- Impact and realistic attack scenario.
- Sanitized reproduction steps.
- Suggested mitigation, if known.

Avoid attaching raw datasets or private notebook outputs.

## Credential and data exposure

If a secret is exposed, revoke or rotate it immediately with the relevant provider. Removing a value from the latest commit does not necessarily remove it from Git history, logs, cached artifacts, or forks.

Do not commit passenger identifiers, contact details, payment data, booking references, or datasets whose license does not permit publication.

## Dependency and workflow hygiene

Use the declared dependencies in `requirements.txt`. Review dependency updates before merging. Workflows should request only the permissions they need, pin actions responsibly, and never print secrets into logs.
