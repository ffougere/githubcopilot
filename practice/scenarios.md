# GH-300 Practice Scenarios

## Scenario 1: Enable and Configure CodeQL

**Objective**: Set up CodeQL scanning for a multi-language repository

**Tasks**:
1. Create a CodeQL workflow file
2. Configure it to scan JavaScript and Python
3. Schedule it to run daily at 2 AM UTC
4. Configure it to run on push to main branch
5. Use security-extended query suite
6. Exclude test directories from scanning

**Expected Outcome**: CodeQL workflow successfully runs and generates security alerts

**Verification**:
- Check Actions tab for successful workflow run
- View code scanning alerts in Security tab
- Confirm test directories are excluded

---

## Scenario 2: Custom Secret Scanning Pattern

**Objective**: Create a custom pattern to detect proprietary API keys

**Tasks**:
1. Navigate to repository or organization settings
2. Create a custom secret scanning pattern
3. Pattern should detect: `MYAPI-[A-Z0-9]{32}`
4. Test the pattern with sample data
5. Configure alert notifications

**Expected Outcome**: Custom pattern detects matching secrets in repository

**Verification**:
- Push a test commit with a matching pattern
- Verify alert appears in Security tab
- Confirm notification is received

---

## Scenario 3: Dependabot Configuration

**Objective**: Configure Dependabot for automated security and version updates

**Tasks**:
1. Create `.github/dependabot.yml`
2. Enable updates for npm and pip ecosystems
3. Set schedule to weekly
4. Group patch updates together
5. Set reviewer for security updates
6. Configure commit message prefix

**Expected Outcome**: Dependabot creates PRs for outdated dependencies

**Verification**:
- Check for Dependabot PRs
- Verify update frequency matches configuration
- Confirm security updates are prioritized

---

## Scenario 4: Dependency Review in PR

**Objective**: Block PRs that introduce vulnerable dependencies

**Tasks**:
1. Create dependency review workflow
2. Configure to fail on "moderate" or higher severity
3. Enable PR comments with findings
4. Test with a PR that adds a vulnerable package
5. Verify the check fails and blocks merge

**Expected Outcome**: PR check fails when vulnerable dependencies are added

**Verification**:
- Create test PR with vulnerable dependency
- Check that status check fails
- Review comment details in PR

---

## Scenario 5: Security Advisory Creation

**Objective**: Create and publish a security advisory

**Tasks**:
1. Navigate to Security Advisories
2. Draft a new advisory
3. Fill in vulnerability details (CVE, severity, description)
4. Add affected versions and patched versions
5. Request CVE assignment
6. Publish the advisory

**Expected Outcome**: Advisory is published and CVE is assigned

**Verification**:
- Advisory appears in repository Security tab
- CVE number is assigned
- Advisory is listed on GitHub Advisory Database

---

## Scenario 6: Organization Security Overview

**Objective**: Use security overview to audit organization security

**Tasks**:
1. Navigate to organization Security tab
2. Review security overview dashboard
3. Filter for high-severity vulnerabilities
4. Export list of repositories with open alerts
5. Identify repositories without security features enabled
6. Generate compliance report

**Expected Outcome**: Comprehensive view of organization security posture

**Verification**:
- Dashboard shows all repositories
- Filters work correctly
- Export contains accurate data

---

## Scenario 7: Push Protection for Secrets

**Objective**: Enable and test push protection

**Tasks**:
1. Enable push protection for repository/organization
2. Attempt to commit a secret (e.g., AWS key)
3. Observe push protection blocking the commit
4. Learn how to bypass protection (with justification)
5. Verify secret is logged even when bypassed

**Expected Outcome**: Push is blocked when secret is detected

**Verification**:
- Commit with secret is rejected
- Clear error message is shown
- Option to bypass with reason is available

---

## Scenario 8: CodeQL Custom Query

**Objective**: Write and test a custom CodeQL query

**Tasks**:
1. Create a custom query to detect hardcoded passwords
2. Test query locally with CodeQL CLI
3. Add query to repository
4. Include query in CodeQL workflow
5. Verify query runs and produces results

**Expected Outcome**: Custom query identifies security issues

**Verification**:
- Query compiles without errors
- Results appear in code scanning alerts
- False positives are minimal

---

## Scenario 9: API Integration for Security Data

**Objective**: Use GitHub API to automate security reporting

**Tasks**:
1. Authenticate with GitHub API
2. Fetch code scanning alerts via API
3. Filter alerts by severity
4. Export to CSV or JSON format
5. Schedule automated reports

**Expected Outcome**: Automated security report generation

**Verification**:
- API calls return expected data
- Report format is correct
- Automation runs on schedule

---

## Scenario 10: Security at Scale

**Objective**: Apply security policies across multiple repositories

**Tasks**:
1. Create organization-level security policy
2. Enable security features for all repositories
3. Set up security managers role
4. Configure organization-wide Dependabot settings
5. Implement required status checks for security

**Expected Outcome**: Consistent security posture across organization

**Verification**:
- All repositories have security features enabled
- Security managers have appropriate access
- Status checks prevent merging vulnerable code

---

## Additional Practice Ideas

### Hands-On Labs:
1. Triage and dismiss false positive alerts
2. Configure SARIF upload from external tools
3. Set up GitHub Advanced Security in GitHub Enterprise Server
4. Integrate security scanning with third-party tools
5. Create security metrics dashboard

### API Exercises:
- List all code scanning alerts for an organization
- Bulk update alert states
- Create custom security reports
- Automate vulnerability tracking

### Advanced Topics:
- CodeQL query optimization
- Custom secret patterns with regex
- Supply chain security with SBOM
- Integration with SIEM tools
- Compliance reporting automation
