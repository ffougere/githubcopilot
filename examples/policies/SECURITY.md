# Security Policy

## Supported Versions

We release security updates for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| 2.x.x   | :white_check_mark: |
| 1.9.x   | :white_check_mark: |
| 1.8.x   | :x:                |
| < 1.8   | :x:                |

## Reporting a Vulnerability

We take the security of our project seriously. If you believe you have found a security vulnerability, please report it to us as described below.

### Reporting Process

**Please do not report security vulnerabilities through public GitHub issues.**

Instead, please report them via one of the following methods:

1. **GitHub Private Vulnerability Reporting** (Preferred)
   - Go to the Security tab
   - Click "Report a vulnerability"
   - Fill out the vulnerability report form

2. **Email**
   - Send an email to security@example.com
   - Include detailed information about the vulnerability
   - Provide steps to reproduce if possible

### What to Include

Please include the following information in your report:

- Type of vulnerability (e.g., SQL injection, XSS, authentication bypass)
- Full paths of source file(s) related to the vulnerability
- Location of the affected source code (tag/branch/commit or direct URL)
- Step-by-step instructions to reproduce the issue
- Proof-of-concept or exploit code (if possible)
- Impact of the vulnerability, including how an attacker might exploit it

### Response Timeline

- **Initial Response**: Within 48 hours
- **Vulnerability Confirmation**: Within 7 days
- **Fix Development**: Varies based on severity and complexity
- **Public Disclosure**: After fix is deployed and users are notified

### Security Updates

Security updates will be released as:
- **Critical**: Immediate patch release
- **High**: Patch release within 7 days
- **Medium**: Next minor release or patch
- **Low**: Next minor release

### Bug Bounty

We currently do not offer a bug bounty program, but we deeply appreciate your efforts to responsibly disclose security issues.

### Safe Harbor

We support safe harbor for security researchers who:
- Make a good faith effort to avoid privacy violations and data destruction
- Contact us before making any vulnerability information public
- Avoid exploiting the vulnerability beyond what's necessary to demonstrate it

## Security Best Practices

When using this project:

1. **Keep Dependencies Updated**
   - Regularly update to the latest version
   - Enable Dependabot alerts
   - Review and apply security updates promptly

2. **Secrets Management**
   - Never commit secrets to the repository
   - Use environment variables or secret management services
   - Enable push protection for secrets

3. **Access Control**
   - Follow principle of least privilege
   - Review and rotate access tokens regularly
   - Use organization SSO when available

4. **Code Review**
   - Enable code scanning and review alerts
   - Require security review for sensitive changes
   - Use branch protection rules

## Security Features

This project uses GitHub Advanced Security features:

- **CodeQL**: Automated code scanning for vulnerabilities
- **Secret Scanning**: Detection of exposed secrets
- **Dependabot**: Automated dependency updates
- **Dependency Review**: PR checks for vulnerable dependencies

## Acknowledgments

We thank the security community for helping us maintain the security of this project. Contributors who report valid security issues will be acknowledged (with their permission) in our security advisories.

## Contact

For any questions about this security policy, contact: security@example.com

## Version History

- v1.0 - Initial security policy (2024-01-31)
