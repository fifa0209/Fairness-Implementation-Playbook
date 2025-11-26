markdown
# RACI Matrix Template for Fairness Decisions

## Overview
The RACI matrix defines clear accountability for fairness decisions across the organization. This template can be adapted for different organizational structures and decision types.

## RACI Definitions
- **Responsible (R)**: Does the work to complete the task
- **Accountable (A)**: Ultimately answerable for completion (only ONE person)
- **Consulted (C)**: Provides input before decision
- **Informed (I)**: Kept updated on progress/outcomes

## Core Fairness Decision Matrix

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| **Fairness metric selection** | Technical Fairness Lead | Chief AI Ethics Officer | Domain Specialists, Legal | All development teams |
| **Fairness threshold definition** | Domain Specialist | Chief AI Ethics Officer | Recruiting Managers, Product | Executive team |
| **Fairness-performance trade-off resolution** | Technical Fairness Lead | Chief AI Ethics Officer | AI Ethics Committee | All stakeholders |
| **High-risk system deployment approval** | Product Manager | Chief AI Ethics Officer | AI Ethics Committee, Legal | Executive team, Users |
| **Bias incident response (Critical)** | On-call engineer | Technical Fairness Lead | Chief AI Ethics Officer | CEO, Affected users |
| **Fairness intervention selection** | ML Engineer | Technical Fairness Lead | Domain Specialist | Product Manager |
| **Model card content and disclosure** | Technical writer | Domain Specialist | Legal, Technical Lead | Public/Users |
| **Compliance framework updates** | Legal/Compliance | Chief AI Ethics Officer | Technical Fairness Lead | All teams |

## Implementation Guidelines

### For Small Organizations (<50 employees)
```markdown
| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Fairness metric selection | Senior Engineer | VP Engineering | Product Manager | All teams |
| Deployment approval | Product Manager | VP Engineering | Legal (external) | Executive team |
| Bias incident response | On-call engineer | Senior Engineer | VP Engineering | All stakeholders |
For Large Enterprises (>1000 employees)
markdown
| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Fairness metric selection | Technical Fairness Lead | Chief AI Ethics Officer | Domain Specialists, Legal, Compliance | All BUs |
| Portfolio-level fairness strategy | BU Fairness Leads | Chief AI Ethics Officer | Executive Committee, Legal | All teams |
| Cross-BU fairness standards | Central CoE | Chief AI Ethics Officer | All BU Fairness Leads | Executive team |
Decision Tiers Framework
Tier 1: Strategic Decisions
Examples: Fairness principles adoption, major resource allocation, regulatory strategy

Accountable: Chief AI Ethics Officer + Executive Sponsor

Consulted: AI Ethics Committee, Legal, Executive Team

Tier 2: Tactical Decisions
Examples: System-specific fairness approaches, metric selection, intervention strategies

Accountable: Technical Fairness Lead

Consulted: Domain Specialists, Product Managers, Legal

Tier 3: Operational Decisions
Examples: Implementation details, testing approaches, monitoring configuration

Accountable: Team Fairness Champion

Consulted: Technical Lead, Domain Expert

Escalation Procedures
When to Escalate:
Decision requires resources beyond local authority

Significant fairness-performance trade-offs (>5% impact)

Potential regulatory compliance issues

Cross-team or cross-system implications

Stakeholder disagreement cannot be resolved locally

Escalation Path:
Team Level: Attempt resolution within team (24 hours)

Domain Level: Escalate to Technical Fairness Lead (48 hours)

Organizational Level: Escalate to Chief AI Ethics Officer (72 hours)

Executive Level: Escalate to AI Ethics Committee (1 week)

Best Practices
Clear Authority:
Ensure exactly ONE "Accountable" per decision type

Avoid "A by committee" which leads to decision paralysis

Document escalation paths explicitly

Effective Consultation:
Include diverse perspectives in consultation

Document consultation inputs and how they influenced decisions

Balance technical and domain expertise

Timely Communication:
Inform stakeholders at appropriate stages

Use established communication channels

Document communication in Fairness Decision Records

Regular Review:
Review RACI matrix quarterly

Update based on organizational changes

Incorporate lessons learned from decision processes

text

## templates/sprint-planning-checklist.md

```markdown
# Sprint Planning Fairness Integration Checklist

## Pre-Planning Preparation

### [ ] Review Fairness Backlog
- Review fairness backlog items from previous sprint
- Check for new fairness requirements from governance body
- Review monitoring alerts and incident reports
- Update fairness risk assessment for upcoming features

### [ ] Capacity Planning
- Confirm fairness capacity allocation (15-30% target)
- Ensure fairness champion availability
- Schedule fairness review sessions
- Allocate buffer for unexpected fairness work

## During Sprint Planning

### [ ] User Story Fairness Review
- All user stories include fairness dimensions (SAFE framework)
- Fairness acceptance criteria defined (FAIR framework)
- Intersectional considerations identified for high-risk features
- Protected attributes explicitly documented

### [ ] Task Breakdown
- Fairness tasks broken down and estimated
- Dependencies on fairness evaluation tools identified
- Testing requirements for fairness metrics specified
- Documentation tasks included

### [ ] Risk Assessment
- High-risk features flagged for special attention
- Mitigation strategies for identified fairness risks
- Contingency plans for fairness-performance trade-offs
- Escalation paths documented

## Story Review Questions

### Impact Assessment
- Does this story impact different demographic groups differently?
- What protected attributes are relevant to this feature?
- Are there intersectional considerations we're missing?

### Metric Selection
- What fairness metric is appropriate for this functionality?
- What thresholds should we set for success?
- How will we measure intersectional performance?

### Implementation Considerations
- What technical interventions might be needed?
- What data requirements exist for fairness evaluation?
- What monitoring will be implemented?

### Risk Management
- What trade-offs might emerge during implementation?
- What are the failure modes for fairness?
- What safeguards need to be implemented?

## Definition of Done (Fairness-Enhanced)

### [ ] Fairness Testing
- Disaggregated performance testing completed
- Intersectional analysis performed
- Counterfactual testing for high-stakes decisions
- Red-team testing for adversarial inputs

### [ ] Documentation
- Fairness metrics documented and within thresholds
- Model card updated with fairness properties
- Limitations documented with safeguards
- Fairness Decision Record created for major decisions

### [ ] Monitoring
- Monitoring configured for key fairness metrics
- Alert thresholds set appropriately
- Dashboards updated with new functionality
- Documentation for ongoing fairness evaluation

### [ ] Governance
- Required approvals obtained
- Stakeholders informed of changes
- Compliance evidence collected
- Deployment checklist completed

## Exit Criteria

### [ ] Completion Standards
- ≥80% of stories include explicit fairness requirements
- Fairness capacity allocation meets team target
- All high-risk stor