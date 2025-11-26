# Fairness User Story Template

markdown
# Fairness-Enhanced User Story Template

## Standard Format
As a [role/stakeholder],
I want [functionality/feature]
So that [benefit/value]
Ensuring [specific fairness goal] across [protected attributes]

text

## Acceptance Criteria (FAIR Framework)

### F - Fairness Metrics Thresholds:
- [Metric 1]: [Threshold] (e.g., Demographic parity difference ≤0.05)
- [Metric 2]: [Threshold] (e.g., True positive rate parity within 0.03)
- [Metric 3]: [Threshold] (e.g., Intersectional gap ≤0.04)

### A - Auditing Requirements:
- [Audit type 1] (e.g., Counterfactual analysis for top-N decisions)
- [Audit type 2] (e.g., Red-team testing with adversarial inputs)

### I - Intersectional Analysis:
- Performance reported for key intersections: [List combinations]
- Special review process for multiply-marginalized groups: [Process]

### R - Reporting Guidelines:
- Disaggregated performance dashboard covering [groups]
- Limitation disclosure in model card addressing [constraints]
- Fairness Decision Record documenting [trade-offs/decisions]

## Example: Candidate Ranking System
As a recruiting manager, I want candidates ranked by predicted job fit
so that I can efficiently identify top prospects, ensuring equivalent
ranking accuracy across gender, race, age, disability status, and their
intersections (particularly gender × race combinations).

Acceptance Criteria (FAIR Framework):

F - Fairness Metrics:
- True positive rate parity within 0.03 across protected groups
- Demographic parity difference ≤ 0.05
- Intersectional analysis for gender × race showing ≤ 0.04 gap

A - Auditing Requirements:
- Counterfactual analysis for top-100 candidates
- Red-team testing with adversarial demographic inputs

I - Intersectional Analysis:
- Performance reported for key intersections (gender × race,
disability × age)
- Special review for multiply-marginalized groups

R - Reporting Guidelines:
- Disaggregated performance dashboard
- Limitation disclosure in model card
- Fairness Decision Record documenting trade-offs

text

## SAFE Framework Guidance

### Specific Attributes
- Identify all protected attributes relevant to the feature
- Consider intersectional combinations
- Document data collection and handling procedures

### Actionable Definition
- Define measurable fairness metrics
- Set specific threshold values
- Establish testing methodologies

### Feature Integration
- Identify where fairness should be measured in the user journey
- Define monitoring points
- Specify intervention triggers

### Expected Measures
- Document success criteria
- Define reporting requirements
- Establish review processes