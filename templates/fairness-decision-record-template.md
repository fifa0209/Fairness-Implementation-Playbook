# Fairness Decision Record (FDR) Template

**Date**: [YYYY-MM-DD]  
**System**: [AI System Name]  
**Decision ID**: FDR-[YYYY]-[###]  
**Status**: [Draft | In Review | Approved | Archived]

## Context
[Describe the fairness challenge or trade-off requiring a decision. Include relevant background, data, and stakeholder concerns.]

## Decision
[State the decision made clearly and concisely. Be specific about what was chosen and what was rejected.]

## Alternatives Considered

### Alternative 1: [Brief description]
- **Pros**: [List advantages]
- **Cons**: [List disadvantages]
- **Why rejected**: [Rationale for not selecting this option]

### Alternative 2: [Brief description]
- **Pros**: [List advantages]
- **Cons**: [List disadvantages]
- **Why rejected**: [Rationale for not selecting this option]

### Alternative 3: [Selected approach]
- **Pros**: [List advantages]
- **Cons**: [List disadvantages]
- **Why selected**: [Rationale for choosing this option]

## Stakeholders Involved
- **Decision Maker (Accountable)**: [Name, Role]
- **Contributors (Responsible)**: [Names, Roles]
- **Consulted**: [Names, Roles]
- **Informed**: [Names, Roles]

## Rationale
[Detailed explanation of why this decision best addresses the fairness challenge. Include technical analysis, ethical considerations, business impact, and regulatory compliance factors.]

## Trade-offs
[Explicit acknowledgment of what is sacrificed or accepted in this decision.]

### Fairness Dimension:
- [Impact on different demographic groups]
- [Intersectional considerations]

### Performance Dimension:
- [Impact on model accuracy/performance]
- [Computational costs]

### Business Dimension:
- [Impact on business objectives]
- [Resource requirements]

### Regulatory Dimension:
- [Compliance implications]
- [Documentation requirements]

## Known Limitations
[What fairness properties this decision does NOT achieve. Be transparent about edge cases or scenarios where this approach may fail.]

## Mitigation & Monitoring

### Safeguards:
- [Controls to limit negative impacts]
- [Fallback mechanisms]
- [Human oversight procedures]

### Monitoring:
- [How we'll track effectiveness]
- [Key metrics to watch]
- [Alert thresholds]

### Review Frequency:
- [When this decision will be revisited]
- [Trigger conditions for re-evaluation]

## Supporting Evidence
- **Technical analysis**: [Link to evaluation reports]
- **Stakeholder input**: [Link to meeting notes, surveys]
- **Regulatory mapping**: [Link to compliance documentation]
- **Testing results**: [Link to fairness testing outcomes]

## Approval
- **Approved by**: [Name, Role] on [Date]
- **Next review date**: [YYYY-MM-DD]
- **Archival date**: [YYYY-MM-DD]

---

## Example: Adversarial Debiasing Implementation

**Date**: 2024-01-15  
**System**: Resume Screening AI  
**Decision ID**: FDR-2024-001

### Context:
The resume screening system showed persistent gender bias (women 12% less likely to reach interview stage) despite removing gender indicators from resumes.

### Decision:
Implement adversarial debiasing to remove gender information from learned representations, accepting a 2% accuracy reduction.

### Trade-offs:
- **Fairness**: 9.2% gender fairness improvement
- **Performance**: 2% accuracy reduction
- **Business**: Within acceptable threshold for recruitment quality

### Rationale:
Representation-level intervention addresses root cause rather than symptoms. Post-processing alternatives were rejected as they treat symptoms rather than causes.

### Known Limitations:
May not capture all proxy pathways; requires ongoing monitoring of representation fairness.

### Monitoring:
Monthly disaggregated performance reviews, quarterly re-evaluation of protected attribute predictability.