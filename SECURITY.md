# Security Policy

## Supported Versions
This project is currently under active development. Security updates are applied to the latest version only.

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |
| Older   | :x:                |

## Reporting a Vulnerability
If you discover a security vulnerability, please **do not** open a public issue. Instead, follow these steps:

1. **Contact Maintainers Privately**:  
    create a [security advisory](https://github.com/dada-io/python.io/security/advisories/new).

2. **Response Time**:  
   We aim to respond within **48 hours**. If the issue is confirmed, we will work on a fix and release a patch.

3. **Disclosure Policy**:  
   Vulnerabilities will be disclosed publicly after a patch is released, with credit to the reporter (unless requested otherwise).

## Security Practices
- **Dependencies**: This project uses GitHub Actions for CI. Dependencies are checked automatically via [Dependabot](https://docs.github.com/en/code-security/dependabot).
- **Permissions**: Workflows use least-privilege tokens (`GITHUB_TOKEN` or scoped PATs).
- **Auditing**: Markdown files are linted and checked for malicious links.

## Scope
This policy applies to:
- All `.md` files in this repository.
- GitHub Actions workflows (`.github/workflows/*.yml`).

---

*Last Updated: 25-03-2025*  
*Maintainers: @DadaNanjesha*
