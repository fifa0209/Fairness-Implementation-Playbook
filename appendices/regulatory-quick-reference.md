
## appendices/regulatory-quick-reference.md

```markdown
# Regulatory Quick Reference

## EU AI Act (High-Risk Systems)

### Applicable to
Employment, education, credit scoring, law enforcement, critical infrastructure

### Key Requirements
- Risk management system (identify, evaluate, mitigate)
- Data governance (bias examination, quality assurance)
- Technical documentation (design, development, performance)
- Record-keeping (automatically generated logs)
- Transparency (information to deployers and users)
- Human oversight (human-in-the-loop or on-the-loop)
- Accuracy, robustness, cybersecurity

### Implementation Mapping
- **Risk management** → Risk classification framework + monitoring
- **Data governance** → Fair AI Scrum (data validation checkpoints)
- **Documentation** → Fairness Decision Records + Model cards
- **Human oversight** → Governance gates + deployment approval

### Evidence Requirements
- Conformity assessment documentation
- Technical file with full system description
- Post-market monitoring reports
- CE marking preparation

## GDPR Article 22 (Automated Decision-Making)

### Applicable to
Decisions significantly affecting individuals, without human involvement

### Key Requirements
- Right not to be subject to purely automated decisions (with exceptions)
- Meaningful information about logic involved
- Right to human intervention
- Right to contest decision
- Right to explanation

### Implementation Mapping
- **Meaningful information** → Model cards with progressive disclosure
- **Human intervention** → Governance oversight, deployment approval
- **Right to contest** → Appeal process with human review
- **Explanation** → Interpretability methods (SHAP, LIME) for individual decisions

### Compliance Checklist
- [ ] Is there human oversight in the decision process?
- [ ] Can users request human review of decisions?
- [ ] Is information about the logic provided in accessible language?
- [ ] Is there an appeal/contest mechanism?
- [ ] Are explanations available for individual decisions?

## U.S. Algorithmic Accountability Laws (State-Level)

### Applicable to
Varies by state; typically employment, housing, credit

### Key Requirements (Common across states)
- Impact assessments before deployment
- Bias testing (often quarterly)
- Disparate impact analysis (80% rule)
- Documentation of testing methodologies
- Public disclosure requirements (varies)

### Implementation Mapping
- **Impact assessment** → Fairness Impact Assessment (Stage 4)
- **Bias testing** → Automated monitoring with quarterly formal audits
- **Disparate impact** → Group fairness metrics in Definition of Done
- **Documentation** → Regulatory Compliance Guide evidence collection

### 80% Rule
Selection rate for protected group ≥ 80% of selection rate for highest group

**Example**: If 50% of men are selected, ≥40% of women must be selected (50% × 0.8 = 40%)

## Canadian Algorithmic Impact Assessment (AIA)

### Applicable to
Federal government AI use (may influence private sector)

### Key Requirements
- Complete AIA questionnaire (risk scoring)
- Mitigation measures based on risk level
- Transparency: Publication of results
- Human-in-the-loop for high-impact decisions
- Recourse mechanisms
- Training for staff

### Implementation Mapping
- **AIA questionnaire** → Risk classification framework
- **Mitigation measures** → Architecture-specific interventions
- **Transparency** → Model cards, public fairness reports
- **Recourse** → Governance oversight, appeal process

### Risk Levels
- **Level I (Low)**: Minimal oversight
- **Level II (Medium)**: Some transparency and quality assurance
- **Level III (High)**: Peer review, monitoring, explanation
- **Level IV (Very High)**: All of above + algorithmic impact assessment publication

## Layered Compliance Strategy

### Shared Compliance Core
Implement to highest standard across all jurisdictions:
- **Bias Testing Frequency**: Quarterly (meets strictest requirement)
- **Fairness Impact Assessment**: Comprehensive coverage
- **Documentation**: Technical docs + model cards
- **Human Oversight**: Appropriate level for decision impact
- **Transparency**: Clear explanations of AI role

### Jurisdiction-Specific Extensions
- **EU-specific**: Annex III compliance, CE marking
- **US-specific**: State-specific disparate impact reporting
- **Canada-specific**: AIA using Treasury Board template

## Evidence Collection Framework

### Automated Evidence
- CI/CD pipeline integration for test reports
- Monitoring dashboard with automated logging
- Version-controlled Fairness Decision Records
- Requirement traceability matrices

### Manual Evidence
- Fairness Impact Assessment reports
- Model cards with limitation disclosure
- Governance meeting minutes and approvals
- Stakeholder consultation records

### Audit Preparation
- **Time to compile**: Target <5 days
- **Completeness**: 100% requirement coverage
- **Accuracy**: Evidence matches implementation
- **Accessibility**: Organized for regulator review

## Compliance Timeline

### Pre-Deployment
- Risk classification completed
- Fairness Impact Assessment conducted
- Technical documentation prepared
- Governance approvals obtained

### Post-Deployment
- Quarterly bias testing conducted
- Monitoring dashboards operational
- Incident response protocols tested
- Documentation updated regularly

### Annual Compliance
- Comprehensive regulatory review
- External audit engagement
- Compliance framework assessment
- Training program evaluation