# Sprint Planning Checklist

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
- All high-risk stories have intersectional analysis planned
- Team consensus on fairness priorities for sprint

### [ ] Risk Management
- Critical fairness risks identified and mitigated
- Escalation paths documented for trade-offs
- Contingency plans for fairness issues
- Communication plan for stakeholders

### [ ] Resource Allocation
- Fairness champion identified and available for sprint
- Necessary tools and data access confirmed
- External dependencies identified and managed
- Training needs addressed

## Post-Planning Actions

### [ ] Communication
- Update fairness backlog with carried-over items
- Communicate sprint fairness goals to stakeholders
- Schedule mid-sprint fairness checkpoints
- Prepare fairness demonstration for sprint review

### [ ] Preparation
- Set up fairness testing environments
- Prepare fairness evaluation datasets
- Configure monitoring for new functionality
- Schedule fairness review sessions

---

## Example: 2-Week Sprint Planning

### Week 1 Focus:
- Data bias audit (3 points)
- Fairness metric implementation (5 points)
- Baseline fairness evaluation (2 points)

### Week 2 Focus:
- Bias mitigation implementation (5 points)
- Intersectional testing (3 points)
- Documentation and model cards (2 points)

### Fairness Capacity: 25% (10 story points)
- Total sprint capacity: 40 points
- Fairness allocation: 10 points
- Remaining for feature work: 30 points

### Key Dependencies:
- Access to demographic data for testing
- Fairness evaluation tools availability
- Legal review for model card disclosures