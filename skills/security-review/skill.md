# Security Review

Perform a security review of the **pending changes on the current branch** (the
diff against the base branch), not the entire codebase. Focus on vulnerabilities
that the change introduces or exposes.

## Scope

1. Determine the diff: `git diff <base>...HEAD` (default base: `main`/`master`).
2. Review only changed files and the code paths they touch.

## What to look for

- **Injection**: SQL, command, template, LDAP, or path traversal from untrusted input.
- **AuthN/AuthZ**: missing or weakened access checks, privilege escalation, IDOR.
- **Secrets**: hardcoded credentials, tokens, or keys; secrets logged or returned.
- **Crypto**: weak algorithms, static IVs/salts, predictable randomness.
- **Input validation**: unbounded input, deserialization of untrusted data, SSRF.
- **Output handling**: XSS, open redirects, sensitive data in responses or logs.
- **Dependencies**: newly added packages with known CVEs or excessive trust.

## Output

For each finding report:

- **Severity** (critical / high / medium / low)
- **Location** (`file:line`)
- **Description** of the vulnerability and how it could be exploited
- **Recommendation** with a concrete fix

If no security-relevant issues are found, say so explicitly rather than padding
the report. Do not flag stylistic issues — that is the job of code review.
