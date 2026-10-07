# Security Policy

RockxyBase connects to databases, holds the credentials for them in the macOS Keychain, and
runs statements against production systems. Reports about any of that are taken seriously.

## Supported versions

| Version | Supported |
|---------|-----------|
| Latest release | Yes |
| Previous release | Security fixes only |
| Older releases | No |

## Reporting a vulnerability

**Please do not open a public issue for a security vulnerability.**

Use a private [GitHub Security Advisory](https://github.com/RockxyApp/RockxyBase/security/advisories/new)
(Security tab ▸ Report a vulnerability). Please include:

- what the vulnerability is, and its impact;
- the steps to reproduce it, or a proof of concept;
- the RockxyBase version (RockxyBase ▸ About RockxyBase), the macOS version and the
  database engine involved;
- whether you would like to be credited.

Never send real credentials, connection strings or production data. Use a disposable
database you control.

## What to expect

We will acknowledge the report, keep you informed while a fix is prepared, and credit you in
the release notes unless you prefer otherwise. Please allow a reasonable time for a fix to
ship before disclosing publicly.

## Scope

In scope: the RockxyBase app — credential handling, network transport (TLS, SSH),
read-only enforcement, statement safety, file import and export, and the update mechanism.
Out of scope: vulnerabilities in the database servers themselves, and findings that need
an already-compromised Mac.
