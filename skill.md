# SOC 2 Policy Generation Skill

## Overview
This skill enables automated generation of SOC 2-compliant security policies aligned with the Trust Services Criteria (TSC). It produces professional, audit-ready policies covering all 24 essential SOC 2 policy requirements with proper structure, controls, and implementation guidance.

## When to Use This Skill
- Client preparing for SOC 2 Type I or Type II audit
- Organization needs to establish or update security policy framework
- Compliance gap analysis identifies missing policies
- Audit remediation requires policy documentation
- Annual policy review and update cycles

## Trust Services Criteria Mapping
SOC 2 policies map to five Trust Services Criteria:
- **Security (CC)**: Common Criteria - foundational security controls
- **Availability (A)**: System uptime and performance
- **Processing Integrity (PI)**: Accurate, timely, authorized processing
- **Confidentiality (C)**: Protection of confidential information
- **Privacy (P)**: Collection, use, retention, disclosure of personal information

## Complete SOC 2 Policy Set (24 Policies)

### Core Security Policies
1. **Information Security Policy** - Overarching security program (CC1.1, CC1.2)
2. **Access Control Policy** - User access management (CC6.1, CC6.2, CC6.3)
3. **Password Policy** - Authentication standards (CC6.1)
4. **Encryption Policy** - Data protection at rest and in transit (CC6.7)
5. **Physical Security Policy** - Facility and asset protection (CC6.4)

### Operational Policies
6. **Change Management Policy** - System change controls (CC8.1)
7. **Incident Response Management Policy** - Security event handling (CC7.3, CC7.4)
8. **Logging and Monitoring Policy** - Audit trail requirements (CC7.2)
9. **Backup Policy** - Data recovery procedures (A1.2)
10. **Business Continuity Policy** - Operational resilience (A1.1, A1.2)
11. **Disaster Recovery Policy** - Emergency response (A1.3)

### Data Protection Policies
12. **Data Classification Policy** - Information sensitivity levels (C1.1, C1.2)
13. **Confidentiality Policy** - Protected data handling (C1.1)
14. **Acceptable Use Policy** - Employee technology usage (CC1.4)
15. **Email/Communication Policy** - Secure communications (CC6.6, C1.2)
16. **Remote Access Policy** - Secure remote work (CC6.6, CC6.7)

### Governance Policies
17. **Risk Assessment and Mitigation Policy** - Risk management program (CC3.1, CC3.2)
18. **Vendor Management Policy** - Third-party risk (CC9.1, CC9.2)
19. **Code of Conduct Policy** - Employee behavior standards (CC1.4)
20. **Software Development Lifecycle Policy** - Secure development (CC8.1, PI1.3)

### Supplementary Policies
21. **Security Policy** - General security requirements (CC1.1)
22. **Network Security Policy** - Network controls (CC6.6)
23. **Asset Management Policy** - Asset inventory and control (CC6.5)
24. **Security Awareness Training Policy** - Employee education (CC1.4)

## Prerequisites

### Required Information from Client
```python
client_info = {
    "company_name": "Acme Corporation",
    "industry": "SaaS/Technology",
    "soc2_type": "Type II",  # Type I or Type II
    "trust_criteria": ["Security", "Availability", "Confidentiality"],
    "employee_count": 50,
    "data_types": ["Customer data", "PII", "Payment card data"],
    "infrastructure": "AWS/GCP/Azure",
    "compliance_frameworks": ["SOC 2", "ISO 27001", "GDPR"],
    "audit_timeline": "Q2 2025",
    "existing_policies": ["Information Security Policy"],
    "contact": {
        "ciso": "Jane Smith",
        "dpo": "John Doe",
        "compliance_officer": "Sarah Johnson"
    }
}
```

### Required Tools
- Document creation capability (docx/pdf)
- Version control system
- SOC 2 control matrix reference
- Industry-specific regulatory requirements database

## Policy Generation Process

### Step 1: Requirements Analysis
```python
def analyze_requirements(client_info):
    """
    Determine which policies are required based on:
    - Trust Services Criteria selected
    - Industry regulations
    - Infrastructure type
    - Data sensitivity
    """
    required_policies = []
    
    # All SOC 2 audits require these core policies
    core_policies = [
        "Information Security Policy",
        "Access Control Policy",
        "Password Policy",
        "Incident Response Management Policy"
    ]
    
    # Add criteria-specific policies
    if "Availability" in client_info["trust_criteria"]:
        required_policies.extend([
            "Business Continuity Policy",
            "Disaster Recovery Policy",
            "Backup Policy"
        ])
    
    if "Confidentiality" in client_info["trust_criteria"]:
        required_policies.extend([
            "Data Classification Policy",
            "Confidentiality Policy",
            "Encryption Policy"
        ])
    
    return list(set(core_policies + required_policies))
```

### Step 2: Policy Template Selection

Each policy follows this standardized structure:

```markdown
# [Policy Name]

## Document Control
- **Policy Owner**: Chief Information Security Officer
- **Approved By**: CEO / Board of Directors
- **Effective Date**: [Date]
- **Last Reviewed**: [Date]
- **Next Review**: [Date + 1 year]
- **Version**: 1.0
- **Classification**: Internal

## Purpose
[Why this policy exists - 2-3 sentences]

## Scope
This policy applies to:
- All employees, contractors, and third parties
- All systems, applications, and data
- All geographic locations

## Policy Statement
[Core policy requirements - 5-8 statements]

## Roles and Responsibilities

### Chief Information Security Officer (CISO)
- Overall policy accountability
- Annual policy review and approval

### IT Security Team
- Policy implementation
- Control monitoring and reporting

### Department Managers
- Ensure team compliance
- Report violations

### All Employees
- Comply with policy requirements
- Report security incidents

## Policy Details

### [Section 1]
Detailed requirements and procedures

### [Section 2]
Implementation guidance

## Exceptions
Exceptions to this policy must be:
- Documented in writing
- Approved by CISO
- Reviewed annually

## Compliance
Non-compliance may result in:
- Disciplinary action
- Termination of employment
- Legal action

## Related Policies
- [Related Policy 1]
- [Related Policy 2]

## References
- SOC 2 Trust Services Criteria: [Specific controls]
- NIST CSF: [Framework reference]
- ISO 27001: [Control reference]

## Revision History
| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | YYYY-MM-DD | CISO | Initial release |

## Approval

**Approved By**:
___________________________
[Name], [Title]
Date: _______________
```

### Step 3: Control Mapping Integration

```python
# SOC 2 Trust Services Criteria Control Mapping
TSC_CONTROLS = {
    "Access Control Policy": {
        "controls": ["CC6.1", "CC6.2", "CC6.3"],
        "requirements": [
            "Logical access controls restrict unauthorized access",
            "New users provisioned with appropriate authorization",
            "User access removed upon termination",
            "User access reviewed periodically"
        ]
    },
    "Encryption Policy": {
        "controls": ["CC6.7"],
        "requirements": [
            "Data encrypted in transit using TLS 1.2+",
            "Data encrypted at rest using AES-256",
            "Encryption key management procedures defined"
        ]
    },
    "Incident Response Management Policy": {
        "controls": ["CC7.3", "CC7.4", "CC7.5"],
        "requirements": [
            "Security incidents detected and reported",
            "Incident response plan documented and tested",
            "Lessons learned documented post-incident"
        ]
    }
}
```

### Step 4: Industry-Specific Customization

```python
INDUSTRY_CUSTOMIZATIONS = {
    "Healthcare": {
        "additional_policies": ["HIPAA Privacy Policy", "PHI Handling Policy"],
        "data_classification": ["PHI", "ePHI", "Research Data"],
        "retention_requirements": "HIPAA: 6 years minimum"
    },
    "Financial Services": {
        "additional_policies": ["PCI DSS Policy", "Anti-Money Laundering Policy"],
        "data_classification": ["Cardholder Data", "Sensitive Authentication Data"],
        "retention_requirements": "PCI DSS: 1 year minimum"
    },
    "SaaS/Technology": {
        "additional_policies": ["Secure SDLC Policy", "API Security Policy"],
        "data_classification": ["Customer Data", "Source Code", "API Keys"],
        "retention_requirements": "Per customer contract"
    }
}
```

## Detailed Policy Examples

### Example 1: Access Control Policy (Complete)

<example description="SOC 2 Access Control Policy - Production Ready">
```markdown
# Access Control Policy

## Document Control
- **Policy Owner**: Chief Information Security Officer
- **Approved By**: CEO
- **Effective Date**: January 1, 2025
- **Last Reviewed**: January 1, 2025
- **Next Review**: January 1, 2026
- **Version**: 1.0
- **Classification**: Internal

## Purpose
This Access Control Policy establishes requirements for managing access to Acme Corporation's information systems, applications, and data to prevent unauthorized access and ensure the principle of least privilege is maintained across all systems.

## Scope
This policy applies to:
- All employees, contractors, consultants, and third-party users
- All information systems, applications, databases, and network resources
- All access methods including on-premise, cloud, and remote access
- All geographic locations and business units

## Policy Statement

Acme Corporation requires that:
1. Access to systems and data is granted based on business need and least privilege principle
2. User accounts are uniquely assigned and not shared between individuals
3. Access rights are reviewed quarterly and adjusted based on role changes
4. Access is promptly revoked upon termination or role change
5. Privileged access requires additional approval and monitoring
6. All access attempts are logged and monitored for suspicious activity
7. Multi-factor authentication (MFA) is required for all access to production systems

## Roles and Responsibilities

### Chief Information Security Officer (CISO)
- Overall accountability for access control policy
- Approve privileged access requests
- Annual policy review and updates
- Report access control metrics to executive team

### IT Security Team
- Implement technical access controls
- Monitor access logs for anomalies
- Conduct quarterly access reviews
- Manage identity and access management (IAM) system

### Department Managers
- Approve access requests for team members
- Participate in quarterly access reviews
- Report role changes and terminations promptly
- Ensure team members complete security awareness training

### All Users
- Protect account credentials
- Report suspicious access attempts
- Comply with access control requirements
- Complete annual security awareness training

## Policy Details

### 1. User Account Management

**Account Creation**
- Access requests submitted via IT ticketing system
- Manager approval required for all access requests
- CISO approval required for privileged access
- Accounts created within 24 hours of approval
- Default access: read-only to required systems only

**Account Types**
- **Standard User**: Regular employee access, no administrative privileges
- **Privileged User**: Elevated access for IT administrators, requires MFA
- **Service Account**: Application-to-application authentication, key rotation every 90 days
- **Emergency Access**: Break-glass accounts, monitored and reviewed after each use

### 2. Access Provisioning Process

```
User Request → Manager Approval → Security Review → Provisioning → User Notification
     ↓              ↓                   ↓                ↓              ↓
 Ticket System   Workflow          IAM System      Auto-provision   Email/Slack
```

**Standard Access**: 
- New hire onboarding: provisioned 24 hours before start date
- Role-based access groups assigned based on department
- Default access includes: Email, Slack, HRIS, Document management

**Privileged Access**:
- CISO approval required
- Business justification documented
- Time-limited (30-90 days), reviewed for extension
- All privileged actions logged and monitored

### 3. Authentication Requirements

**Password Requirements** (see Password Policy for details):
- Minimum 12 characters
- Complexity: uppercase, lowercase, numbers, special characters
- Password expiration: 90 days
- Password history: cannot reuse last 10 passwords

**Multi-Factor Authentication (MFA)**:
- Required for all production system access
- Required for VPN/remote access
- Required for privileged accounts
- Approved MFA methods: Authenticator app, Hardware token, Biometric

### 4. Access Reviews

**Quarterly Access Reviews**:
- IT Security Team generates access reports
- Department managers review team member access
- Inappropriate access removed within 48 hours
- Review completion tracked (target: 100% completion within 2 weeks)

**Review Checklist**:
- [ ] User still employed
- [ ] Access appropriate for current role
- [ ] No excessive privileges
- [ ] MFA enabled
- [ ] Last access date recent (inactive accounts flagged)

### 5. Access Revocation

**Termination Process**:
- HR notifies IT Security via ticketing system
- All access revoked within 1 hour of termination notification
- Equipment retrieved and wiped
- Exit interview includes security obligations reminder

**Role Change**:
- Manager submits access change request
- New access provisioned before old access removed (no disruption)
- Old access removed within 24 hours of role change effective date

**Account Inactivity**:
- Accounts inactive >90 days: disabled
- Accounts inactive >180 days: deleted
- Notification sent to user and manager before disabling

### 6. Privileged Access Management

**Privileged Access Requirements**:
- Separate privileged account from standard account
- Privileged sessions recorded and retained 1 year
- Privileged access reviewed monthly
- Jump boxes/bastion hosts required for production access

**Emergency Access**:
- Break-glass accounts for critical incidents
- Requires two-person authorization
- All actions logged and reviewed within 24 hours
- Post-incident report required

### 7. Third-Party Access

**Vendor/Contractor Access**:
- NDA and security agreement required
- Limited duration access (contract period only)
- Dedicated contractor accounts (no shared credentials)
- VPN with MFA required for external access
- Monthly access review

**Customer Access**:
- Self-service access via customer portal
- SSO/SAML integration required for enterprise customers
- Customer data segregation enforced

## Monitoring and Compliance

**Access Monitoring**:
- Failed login attempts: >5 failures in 15 minutes triggers alert
- Privileged access: All commands logged and reviewed weekly
- Off-hours access: Flagged for review
- Geographic anomalies: Access from unusual locations requires verification

**Compliance Metrics**:
- Quarterly access review completion rate: Target 100%
- MFA adoption rate: Target 100%
- Access provisioning time: Target <24 hours
- Access revocation time (termination): Target <1 hour

## Exceptions

Exceptions to this policy must be:
1. Submitted in writing via security exception request form
2. Include business justification and risk assessment
3. Approved by CISO
4. Documented in exception register
5. Time-limited (maximum 90 days)
6. Reviewed monthly
7. Compensating controls implemented where possible

**Valid Exception Scenarios**:
- Legacy system incompatible with MFA (requires compensating controls)
- Emergency incident response requiring immediate access
- Regulatory auditor requiring specific access

## Non-Compliance

Violations of this policy may result in:
- Verbal/written warning
- Mandatory security training
- Suspension of access privileges
- Termination of employment/contract
- Legal action for deliberate breaches

**Common Violations**:
- Sharing passwords or accounts
- Accessing systems without authorization
- Failing to report access issues
- Circumventing access controls

## Related Policies
- Password Policy
- Information Security Policy
- Remote Access Policy
- Incident Response Management Policy
- Acceptable Use Policy

## References
- **SOC 2 TSC**: CC6.1 (Logical Access Controls), CC6.2 (User Access Provisioning), CC6.3 (User Access Removal)
- **NIST CSF**: PR.AC-1, PR.AC-4, PR.AC-7
- **ISO 27001:2022**: A.5.15, A.5.16, A.5.18, A.8.2, A.8.3
- **CIS Controls**: Control 5 (Account Management), Control 6 (Access Control Management)

## Revision History
| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-01-01 | J. Smith, CISO | Initial policy release |

## Approval

**Approved By**:

___________________________
Jane Smith, Chief Information Security Officer
Date: January 1, 2025

___________________________
John Anderson, Chief Executive Officer
Date: January 1, 2025
```
</example>

### Example 2: Incident Response Management Policy (Complete)

<example description="SOC 2 Incident Response Policy - Production Ready">
```markdown
# Incident Response Management Policy

## Document Control
- **Policy Owner**: Chief Information Security Officer
- **Approved By**: CEO
- **Effective Date**: January 1, 2025
- **Last Reviewed**: January 1, 2025
- **Next Review**: January 1, 2026
- **Version**: 1.0
- **Classification**: Confidential - Internal Use Only

## Purpose
This Incident Response Management Policy establishes the framework for detecting, responding to, recovering from, and learning from security incidents to minimize impact on Acme Corporation's operations, data, and reputation.

## Scope
This policy applies to:
- All security incidents affecting Acme Corporation systems, data, or personnel
- All employees, contractors, and third parties who may detect or respond to incidents
- All systems including on-premise, cloud, SaaS, and mobile devices
- All data breach incidents requiring regulatory notification

## Policy Statement

Acme Corporation requires that:
1. All suspected security incidents are reported immediately
2. An Incident Response Team (IRT) is maintained and trained
3. Incident severity is classified using a standardized severity matrix
4. Incidents are contained, eradicated, and recovered following documented procedures
5. Root cause analysis is performed for all major incidents
6. Lessons learned are documented and controls improved
7. Affected parties are notified per legal and contractual obligations

## Roles and Responsibilities

### Chief Information Security Officer (CISO)
- Overall accountability for incident response program
- Incident Response Team lead for major incidents
- Approve incident response procedures and updates
- Report security incidents to executive leadership and board
- Authorize external incident response support

### Incident Response Team (IRT)
- **Core Members**: CISO, IT Security Manager, IT Operations Manager, Legal Counsel
- **Extended Members**: HR Director, PR/Communications, Customer Success
- On-call rotation for 24/7 incident response
- Execute incident response playbooks
- Document all incident actions and decisions

### IT Security Team
- Monitor security alerts and SIEM
- Perform initial incident triage and classification
- Escalate incidents to IRT based on severity
- Execute containment and eradication procedures
- Conduct forensic analysis

### All Employees
- Report suspected security incidents immediately
- Cooperate with incident investigations
- Follow incident response instructions
- Complete annual security awareness training including incident reporting

## Policy Details

### 1. Incident Classification

**Severity Levels**:

**Critical (P1)**: Response time <15 minutes
- Active data breach in progress
- Ransomware affecting multiple systems
- Complete system outage affecting customers
- Confirmed APT/nation-state actor
- Public disclosure of credentials or sensitive data

**High (P2)**: Response time <1 hour
- Malware infection contained to single system
- Successful phishing attack with credential compromise
- Unauthorized access to non-critical systems
- DDoS attack causing partial service degradation
- Loss of backup integrity

**Medium (P3)**: Response time <4 hours
- Failed phishing attempt (user reported, no compromise)
- Vulnerability scan detecting high-risk findings
- Physical security breach (no data impact)
- Policy violation requiring investigation

**Low (P4)**: Response time <8 hours
- False positive security alert
- Minor policy violation
- Security awareness training failure

### 2. Incident Response Phases

```
Detection → Triage → Containment → Eradication → Recovery → Post-Incident Review
    ↓         ↓           ↓              ↓            ↓              ↓
SIEM/EDR   Classify   Isolate      Remove       Restore     Lessons Learned
Alerts      P1-P4     Systems      Threat       Systems     Control Updates
```

### 3. Detection and Reporting

**Detection Sources**:
- Security Information and Event Management (SIEM)
- Endpoint Detection and Response (EDR)
- Intrusion Detection System (IDS)
- Antivirus/Anti-malware alerts
- User reports
- Third-party notifications
- Cloud security posture management

**Reporting Channels** (24/7):
- Primary: security@acmecorp.com
- Phone: +1-555-SECURITY (monitored 24/7)
- Slack: #security-incidents channel
- IT Helpdesk: Ticket marked "SECURITY INCIDENT"

**Information to Report**:
1. Date/time incident observed
2. System(s) affected
3. Description of suspicious activity
4. Potential impact
5. Current status
6. Reporter contact information

### 4. Incident Triage Process

**Initial Assessment** (Within 15 minutes for P1):
```python
def triage_incident(incident_report):
    """
    Assess incident severity and assign response team
    """
    assessment = {
        "severity": classify_severity(incident_report),
        "systems_affected": identify_affected_systems(),
        "data_at_risk": determine_data_sensitivity(),
        "business_impact": assess_business_impact(),
        "notification_required": check_notification_requirements()
    }
    
    if assessment["severity"] in ["P1", "P2"]:
        activate_incident_response_team()
    
    return assessment
```

**Severity Classification Factors**:
- **Confidentiality Impact**: Data exposed or compromised
- **Integrity Impact**: Data modified or corrupted
- **Availability Impact**: Systems unavailable
- **Scope**: Number of systems/users affected
- **Regulatory Impact**: GDPR, HIPAA, PCI DSS breach notification required

### 5. Containment Strategy

**Short-term Containment** (Immediate):
- Isolate affected systems from network
- Disable compromised accounts
- Block malicious IPs/domains at firewall
- Preserve evidence (memory dumps, logs)
- Initiate communication tree

**Long-term Containment**:
- Implement compensating controls
- Deploy patches/updates
- Rebuild affected systems from clean backups
- Enhanced monitoring of related systems

**Containment Decision Matrix**:
| Incident Type | Containment Action | Approval Required |
|---------------|-------------------|-------------------|
| Malware | Isolate endpoint, block C2 | Security Team |
| Data Breach | Revoke access, audit logs | CISO |
| Ransomware | Shutdown affected systems, isolate backups | CISO + CTO |
| Insider Threat | Disable accounts, legal hold | CISO + Legal |

### 6. Eradication and Recovery

**Eradication Steps**:
1. Remove malware/backdoors from systems
2. Patch vulnerabilities exploited in attack
3. Reset compromised credentials (all potentially affected)
4. Review and remove unauthorized access
5. Verify system integrity before recovery

**Recovery Procedures**:
1. Restore systems from verified clean backups
2. Validate system functionality and data integrity
3. Implement enhanced monitoring (30-90 days)
4. Gradual return to production (staged approach)
5. Monitor for reinfection or persistence

**Recovery Verification Checklist**:
- [ ] All malware removed and verified clean
- [ ] Vulnerabilities patched
- [ ] Unauthorized access removed
- [ ] Logs reviewed for additional indicators
- [ ] Enhanced monitoring in place
- [ ] Users notified of password reset requirement
- [ ] Customer impact assessment complete

### 7. Communication Requirements

**Internal Communication**:
- **P1 Incidents**: Notify C-suite within 1 hour
- **All Incidents**: Incident ticket created in IRT system
- **Status Updates**: Every 2 hours for P1, daily for P2/P3
- **Stakeholder Notification**: Affected department heads

**External Communication**:
- **Customers**: If customer data affected, notify within 72 hours
- **Regulators**: Per breach notification laws (GDPR: 72 hours, state laws vary)
- **Law Enforcement**: For criminal activity (FBI, IC3)
- **Cyber Insurance**: Notify carrier per policy terms
- **Partners/Vendors**: If their systems impacted

**Communication Templates**:
- Initial notification (factual, no speculation)
- Status update (progress, timeline, actions taken)
- Final report (resolution, lessons learned, controls implemented)

### 8. Post-Incident Review

**Required Within 7 Days of Incident Closure**:

**Root Cause Analysis**:
- What happened? (Timeline of events)
- Why did it happen? (Root cause, not symptoms)
- How was it detected? (Detection effectiveness)
- What was the response time? (Metrics vs. targets)
- What worked well? (Effective controls/procedures)
- What needs improvement? (Gaps identified)

**5 Whys Technique Example**:
```
Problem: Ransomware encrypted file server
1. Why? User clicked phishing link
2. Why? Email bypassed spam filter
3. Why? Filter signatures not updated
4. Why? Auto-update disabled during maintenance
5. Why? No process to re-enable after maintenance
Root Cause: Lack of configuration change control
```

**Action Items**:
- Technical improvements (patches, config changes)
- Process improvements (procedure updates)
- Training requirements (user awareness)
- Policy updates
- Control enhancements

**Lessons Learned Report Template**:
```markdown
## Incident Summary
- Incident ID: INC-2025-001
- Date: 2025-01-15
- Severity: P1
- Duration: 4 hours (detection to resolution)

## What Happened
[Narrative description]

## Timeline
- 09:00: Initial detection (SIEM alert)
- 09:15: IRT activated
- 09:30: Containment initiated
- 12:00: Eradication complete
- 13:00: Systems restored

## Root Cause
[5 Whys analysis]

## Impact Assessment
- Systems: 3 servers affected
- Users: 50 users unable to access files (4 hours)
- Data: No data loss, 2GB encrypted (restored from backup)
- Customers: No customer impact
- Financial: $25K estimated cost (response time + consulting)

## What Went Well
- Detection within 15 minutes
- Effective containment prevented spread
- Clean backups available
- Good team communication

## Areas for Improvement
- Backup verification process
- Phishing simulation training frequency
- Email security controls
- Incident playbook clarity

## Action Items
| Action | Owner | Due Date | Status |
|--------|-------|----------|--------|
| Deploy email security enhancement | IT Security | 2025-01-30 | In Progress |
| Update backup verification procedure | IT Ops | 2025-01-20 | Complete |
| Conduct phishing simulation | CISO | 2025-02-15 | Planned |

## Attachments
- Forensic analysis report
- Communication logs
- Evidence preservation records
```

### 9. Incident Metrics and Reporting

**Key Performance Indicators (KPIs)**:
- Mean Time to Detect (MTTD): Target <15 minutes for P1
- Mean Time to Respond (MTTR): Target <1 hour for P1
- Incident closure rate: Target 95% within SLA
- False positive rate: Target <10%

**Monthly Reporting to Executive Team**:
- Total incidents by severity
- Top attack vectors
- Response time metrics
- Action item completion rate
- Training effectiveness

**Annual Reporting to Board**:
- Major incidents (P1/P2) summary
- Program maturity assessment
- Threat landscape changes
- Budget recommendations

### 10. Incident Response Training

**Required Training**:
- **All Employees**: Annual security awareness (includes incident reporting)
- **IRT Members**: Quarterly tabletop exercises
- **IT Security Team**: Monthly technical training
- **New Hires**: Security awareness within first week

**Tabletop Exercise Scenarios**:
- Ransomware attack
- Data breach with notification requirements
- Insider threat investigation
- Supply chain compromise
- DDoS attack

## Third-Party Incident Response Support

**Pre-approved Vendors**:
- Forensic investigation firm (retainer)
- Legal counsel (breach notification specialists)
- PR/crisis communication firm
- Cyber insurance carrier
- Law enforcement liaison

**Engagement Criteria**:
- P1 incidents with potential criminal activity
- Data breach affecting >1,000 records
- Advanced persistent threat (APT) suspected
- Specialized forensics required
- Legal or regulatory complexity

## Regulatory Notification Requirements

**GDPR** (If EU citizens affected):
- Notification to supervisory authority: 72 hours
- Notification to data subjects: Without undue delay
- Documentation required: Nature of breach, affected records, measures taken

**State Breach Notification Laws**:
- California (CCPA): Notify without unreasonable delay
- New York (SHIELD Act): Notify without unreasonable delay
- Other states: Review state-specific requirements

**Industry-Specific**:
- **PCI DSS**: Notify card brands and acquirer within 24-48 hours
- **HIPAA**: Notify HHS within 60 days (breaches >500 records)

## Evidence Preservation

**Chain of Custody**:
- Document all evidence handling
- Secure storage of forensic images
- Access control to evidence
- Retention: 7 years minimum

**Evidence Types**:
- System logs (SIEM, firewall, application)
- Memory dumps
- Disk images
- Network traffic captures (PCAP)
- Email communications
- Physical devices

## Exceptions

This policy allows no exceptions for:
- Reporting incidents immediately
- Activating IRT for P1 incidents
- Regulatory notification timelines

Exceptions for non-critical elements:
- Must be documented and approved by CISO
- Compensating controls required

## Compliance

**Audit Requirements**:
- Incident response plan reviewed annually
- IRT training documented
- Tabletop exercises conducted (minimum 2 per year)
- All incidents documented in ticketing system
- Post-incident reviews completed for P1/P2 incidents

**Non-Compliance Consequences**:
- Failure to report incident: Disciplinary action
- Interference with investigation: Termination
- Evidence tampering: Legal action

## Related Policies
- Information Security Policy
- Data Breach Notification Policy
- Business Continuity Policy
- Access Control Policy
- Logging and Monitoring Policy
- Vendor Management Policy

## References
- **SOC 2 TSC**: CC7.3 (Incident Management), CC7.4 (Incident Response), CC7.5 (Incident Remediation)
- **NIST CSF**: DE.AE (Anomalies and Events), RS.RP (Response Planning), RS.CO (Communications), RS.AN (Analysis), RS.MI (Mitigation)
- **NIST SP 800-61 Rev 2**: Computer Security Incident Handling Guide
- **ISO 27001:2022**: A.5.24, A.5.25, A.5.26, A.5.27
- **CIS Controls**: Control 17 (Incident Response Management)

## Revision History
| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-01-01 | J. Smith, CISO | Initial policy release |

## Approval

**Approved By**:

___________________________
Jane Smith, Chief Information Security Officer
Date: January 1, 2025

___________________________
John Anderson, Chief Executive Officer
Date: January 1, 2025

___________________________
Sarah Johnson, Legal Counsel
Date: January 1, 2025
```
</example>

## Best Practices for Policy Generation

### 1. Language and Readability
- **Use plain language**: Avoid jargon where possible
- **Reading level**: Target 10th-12th grade (use Hemingway Editor)
- **Sentence length**: Average 15-20 words
- **Active voice**: "IT Security will review access" not "Access will be reviewed"
- **Specific numbers**: "within 24 hours" not "promptly"

### 2. Control Mapping
Always include specific SOC 2 control references:
```markdown
## SOC 2 Control Mapping
- **CC6.1**: This policy addresses logical access control requirements by...
- **CC6.2**: User provisioning procedures defined in Section 4.2
- **CC6.3**: Access revocation procedures defined in Section 5.1
```

### 3. Evidence Generation
Include elements that generate audit evidence:
- Approval signatures with dates
- Version control and revision history
- Annual review requirements
- Compliance metrics and reporting
- Training completion tracking

### 4. Implementation Guidance
Don't just state requirements - provide HOW:
```markdown
### How to Implement
1. Configure SIEM to alert on failed logins >5 attempts
2. Create ServiceNow workflow for access requests
3. Schedule quarterly access reviews in calendar
4. Deploy MFA via Okta/Duo
```

### 5. Common Pitfalls to Avoid
❌ **Don't**: Vague statements like "appropriate security measures"
✅ **Do**: Specific requirements like "AES-256 encryption for data at rest"

❌ **Don't**: "Users should change passwords regularly"
✅ **Do**: "Passwords expire every 90 days with 7-day warning"

❌ **Don't**: Copy-paste generic templates without customization
✅ **Do**: Customize for client's tech stack, industry, size

### 6. Audit Readiness
Ensure policies include:
- Clear ownership (who is responsible)
- Measurable requirements (auditors can verify)
- Evidence of enforcement (metrics, reports)
- Regular review cycle (not stale)

### 7. Version Control and Distribution
```python
def manage_policy_lifecycle(policy):
    """
    Track policy through its lifecycle
    """
    lifecycle_stages = {
        "draft": {
            "status": "In Development",
            "approver": "CISO",
            "location": "SharePoint/Policies/Draft/"
        },
        "review": {
            "status": "Under Review",
            "reviewers": ["Legal", "Compliance", "Department Heads"],
            "duration": "14 days"
        },
        "approved": {
            "status": "Approved",
            "distribution": "Company-wide email, Intranet, Onboarding",
            "acknowledgment_required": True
        },
        "active": {
            "status": "In Effect",
            "review_cycle": "Annual",
            "next_review": calculate_next_review_date()
        },
        "retired": {
            "status": "Superseded",
            "retention": "7 years",
            "archive_location": "SharePoint/Policies/Archive/"
        }
    }
    return lifecycle_stages[policy.status]
```

## Output Formats

### 1. Word Document (.docx)
- Professional template with company branding
- Table of contents
- Headers/footers with policy name and version
- Approval signature section

### 2. PDF
- Locked/read-only for distribution
- Digital signatures for approved policies
- Watermark for draft versions

### 3. Web Format (HTML/Markdown)
- For intranet publishing
- Searchable and linkable
- Track user acknowledgments

### 4. Policy Management System
- Upload to GRC platform (Vanta, Sprinto, Drata)
- Link to control framework
- Automated review reminders

## Quality Assurance Checklist

Before delivering policies to client, verify:

- [ ] All placeholders replaced with client-specific information
- [ ] SOC 2 TSC controls accurately mapped
- [ ] Industry-specific requirements included
- [ ] No spelling or grammatical errors (run through Grammarly)
- [ ] Consistent formatting and numbering
- [ ] All sections complete (no "TBD" or "[Insert]")
- [ ] Roles and responsibilities clearly defined
- [ ] Measurable compliance requirements
- [ ] Related policies referenced
- [ ] Approval section includes correct names/titles
- [ ] Effective date is realistic
- [ ] Next review date calculated (typically 1 year)
- [ ] Version number consistent across document
- [ ] Document classification appropriate
- [ ] Legal review completed (if required)

## Bulk Policy Generation Script

```python
import os
from datetime import datetime, timedelta

class SOC2PolicyGenerator:
    def __init__(self, client_info):
        self.client = client_info
        self.policies = self.load_policy_templates()
        self.tsc_controls = self.load_control_mappings()
    
    def generate_all_policies(self, output_dir="policies"):
        """
        Generate complete SOC 2 policy set for client
        """
        os.makedirs(output_dir, exist_ok=True)
        
        generated_policies = []
        
        for policy_name in self.get_required_policies():
            policy_content = self.generate_policy(policy_name)
            
            # Validate policy completeness
            if self.validate_policy(policy_content):
                # Save in multiple formats
                self.save_as_docx(policy_content, output_dir)
                self.save_as_pdf(policy_content, output_dir)
                self.save_as_markdown(policy_content, output_dir)
                
                generated_policies.append(policy_name)
                print(f"✓ Generated: {policy_name}")
            else:
                print(f"✗ Failed validation: {policy_name}")
        
        # Generate index and cross-reference
        self.generate_policy_index(generated_policies, output_dir)
        
        return generated_policies
    
    def generate_policy(self, policy_name):
        """
        Generate single policy from template
        """
        template = self.policies[policy_name]
        
        # Replace placeholders
        policy = self.customize_template(template)
        
        # Add control mappings
        policy = self.add_tsc_controls(policy, policy_name)
        
        # Add industry-specific requirements
        policy = self.add_industry_requirements(policy)
        
        # Set dates
        policy = self.set_policy_dates(policy)
        
        return policy
    
    def validate_policy(self, policy):
        """
        Validate policy completeness
        """
        required_sections = [
            "Document Control",
            "Purpose",
            "Scope",
            "Policy Statement",
            "Roles and Responsibilities",
            "Policy Details",
            "Compliance",
            "Related Policies",
            "References",
            "Approval"
        ]
        
        for section in required_sections:
            if section not in policy:
                return False
        
        # Check for placeholders
        if "{{" in policy or "[Insert" in policy:
            return False
        
        return True
    
    def generate_policy_index(self, policies, output_dir):
        """
        Generate master policy index with cross-references
        """
        index = f"""
# SOC 2 Policy Framework Index
## {self.client['company_name']}

**Generated**: {datetime.now().strftime('%Y-%m-%d')}
**SOC 2 Type**: {self.client['soc2_type']}
**Trust Criteria**: {', '.join(self.client['trust_criteria'])}

## Policy Inventory

"""
        for i, policy in enumerate(policies, 1):
            index += f"{i}. {policy}\n"
        
        index += "\n## Control Mapping Matrix\n\n"
        # Add TSC control cross-reference
        
        with open(f"{output_dir}/00-Policy-Index.md", "w") as f:
            f.write(index)

# Usage Example
client_info = {
    "company_name": "Acme Corporation",
    "industry": "SaaS",
    "soc2_type": "Type II",
    "trust_criteria": ["Security", "Availability", "Confidentiality"],
    "employee_count": 50,
    "effective_date": "2025-01-01",
    "ciso_name": "Jane Smith",
    "ceo_name": "John Anderson"
}

generator = SOC2PolicyGenerator(client_info)
policies = generator.generate_all_policies(output_dir="acme_policies")

print(f"\n✓ Generated {len(policies)} policies successfully!")
```

## Maintenance and Updates

### Annual Policy Review Process
1. **Q4 Review Planning** (October)
   - Schedule review meetings
   - Assign policy owners
   - Gather incident data, audit findings, regulatory updates

2. **Policy Review** (November)
   - Each policy owner reviews assigned policies
   - Update control mappings for framework changes
   - Incorporate lessons learned from incidents
   - Update metrics and compliance requirements

3. **Stakeholder Approval** (December)
   - Legal review for regulatory changes
   - CISO approval
   - CEO/Board approval for major changes

4. **Distribution** (January)
   - Publish updated policies
   - User acknowledgment campaign
   - Training on significant changes

### Triggers for Ad-Hoc Updates
- Significant security incident
- New regulatory requirement
- Audit finding requiring policy change
- Organizational change (M&A, restructure)
- Technology stack changes

## Deliverables Package

When delivering policies to client, include:

1. **Individual Policy Documents** (24 policies)
   - Word format (editable)
   - PDF format (distribution)

2. **Policy Index and Cross-Reference**
   - Master policy list
   - TSC control mapping matrix
   - Related policy relationships

3. **Implementation Guide**
   - Rollout timeline
   - Communication templates
   - User acknowledgment process
   - Training materials

4. **Policy Management Toolkit**
   - Review schedule calendar
   - Policy exception request form
   - Policy violation report template
   - Annual review checklist

5. **Control Matrix**
   - SOC 2 TSC controls mapped to policies
   - Evidence collection guidance
   - Compliance metrics dashboard

## Resources and References

### SOC 2 Framework Documentation
- AICPA TSC: https://www.aicpa.org/interestareas/frc/assuranceadvisoryservices/trust-services-criteria
- SOC 2 Guide: https://www.aicpa.org/resources/download/soc-2-examination-guide

### Complementary Frameworks
- **NIST Cybersecurity Framework**: https://www.nist.gov/cyberframework
- **ISO 27001:2022**: Information Security Management
- **CIS Controls v8**: https://www.cisecurity.org/controls

### Industry Resources
- SANS Policy Templates: https://www.sans.org/information-security-policy/
- NIST SP 800-53: Security Control Catalog
- NIST SP 800-61: Incident Handling Guide
- NIST SP 800-171: Protecting CUI

## Conclusion

This skill enables rapid, audit-ready SOC 2 policy generation that:
- Meets Trust Services Criteria requirements
- Includes specific, measurable controls
- Provides implementation guidance
- Generates audit evidence
- Scales to client needs

The key to successful policy generation is balancing comprehensiveness with usability - policies must be detailed enough to pass audit but practical enough for organizations to implement and maintain.

## Version History
- **v1.0** (2025-01-02): Initial skill creation with complete 24-policy framework
