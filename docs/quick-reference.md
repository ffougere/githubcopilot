# Quick Reference Guide - GH-300 Certification

## Common CodeQL Commands

```bash
# Initialize CodeQL database
codeql database create /path/to/database --language=javascript

# Run analysis
codeql database analyze /path/to/database \
  --format=sarif-latest \
  --output=/path/to/results.sarif \
  codeql/javascript-queries

# View results
codeql database interpret-results /path/to/database \
  --format=csv \
  --output=/path/to/results.csv

# Run specific query
codeql query run /path/to/query.ql \
  --database=/path/to/database

# Test custom query
codeql test run /path/to/test
```

## GitHub CLI Commands for Security

```bash
# List code scanning alerts
gh api repos/{owner}/{repo}/code-scanning/alerts

# Get specific alert
gh api repos/{owner}/{repo}/code-scanning/alerts/{alert_number}

# Update alert state
gh api repos/{owner}/{repo}/code-scanning/alerts/{alert_number} \
  -X PATCH \
  -f state=dismissed \
  -f dismissed_reason=false_positive

# List secret scanning alerts
gh api repos/{owner}/{repo}/secret-scanning/alerts

# List Dependabot alerts
gh api repos/{owner}/{repo}/dependabot/alerts

# Enable secret scanning
gh api repos/{owner}/{repo} \
  -X PATCH \
  -f security_and_analysis[secret_scanning][status]=enabled

# Enable push protection
gh api repos/{owner}/{repo} \
  -X PATCH \
  -f security_and_analysis[secret_scanning_push_protection][status]=enabled
```

## REST API Endpoints

### Code Scanning
- `GET /repos/{owner}/{repo}/code-scanning/alerts`
- `GET /repos/{owner}/{repo}/code-scanning/alerts/{alert_number}`
- `PATCH /repos/{owner}/{repo}/code-scanning/alerts/{alert_number}`
- `GET /repos/{owner}/{repo}/code-scanning/analyses`
- `POST /repos/{owner}/{repo}/code-scanning/sarifs`

### Secret Scanning
- `GET /repos/{owner}/{repo}/secret-scanning/alerts`
- `GET /repos/{owner}/{repo}/secret-scanning/alerts/{alert_number}`
- `PATCH /repos/{owner}/{repo}/secret-scanning/alerts/{alert_number}`
- `GET /orgs/{org}/secret-scanning/alerts`

### Dependabot
- `GET /repos/{owner}/{repo}/dependabot/alerts`
- `GET /repos/{owner}/{repo}/dependabot/alerts/{alert_number}`
- `PATCH /repos/{owner}/{repo}/dependabot/alerts/{alert_number}`

### Security Advisories
- `GET /repos/{owner}/{repo}/security-advisories`
- `POST /repos/{owner}/{repo}/security-advisories`
- `PATCH /repos/{owner}/{repo}/security-advisories/{ghsa_id}`

## Important Files and Locations

### Repository Files
- `.github/workflows/` - GitHub Actions workflows
- `.github/dependabot.yml` - Dependabot configuration
- `.github/codeql/` - Custom CodeQL configuration
- `SECURITY.md` - Security policy
- `.github/CODEOWNERS` - Code ownership (can include security team)

### CodeQL Directories
- `qlpacks/` - Custom query packs
- `queries/` - Custom queries
- `.codeql/` - CodeQL configuration

## Alert States

### Code Scanning
- `open` - Active alert
- `dismissed` - Dismissed by user
- `fixed` - Automatically closed (code changed)

### Secret Scanning
- `open` - Active alert
- `resolved` - User marked as resolved

### Dependabot
- `auto_dismissed` - Automatically dismissed
- `dismissed` - User dismissed
- `fixed` - Dependency updated
- `open` - Active alert

## Severity Levels

From highest to lowest:
1. **Critical** - Immediate action required
2. **High** - Prompt action required
3. **Medium** - Should be addressed
4. **Low** - Minor issue
5. **Note** - Informational
6. **Warning** - Potential issue

## Common Dismissal Reasons

### Code Scanning
- `false positive` - Not a real issue
- `won't fix` - Accepted risk
- `used in tests` - Test code only

### Secret Scanning
- `false_positive` - Not a real secret
- `wont_fix` - Accepted risk
- `revoked` - Secret has been revoked
- `used_in_tests` - Test secret only
- `pattern_deleted` - Custom pattern removed
- `pattern_edited` - Custom pattern modified

## Security Manager Permissions

Organization security managers can:
- View security alerts across all repositories
- Manage security settings for repositories
- Configure organization security settings
- Access security overview
- Cannot push code or manage repository settings

## Branch Protection Rules for Security

Recommended settings:
```yaml
required_status_checks:
  - CodeQL
  - Dependency Review
  - Secret Scanning

required_pull_request_reviews:
  required_approving_review_count: 1
  require_code_owner_reviews: true

enforce_admins: true
```

## Custom Secret Pattern Syntax

```regex
# Basic pattern (case-insensitive by default)
MyAPI-[A-Z0-9]{32}

# With word boundaries
\bAPI_KEY_[a-zA-Z0-9]{40}\b

# Multiple formats
(?:key|token|secret)[:=]\s*['""]?[A-Za-z0-9+/=]{32,}['""]?

# With negative lookahead (exclude false positives)
(?!.*test)MY_SECRET_[A-Z0-9]{20}
```

## Environment Variables

Common environment variables for GitHub Actions:
- `GITHUB_TOKEN` - Automatic token for API calls
- `GITHUB_REPOSITORY` - Owner/repo name
- `GITHUB_SHA` - Commit SHA
- `GITHUB_REF` - Branch or tag ref
- `GITHUB_WORKSPACE` - Working directory

## Rate Limits

- **REST API**: 5,000 requests/hour (authenticated)
- **GraphQL API**: 5,000 points/hour
- **Code Scanning**: Varies by plan
- **Secret Scanning**: No explicit limit

## Key Concepts

### SARIF (Static Analysis Results Interchange Format)
- Standard format for security tool output
- JSON-based
- Supported by many security tools
- Required for custom tool integration

### CVE (Common Vulnerabilities and Exposures)
- Standardized identifier for vulnerabilities
- GitHub can assign CVEs for repository advisories
- Format: CVE-YYYY-NNNNN

### CVSS (Common Vulnerability Scoring System)
- Scores 0-10
- Used to determine severity
- Factors: Impact, exploitability, scope

### CWE (Common Weakness Enumeration)
- Classification of software weaknesses
- Used by CodeQL and other tools
- Example: CWE-89 (SQL Injection)

## Quick Tips

1. **CodeQL runs faster** with smaller codebases - use path filters
2. **Secret scanning** scans entire git history - be patient
3. **Dependabot** can create many PRs - use grouping
4. **Push protection** can be bypassed - monitor bypass logs
5. **Custom patterns** support dry-run mode - test before enabling
6. **SARIF uploads** have size limits - filter results if needed
7. **API rate limits** apply - implement backoff strategies
8. **Security overview** updates periodically - not real-time

## Keyboard Shortcuts

In GitHub UI:
- `g` then `s` - Go to security tab
- `?` - Show keyboard shortcuts
- `/` - Focus search bar

## Common Mistakes to Avoid

1. Not excluding test files from CodeQL
2. Forgetting to enable push protection
3. Ignoring Dependabot security updates
4. Not triaging alerts regularly
5. Dismissing alerts without investigation
6. Not documenting security processes
7. Overlooking organization-level settings
8. Not monitoring the security overview

## Exam Day Checklist

- [ ] Review all security features
- [ ] Practice with API and CLI
- [ ] Understand workflow configurations
- [ ] Know dismissal reasons
- [ ] Understand severity levels
- [ ] Review CodeQL query syntax
- [ ] Practice custom secret patterns
- [ ] Review organization security settings
- [ ] Understand advisory workflow
- [ ] Review best practices
