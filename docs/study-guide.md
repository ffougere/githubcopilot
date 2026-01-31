# GH-300 Study Guide

## Exam Overview

The GitHub Advanced Security (GH-300) certification exam tests your knowledge and skills in implementing and managing GitHub Advanced Security features.

## Core Competencies

### 1. Code Scanning and CodeQL (25-30%)

**Key Skills:**
- Configure CodeQL analysis for different languages
- Interpret code scanning results
- Triage and manage security alerts
- Write custom CodeQL queries
- Integrate code scanning into CI/CD pipelines

**Topics to Study:**
- CodeQL CLI usage
- Query suites and packs
- SARIF output format
- False positive management
- Security severity levels

### 2. Secret Scanning (20-25%)

**Key Skills:**
- Enable secret scanning for repositories and organizations
- Configure custom patterns
- Manage and remediate secret alerts
- Implement push protection
- Understand partner patterns

**Topics to Study:**
- Secret types and detection
- Alert notification workflows
- Bypassing push protection
- Historical scanning
- API integration

### 3. Dependency Security (20-25%)

**Key Skills:**
- Configure Dependabot alerts and updates
- Review dependencies in pull requests
- Manage vulnerable dependencies
- Understand supply chain security
- Work with dependency graphs

**Topics to Study:**
- Dependabot version updates vs security updates
- Dependency review action
- Package ecosystems supported
- Vulnerability databases
- SBOM generation

### 4. Security Policies and Advisories (15-20%)

**Key Skills:**
- Create comprehensive security policies
- Publish security advisories
- Coordinate CVE assignment
- Set up private vulnerability reporting
- Manage security disclosures

**Topics to Study:**
- SECURITY.md best practices
- Advisory workflow
- CVE numbering
- Coordinated disclosure
- Security tab features

### 5. Organization-Level Security Management (15-20%)

**Key Skills:**
- Configure organization security settings
- Use security overview dashboard
- Implement security policies at scale
- Integrate with security tools
- Generate compliance reports

**Topics to Study:**
- Organization security settings
- Role-based access control
- API for security data
- Webhooks for security events
- Audit logs

## Hands-On Practice

### Essential Tasks to Master:

1. **Set up CodeQL scanning for a repository**
   - Choose appropriate language queries
   - Configure scanning frequency
   - Review and triage findings

2. **Configure secret scanning with custom patterns**
   - Create custom pattern
   - Test pattern effectiveness
   - Handle alert lifecycle

3. **Manage Dependabot**
   - Enable alerts and updates
   - Configure version update strategy
   - Handle security updates

4. **Create and manage security advisories**
   - Draft an advisory
   - Request CVE
   - Publish advisory

5. **Use Security Overview**
   - Navigate organization security
   - Filter and analyze alerts
   - Generate reports

## Study Resources

- GitHub Docs: Advanced Security
- GitHub Skills learning paths
- CodeQL documentation and tutorials
- GitHub Security Lab
- GitHub Community discussions

## Exam Tips

1. **Hands-on experience is crucial** - Practice in real repositories
2. **Understand the full workflow** - From detection to remediation
3. **Know the differences** - Between organization and repository settings
4. **API familiarity** - Many tasks can be automated
5. **Best practices** - Security is about process, not just tools

## Common Pitfalls

- Confusing secret scanning partner patterns vs custom patterns
- Not understanding CodeQL query pack versioning
- Overlooking the dependency review action
- Forgetting about rate limits in API automation
- Misunderstanding push protection bypass workflows

## Next Steps

1. Complete all hands-on practices
2. Review example configurations
3. Study official documentation
4. Take practice assessments
5. Schedule your certification exam
