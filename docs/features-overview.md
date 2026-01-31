# GitHub Advanced Security Features Overview

## Introduction

GitHub Advanced Security (GHAS) is a comprehensive suite of security tools integrated into the GitHub platform. This document provides an overview of key features covered in the GH-300 certification.

## 1. Code Scanning

### What is Code Scanning?

Code scanning is an automated security testing tool that analyzes code for security vulnerabilities and coding errors.

### Key Features:

- **CodeQL Engine**: GitHub's semantic code analysis engine
- **Multi-Language Support**: JavaScript, TypeScript, Python, Java, C/C++, C#, Go, Ruby, Swift, Kotlin
- **CI/CD Integration**: Runs automatically on push, PR, or schedule
- **SARIF Support**: Accepts results from third-party tools
- **Customizable**: Use default queries or write custom ones

### CodeQL Query Suites:

1. **security-extended**: Enhanced security queries
2. **security-and-quality**: Security + code quality
3. **code-scanning**: Default for code scanning
4. **Custom**: Define your own query suite

### Best Practices:

- Run on every push to main/develop branches
- Include in PR workflows
- Schedule regular scans (e.g., daily)
- Review and triage alerts promptly
- Document false positives
- Create custom queries for org-specific patterns

## 2. Secret Scanning

### What is Secret Scanning?

Automatically detects secrets (API keys, passwords, tokens) committed to repositories.

### Types of Patterns:

1. **Partner Patterns**: Pre-defined patterns from service providers
   - Automatically notifies the provider
   - Over 200+ token types supported
   - Examples: AWS, Azure, Stripe, Slack, GitHub tokens

2. **Custom Patterns**: Organization or repository-specific
   - Define using regular expressions
   - Set dry-run mode for testing
   - Configure validity checks

### Push Protection:

- Blocks commits containing secrets
- Real-time feedback to developers
- Option to bypass with justification
- Logs all bypass attempts

### Features:

- **Historical Scanning**: Scans entire git history
- **Alert Management**: Dismiss, reopen, or mark as used-in-test
- **Notifications**: Email, webhook, or API
- **Partner Integration**: Automatic token revocation

### Best Practices:

- Enable push protection organization-wide
- Create custom patterns for internal systems
- Regularly review and remediate alerts
- Educate developers on secret management
- Use secret scanning as part of security training

## 3. Dependency Management

### Dependabot

Automated dependency updates and security vulnerability detection.

#### Components:

1. **Dependabot Alerts**
   - Notifies about vulnerable dependencies
   - Based on GitHub Advisory Database
   - Includes CVE information and severity

2. **Dependabot Security Updates**
   - Automatic PRs for security vulnerabilities
   - Prioritizes security over features
   - Tests with existing CI/CD

3. **Dependabot Version Updates**
   - Keep dependencies up-to-date
   - Configurable schedule and grouping
   - Supports 20+ package ecosystems

### Dependency Review

- PR checks for new vulnerabilities
- License compliance verification
- Supply chain risk assessment
- Blocks merge if criteria not met

### Supported Ecosystems:

- npm (JavaScript/TypeScript)
- pip (Python)
- Maven/Gradle (Java)
- NuGet (.NET)
- Composer (PHP)
- RubyGems (Ruby)
- Go modules
- Cargo (Rust)
- And many more...

### Best Practices:

- Enable Dependabot alerts for all repositories
- Configure auto-merge for minor updates
- Group related updates
- Set appropriate review requirements
- Monitor dependency review results

## 4. Security Advisories

### GitHub Security Advisories

Platform for privately discussing, fixing, and publishing information about security vulnerabilities.

### Workflow:

1. **Draft**: Create private advisory
2. **Collaborate**: Work with maintainers/reporters
3. **Fix**: Develop and test patch
4. **Request CVE**: Optional CVE assignment
5. **Publish**: Make advisory public
6. **Notify**: Alert users via Dependabot

### Features:

- **Private Forks**: Collaborate on fix privately
- **CVE Assignment**: GitHub as CVE Numbering Authority
- **Credits**: Acknowledge security researchers
- **Temporary Private Forks**: Develop fixes securely

### Security Policy (SECURITY.md)

- Documents vulnerability reporting process
- Provides contact information
- Lists supported versions
- Outlines disclosure timeline
- Explains security update process

### Best Practices:

- Maintain clear SECURITY.md
- Respond to reports within 48 hours
- Use coordinated disclosure
- Credit researchers (with permission)
- Provide clear remediation guidance

## 5. Organization Security Management

### Security Overview

Centralized dashboard for organization security.

#### Features:

- **Alert Aggregation**: All security alerts in one place
- **Filtering**: By repository, severity, type
- **Metrics**: Track security posture over time
- **Exports**: Generate compliance reports
- **Risk Assessment**: Identify high-risk repositories

### Organization Settings:

1. **Security Features**
   - Enable GHAS for all/some repositories
   - Configure default settings
   - Manage security managers

2. **Access Control**
   - Security managers role
   - Repository security settings
   - Audit log access

3. **Policies**
   - Required security features
   - Branch protection with security checks
   - Require status checks to pass

### API and Automation:

- REST API for all security features
- GraphQL API for complex queries
- Webhooks for security events
- Programmatic alert management

### Best Practices:

- Assign security managers
- Regular security overview reviews
- Automate compliance reporting
- Set organization-wide defaults
- Monitor security metrics trends

## 6. Supply Chain Security

### Software Bill of Materials (SBOM)

- Export dependency information
- SPDX format support
- Include in releases
- Compliance documentation

### Dependency Graph

- Visualize dependencies
- Track dependency usage
- Identify impact of vulnerabilities
- Export for external tools

### Best Practices:

- Enable dependency graph for all repositories
- Regularly review dependency trees
- Minimize dependency count
- Pin critical dependencies
- Monitor for supply chain attacks

## 7. Compliance and Auditing

### Audit Logs

- Track security-related actions
- API access logs
- Settings changes
- Alert management actions

### Compliance Features:

- Export security data
- Generate compliance reports
- Track remediation SLAs
- Document security processes

## 8. Integration and Extensibility

### SARIF Integration

- Upload results from external tools
- Standardized format
- View alongside CodeQL results
- Custom tool integration

### API Capabilities:

- Programmatic alert management
- Custom reporting
- Integration with SIEM
- Automated workflows

### Webhooks:

- Real-time notifications
- Security event triggers
- Custom automation
- Integration with ticketing systems

## Conclusion

GitHub Advanced Security provides a comprehensive security platform integrated into the development workflow. Understanding these features in depth is essential for the GH-300 certification and for effectively securing your organization's code and dependencies.

## Additional Resources

- [GitHub Docs: Code Security](https://docs.github.com/en/code-security)
- [CodeQL Documentation](https://codeql.github.com/)
- [GitHub Security Lab](https://securitylab.github.com/)
- [GitHub Advisory Database](https://github.com/advisories)
