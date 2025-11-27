# Fairness-Enhanced User Story Template

## Template Format

```markdown
**User Story**: [Story Title]

As a [role/stakeholder],
I want [functionality/feature]
So that [benefit/value]
Ensuring [specific fairness goal] across [protected attributes]

## SAFE Framework

**S - Specific Protected Attributes**:
- [List specific attributes: gender, race, age, disability, socioeconomic status, etc.]
- [List key intersections: gender × race, age × disability, etc.]

**A - Actionable Fairness Definition**:
- [Primary fairness metric: e.g., Equal opportunity (TPR parity within 0.03)]
- [Secondary fairness metric: e.g., Demographic parity difference ≤0.05]
- [Tertiary metric: e.g., Intersectional gap ≤0.04]

**F - Feature Integration Points**:
- [Where fairness intersects with functionality]
- [Components affected: data pipeline, model, API, UI, etc.]
- [Dependencies: fairness evaluation tools, demographic data, etc.]

**E - Expected Outcome Measures**:
- [Quantifiable fairness metrics with thresholds]
- [Performance metrics (accuracy, latency, etc.)]
- [Business metrics affected]

## Acceptance Criteria (FAIR Framework)

### F - Fairness Metrics Thresholds
- [ ] [Primary metric] within target threshold
- [ ] [Secondary metric] within target threshold
- [ ] [Tertiary metric] within target threshold
- [ ] Intersectional performance gaps within target

### A - Auditing Requirements
- [ ] [Audit type 1, e.g., Counterfactual analysis for N test cases]
- [ ] [Audit type 2, e.g., Red-team testing with adversarial inputs]
- [ ] [Audit type 3, e.g., Proxy variable analysis completed]

### I - Intersectional Analysis
- [ ] Performance disaggregated for key intersections: [list]
- [ ] Special review process for multiply-marginalized groups documented
- [ ] Performance gaps explained and documented
- [ ] Edge cases identified

### R - Reporting Guidelines
- [ ] Disaggregated performance dashboard updated
- [ ] Model card updated with fairness properties
- [ ] Fairness Decision Record created (if trade-offs made)
- [ ] Monitoring alerts configured for fairness drift
- [ ] Limitation disclosure documented

## Story Points
- Functional work: [X points]
- Fairness work: [Y points]
- Total: [X+Y points]

## Definition of Done
- [ ] All functional acceptance criteria met
- [ ] All fairness acceptance criteria met (FAIR framework)
- [ ] Code review completed
- [ ] Unit tests passing
- [ ] Fairness tests passing (automated)
- [ ] Integration tests passing
- [ ] Documentation updated
- [ ] Stakeholder demo completed

## Dependencies
- [List any dependencies on other stories, infrastructure, data, tools]

## Notes
- [Any additional context, risks, or considerations]
```

---

## Example: Recruitment System

```markdown
**User Story**: Candidate Ranking for Software Engineer Positions

As a recruiting manager,
I want candidates ranked by predicted job fit
So that I can efficiently identify top prospects for interviews
Ensuring equivalent ranking accuracy across gender, race, age, socioeconomic background, and their intersections (particularly gender × race and first-generation × race)

## SAFE Framework

**S - Specific Protected Attributes**:
- Gender: Male, Female, Non-binary
- Race/Ethnicity: White, Black, Hispanic, Asian, Other
- Age: <30, 30-40, 40-50, 50-60, 60+
- Socioeconomic status: Inferred from educational institutions, geographic location
- First-generation status: First-generation college graduate vs. not
- Key intersections: Gender × Race (8 combinations), First-generation × Race (8 combinations)

**A - Actionable Fairness Definition**:
- Primary: Equal Opportunity (True Positive Rate parity within 0.03)
- Secondary: Demographic Parity (Selection rate parity within 0.05)
- Tertiary: Intersectional Gap (≤0.04 for key intersections)

**F - Feature Integration Points**:
- Ranking algorithm: Fair representation learning
- Score calculation: Adversarial debiasing applied
- Top-N selection: Post-processing threshold optimization
- API: Fairness metrics logging
- Dashboard: Disaggregated performance display

**E - Expected Outcome Measures**:
- Demographic parity difference: ≤0.05 (5%)
- Equal opportunity difference: ≤0.03 (3%)
- Intersectional gap: ≤0.04 (4%)
- Overall accuracy: ≥82%
- API latency: <200ms at p95

## Acceptance Criteria (FAIR Framework)

### F - Fairness Metrics Thresholds
- [ ] TPR parity ≤0.03 across gender, race, age, socioeconomic status
- [ ] Demographic parity difference ≤0.05 across all protected attributes
- [ ] Intersectional gap ≤0.04 for:
  - Gender × Race (8 combinations)
  - First-generation × Race (8 combinations)
  - Age × Disability (if applicable)

### A - Auditing Requirements
- [ ] Counterfactual analysis: 500 test candidates (change only demographics, verify ranking stability within 0.5 points)
- [ ] Red-team testing: Adversarial demographic inputs designed to elicit bias (100 test cases)
- [ ] Proxy variable analysis: Verify no hidden demographic predictors (school name, zip code, language patterns)

### I - Intersectional Analysis
- [ ] Performance reported for all gender × race combinations (8 groups, minimum 50 samples each)
- [ ] Special analysis for multiply-marginalized groups (Black women, Hispanic women, older workers with disabilities)
- [ ] Performance gaps documented and explained in technical report
- [ ] Edge cases identified: non-traditional career paths, international candidates, career gaps

### R - Reporting Guidelines
- [ ] Disaggregated performance dashboard covering all protected groups and intersections
- [ ] Model card updated with:
  - Fairness properties and metrics
  - Known limitations (e.g., performance on non-traditional candidates)
  - Mitigation strategies implemented
- [ ] Fairness Decision Record created if trade-offs accepted (e.g., 2% accuracy reduction for fairness)
- [ ] Monitoring alerts configured:
  - Weekly fairness metric tracking
  - Automated alerts for >5% deviation from baseline
  - Quarterly intersectional deep-dive scheduled

## Story Points
- Functional work: 8 points
  - Implement new ranking features: 3 points
  - Performance optimization: 2 points
  - API updates: 2 points
  - Testing: 1 point
- Fairness work: 10 points
  - Data bias audit: 3 points
  - Adversarial debiasing implementation: 5 points
  - Intersectional evaluation framework: 2 points
- Total: 18 points

## Definition of Done
- [ ] Ranking algorithm implemented with adversarial debiasing
- [ ] All fairness acceptance criteria met (FAIR framework)
- [ ] Code review completed by Senior Engineer and Fairness Champion
- [ ] Unit tests passing (>90% coverage)
- [ ] Fairness tests passing:
  - Counterfactual tests (500 cases)
  - Red-team tests (100 cases)
  - Proxy variable tests
- [ ] Integration tests passing
- [ ] API latency <200ms validated
- [ ] Documentation updated:
  - Technical documentation
  - Model card
  - API documentation
- [ ] Sprint review demo completed:
  - Functional demo (10 min)
  - Fairness achievements demo (10 min) with disaggregated metrics

## Dependencies
- Fairness evaluation framework (available in shared library)
- Demographic data for test set (100+ samples per group minimum)
- Adversarial debiasing library (reusable component from Team C)
- Monitoring dashboard infrastructure

## Notes
- Adversarial training complexity may be underestimated; allocated 5 points but may need 6-7
- Create reusable adversarial debiasing module for future systems
- Fairness Champion (James Kim) available for consultation throughout sprint
- Mid-sprint checkpoint scheduled (Day 5) for data validation gate
```

---

## Usage Guidelines

### When to Use This Template

**Always Use For**:
- Any user story involving AI/ML predictions or decisions
- Features that impact different demographic groups
- High-risk system development
- Systems subject to fairness regulations

**Optional For**:
- Infrastructure stories (but consider indirect fairness impact)
- Low-risk internal tools (but still document fairness considerations)

### How to Complete

**Step 1: Basic Story** (Standard Agile)
- Define role, want, so that (traditional format)

**Step 2: Add Fairness Goal** (After "so that")
- "Ensuring [specific fairness goal] across [protected attributes]"

**Step 3: SAFE Framework** (Detail planning)
- Work with Fairness Champion to identify:
  - Specific protected attributes relevant to feature
  - Actionable fairness definitions (which metrics?)
  - Feature integration points (where fairness touches code)
  - Expected outcome measures (quantifiable targets)

**Step 4: Acceptance Criteria** (FAIR Framework)
- Define specific, testable fairness criteria
- Include auditing requirements
- Plan intersectional analysis
- Specify reporting obligations

**Step 5: Estimate** (Split fairness work explicitly)
- Estimate functional work separately from fairness work
- Helps track fairness capacity allocation

**Step 6: DoD** (Include fairness gates)
- All fairness acceptance criteria must be met
- Fairness tests must pass (automated where possible)

### Common Mistakes to Avoid

❌ **Too Generic**: "Ensuring fairness across all groups"
- Not specific about which groups or how fairness is measured

❌ **No Metrics**: "Ensuring equal treatment"
- No quantifiable thresholds for validation

❌ **Missing Intersectionality**: Only lists single attributes
- Ignores compound discrimination at intersections

❌ **No Integration Points**: Doesn't specify where fairness touches the system
- Makes implementation unclear

❌ **Unrealistic Thresholds**: Perfection not achievable
- Example: "Demographic parity difference = 0%" is usually impossible

✅ **Good Practice**: Be specific, measurable, realistic
- "Ensuring equivalent ranking accuracy (TPR parity within 0.03) across gender, race, and age, with special attention to gender × race intersections (gap ≤0.04)"

---

## Template Variations

### For Different Domains

**Healthcare AI**:
```markdown
Ensuring [clinical validity and equitable health outcomes] across [race, ethnicity, sex, age, socioeconomic status, disability, genetic predisposition]

SAFE:
- S: Add genetic information, health status
- A: Prioritize false negative rate parity, calibration
- F: Clinical decision support integration
- E: Health equity outcomes (not just predictions)
```

**Financial Services**:
```markdown
Ensuring [equal access to credit/insurance for qualified applicants] across [race, ethnicity, sex, age, marital status, national origin, public assistance receipt]

SAFE:
- S: Add marital status, national origin, proxy variables (zip code, names)
- A: Prioritize equal opportunity, 80% rule compliance
- F: Proxy detection and mitigation
- E: Disparate impact analysis, calibration
```

**Education**:
```markdown
Ensuring [equal opportunity for qualified students while advancing equity goals] across [race, ethnicity, sex, first-generation status, socioeconomic status, disability, geographic location]

SAFE:
- S: Add first-generation, socioeconomic status, geographic
- A: Balance merit and equity (institution-specific)
- F: Admissions/financial aid/placement specific
- E: Intersectional equity for multiply-marginalized students
```

---

## Integration with Other Playbook Components

**Organizational Integration**:
- RACI: Product Manager Responsible, Product Owner Accountable for defining fairness requirements
- FDR: Link to relevant Fairness Decision Records (e.g., metric selection, trade-off decisions)

**Advanced Architecture**:
- Technical implementation details reference architecture-specific cookbook sections
- Example: "Adversarial debiasing (see Deep Learning section)"

**Regulatory Compliance**:
- Acceptance criteria map to regulatory requirements
- Example: "Counterfactual analysis (GDPR Article 22 compliance)"

**Validation Framework**:
- Expected outcome measures feed into validation dashboards
- Metrics tracked in process validation

---

## Continuous Improvement

This template should evolve based on team experience:

**Quarterly Review**:
- Are fairness requirements clear enough?
- Are estimates accurate?
- Are acceptance criteria sufficient?
- What anti-patterns emerged?

**Iterate Template**:
- Add examples from successful stories
- Clarify ambiguous sections
- Remove unnecessary complexity
- Incorporate lessons learned

**Version Control**:
- Maintain template versions
- Document changes and rationale
- Share improvements across teams

---

**Template Version**: 1.0  
**Last Updated**: 2024  
**Owner**: Fair AI Scrum Working Group  
**Feedback**: Submit improvements to fairness-toolkit@organization.com
