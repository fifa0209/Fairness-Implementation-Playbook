# Fairness Implementation Glossary

## Quick Navigation
- [Core Fairness Concepts](#core-fairness-concepts)
- [Metrics & Measurements](#metrics--measurements)
- [Technical Approaches](#technical-approaches)
- [Governance & Process](#governance--process)
- [Regulatory Terms](#regulatory-terms)

---

## Core Fairness Concepts

### Bias
**Definition**: Systematic error in AI predictions that disadvantages certain groups.

**Types**:
- **Historical bias**: Prejudice embedded in training data reflecting past discrimination
- **Representation bias**: Under/over-representation of groups in datasets
- **Measurement bias**: Features measured differently or with different accuracy across groups
- **Aggregation bias**: One-size-fits-all model inappropriate for diverse populations

**Example**: Resume screening model learns from historical hiring data where women were underrepresented in technical roles, perpetuating this pattern.

---

### Fairness
**Definition**: Equitable treatment of individuals regardless of protected attributes.

**Key principle**: Similar individuals should receive similar outcomes (individual fairness), AND different demographic groups should have equitable outcomes (group fairness).

**Context-dependent**: What counts as "fair" depends on:
- Domain (employment vs. entertainment)
- Stakeholder values
- Legal requirements
- Societal norms

**Not absolute**: Trade-offs between different fairness definitions exist; perfect fairness often impossible.

---

### Protected Attributes
**Definition**: Characteristics that cannot legally or ethically be used as basis for decisions.

**Common protected classes** (U.S. context):
- Race/ethnicity
- Sex/gender
- Age (40+)
- Disability status
- Religion
- National origin
- Pregnancy status
- Genetic information

**Domain-specific additions**:
- Employment: Veteran status, union membership
- Healthcare: HIV status, genetic predispositions
- Financial: Marital status, receipt of public assistance

**Global variation**: Protected classes differ by jurisdiction (e.g., EU includes sexual orientation explicitly).

---

### Intersectionality
**Definition**: Framework recognizing that individuals with multiple marginalized identities experience unique forms of discrimination not captured by single-dimension analysis.

**Origin**: Coined by Kimberlé Crenshaw (1989) in legal scholarship on race and gender discrimination.

**In AI fairness**: Evaluating model performance for gender × race, age × disability, etc., not just gender or race alone.

**Example**: Black women face distinct employment discrimination not explained by anti-Black racism or sexism separately.

**Implementation**: Test AI systems on key intersections (≥2-3 for high-risk systems), ensuring no multiply-marginalized group disproportionately harmed.

---

### Proxy Variable
**Definition**: Feature correlated with protected attribute that indirectly encodes demographic information.

**Common examples**:
- **Zip code**: Proxy for race/ethnicity (residential segregation)
- **Name**: Proxy for race, ethnicity, gender
- **Language patterns**: Writing style may correlate with gender
- **Educational institution**: May correlate with socioeconomic status
- **Employment gaps**: May correlate with parental status (gender)

**Challenge**: Removing explicit demographics insufficient if proxies remain.

**Mitigation**:
1. Identify potential proxies through domain knowledge + correlation analysis
2. Test model fairness with and without suspected proxies
3. If strong proxy: Remove, transform, or apply fairness constraints
4. Document residual proxy risks in model card

---

## Metrics & Measurements

### Demographic Parity (Statistical Parity)
**Definition**: Fairness metric requiring equal positive prediction rates across demographic groups.

**Formula**: P(Ŷ=1 | A=a) = P(Ŷ=1 | A=b) for groups a, b

**Plain language**: Same percentage of each group receives positive outcome.

**Example**: 50% of women and 50% of men approved for loans.

**When to use**: When representation or access is primary concern (e.g., ensuring diverse interview pipeline).

**Threshold**: Typically ≤0.05 difference (5 percentage points) acceptable.

**Limitation**: May require different accuracy levels across groups if base rates differ.

---

### Equal Opportunity
**Definition**: Fairness metric requiring equal true positive rates (sensitivity/recall) across groups.

**Formula**: P(Ŷ=1 | Y=1, A=a) = P(Ŷ=1 | Y=1, A=b)

**Plain language**: Among qualified individuals, same percentage from each group receives positive outcome.

**Example**: Among qualified candidates, 80% of women and 80% of men are hired.

**When to use**: When qualification matters and false negatives are primary concern (hiring, admissions, medical diagnosis).

**Threshold**: Typically ≤0.03 difference (3 percentage points) acceptable.

**Why preferred**: Respects different base rates across groups while ensuring qualified individuals treated equally.

---

### Equalized Odds
**Definition**: Fairness metric requiring both equal true positive rates AND equal false positive rates across groups.

**Formula**: 
- P(Ŷ=1 | Y=1, A=a) = P(Ŷ=1 | Y=1, A=b) [Equal Opportunity]
- P(Ŷ=1 | Y=0, A=a) = P(Ŷ=1 | Y=0, A=b) [Equal FPR]

**Plain language**: Both benefits (true positives) and harms (false positives) distributed equally.

**Example**: Among qualified candidates, same % hired across groups; among unqualified, same % incorrectly hired across groups.

**When to use**: When both false positives and false negatives carry significant consequences (criminal justice, fraud detection).

**Threshold**: ≤0.03 difference for both TPR and FPR.

---

### Calibration
**Definition**: Property where predicted probabilities match actual outcome rates across groups.

**Formula**: P(Y=1 | Ŷ=p, A=a) = P(Y=1 | Ŷ=p, A=b) = p

**Plain language**: When model says "70% chance", actual success rate should be 70% in all groups.

**Example**: If loan default risk estimated at 10% for applicants from Group A and Group B, actual default rate should be ~10% for both.

**When to use**: When probability estimates used for decision-making (risk assessment, resource allocation).

**Measurement**: Plot predicted probability vs. actual outcome rate; should align closely for all groups.

---

### Counterfactual Fairness
**Definition**: A prediction is fair if it would remain the same for an individual if their protected attribute were changed, holding all non-descendant variables constant.

**Causal perspective**: Based on causal modeling; considers how changing protected attribute affects prediction.

**Example**: Changing applicant's race from "White" to "Black" (all else equal) shouldn't change loan decision.

**When to use**: High-stakes individual decisions where causal reasoning matters (employment, credit).

**Implementation**: Generate counterfactual examples (swap protected attributes); measure prediction stability.

**Threshold**: ≤5% change in prediction/score when only protected attribute changes.

**Limitation**: Requires causal model of relationships; computationally expensive.

---

### Disparate Impact
**Definition**: Legal standard (U.S.) where substantially different rate of selection works to disadvantage of protected group.

**80% Rule**: Selection rate for protected group should be ≥80% of rate for highest group.

**Formula**: (Selection Rate for Group A) / (Selection Rate for Group B) ≥ 0.80

**Example**: If 60% of men hired, ≥48% of women must be hired (60% × 0.8 = 48%).

**Origin**: Uniform Guidelines on Employee Selection Procedures (1978).

**Legal context**: Prima facie evidence of discrimination under Title VII (U.S. Civil Rights Act).

**Application**: Employment, housing, credit decisions.

---

## Technical Approaches

### Adversarial Debiasing
**Definition**: Technical approach using competing network (discriminator) to remove protected attribute information from learned representations.

**How it works**:
1. Main model learns task (e.g., predict job performance)
2. Discriminator tries to predict demographics from main model's internal representations
3. Main model learns to fool discriminator (gradient reversal)
4. Result: Representations useful for task but not demographics

**Target**: Protected attribute prediction accuracy from representations <60% (near random).

**Architectures**: Deep learning, neural networks.

**Advantage**: Addresses representation-level bias (not just explicit features).

**Implementation**: Add adversarial loss term to training objective; tune fairness weight (λ).

---

### Pre-Processing (Data-Level Interventions)
**Definition**: Fairness interventions applied to training data before model training.

**Techniques**:
- **Resampling**: Oversample minority group or undersample majority
- **Reweighting**: Assign higher weights to underrepresented examples
- **Relabeling**: Correct biased labels in training data
- **Synthetic data generation**: Create balanced synthetic examples

**Advantage**: Model-agnostic; works with any ML algorithm.

**Limitation**: May reduce dataset size (undersampling) or introduce artificial patterns (oversampling).

**When to use**: When data imbalance is primary bias source.

---

### In-Processing (Model-Level Interventions)
**Definition**: Fairness interventions applied during model training.

**Techniques**:
- **Fairness constraints**: Add fairness metrics as constraints in optimization
- **Adversarial training**: Adversarial debiasing (see above)
- **Regularization**: Penalize model for unfair predictions
- **Multi-objective optimization**: Balance accuracy and fairness objectives

**Advantage**: Directly optimizes for fairness during learning.

**Trade-off**: May reduce task performance; requires careful tuning.

**When to use**: When model architecture allows modification (deep learning, gradient-based methods).

---

### Post-Processing (Decision-Level Interventions)
**Definition**: Fairness interventions applied after model training, adjusting predictions or thresholds.

**Techniques**:
- **Threshold optimization**: Different decision thresholds per group to achieve fairness
- **Score adjustment**: Calibrate scores to equalize outcomes
- **Reject option**: Withhold predictions for cases near decision boundary (human review)

**Advantage**: Model-agnostic; can be applied to any model, including black-box models.

**Limitation**: Doesn't address root cause; may be less robust.

**When to use**: When model can't be retrained (vendor models, legacy systems) or for quick fairness improvement.

---

### Fair Representation Learning
**Definition**: Techniques to learn feature representations that are invariant to protected attributes.

**Goal**: Create embeddings useful for task but not predictive of demographics.

**Approaches**:
- Adversarial debiasing
- Variational autoencoders (VAE) with fairness constraints
- Disentangled representations separating task-relevant from demographic features

**Evaluation**: Measure demographic predictability from learned representations; target <60% accuracy.

**Architectures**: Deep learning (autoencoders, transformers, CNNs).

---

### RLHF (Reinforcement Learning from Human Feedback)
**Definition**: Technique for fine-tuning AI models using human preferences as reward signals.

**Process**:
1. Human raters rank model outputs (e.g., "Output A better than Output B")
2. Reward model trained to predict human preferences
3. Policy model (e.g., LLM) fine-tuned to maximize reward

**Fairness application**: 
- Include fairness in human rating criteria
- Raters explicitly evaluate stereotyping, bias, inclusivity
- Fairness weight: 20-40% of reward signal

**Use case**: Large language models (LLMs), conversational AI.

**Advantage**: Aligns model with human values including fairness.

---

## Governance & Process

### RACI Matrix
**Definition**: Decision-making framework defining who is Responsible, Accountable, Consulted, and Informed for each decision type.

**Roles**:
- **R (Responsible)**: Does the work to complete the task (can be multiple people)
- **A (Accountable)**: Ultimately answerable for completion; has veto power (only ONE person)
- **C (Consulted)**: Provides input before decision/action; two-way communication
- **I (Informed)**: Kept updated on progress/outcomes; one-way communication

**Fairness application**: Clarifies decision authority for fairness trade-offs, threshold setting, deployment approval.

**Example**:
- Fairness metric selection: Technical Fairness Lead (A), ML Engineer (R), Domain Specialist (C), Product Owner (I)

**Benefit**: Eliminates "everyone's responsibility, no one's job" problem.

---

### Fairness Decision Record (FDR)
**Definition**: Structured document capturing context, alternatives, rationale, stakeholders, and trade-offs for fairness decisions.

**Required for**:
- Major fairness-performance trade-offs
- Fairness threshold exceptions
- Novel fairness approaches
- Incidents requiring decision

**Contents**:
- Decision summary
- Context and background
- Options considered (with pros/cons)
- Rationale for chosen option
- Trade-offs accepted
- Stakeholder consultations
- Known limitations
- Monitoring plan

**Ownership**: Accountable party (per RACI) must approve.

**Purpose**: 
- Transparency and accountability
- Audit trail for compliance
- Organizational learning

---

### Fairness DoD (Definition of Done)
**Definition**: Expanded Definition of Done including fairness criteria that must be met before story considered complete.

**FAIR criteria**:
- **F (Fairness thresholds)**: Metrics within acceptable ranges
- **A (Auditing)**: Testing completed (disaggregated, intersectional, counterfactual)
- **I (Intersectional)**: Key intersections evaluated
- **R (Reporting)**: Documentation complete (model cards, FDRs, dashboards)

**Gate**: Fairness Champion must approve before story marked "Done."

**Enforcement**: Story cannot be deployed without passing Fairness DoD.

---

### SAFE Framework
**Definition**: Framework for defining fairness requirements in user stories.

**Components**:
- **S (Specific attributes)**: Which protected attributes relevant?
- **A (Actionable definition)**: Which fairness metric and threshold?
- **F (Feature integration)**: Where in code does fairness touch?
- **E (Expected measures)**: What quantified success criteria?

**Example**: "Ensure equal opportunity (TPR parity ≤0.03) across gender and race for candidate ranking feature, with intersectional analysis for gender × race."

**Use in**: Sprint planning, backlog refinement, requirements gathering.

---

### Model Card
**Definition**: Standardized documentation for machine learning models disclosing performance characteristics, limitations, and intended use.

**Originated**: Mitchell et al. (2019), Google Research.

**Required sections**:
- Model details (architecture, version, training date)
- Intended use and out-of-scope uses
- Training data characteristics
- Performance metrics (overall and disaggregated)
- **Fairness properties**: Metrics, protected attributes, interventions applied
- **Known limitations**: What fairness properties NOT achieved
- Ethical considerations

**Audience**: Developers, deployers, users, auditors, regulators.

**Fairness benefit**: Transparency about model limitations and fairness properties.

---

### Risk Classification Framework
**Definition**: Systematic approach to categorizing AI systems by level of risk based on potential harm.

**Risk levels** (aligned with EU AI Act):
- **Critical**: Life, liberty, livelihood at stake (criminal justice, healthcare diagnosis)
- **High**: Significant impact on opportunities (employment, credit, education)
- **Medium**: Moderate impact on experience (news ranking, personalization)
- **Low**: Minimal individual impact (entertainment recommendation)

**Assessment dimensions**:
- Impact severity
- Decision autonomy (human oversight level)
- Scale (number affected)
- Reversibility (can harm be corrected?)
- Vulnerable populations affected?

**Fairness implications**: Higher risk → more rigorous fairness requirements (capacity allocation, testing, oversight).

---

## Regulatory Terms

### Algorithmic Impact Assessment (AIA)
**Definition**: Structured evaluation process to assess potential impacts of automated decision systems before deployment.

**Origin**: Canadian government Directive on Automated Decision-Making (2019).

**Components**:
- Risk scoring questionnaire
- Impact on individuals and communities
- Mitigation measures
- Transparency obligations
- Recourse mechanisms

**Fairness relevance**: Requires explicit consideration of bias and discrimination risks.

**Adoption**: Canadian federal government mandatory; influencing private sector and other jurisdictions.

---

### EU AI Act
**Definition**: European Union's regulatory framework for artificial intelligence, establishing risk-based approach to AI governance.

**Status**: Adopted April 2024; phased enforcement 2025-2027.

**Risk categories**:
- **Unacceptable risk**: Banned (e.g., social scoring, real-time biometric surveillance)
- **High-risk**: Strict requirements (employment, education, credit, law enforcement)
- **Limited risk**: Transparency obligations
- **Minimal risk**: No specific requirements

**High-risk requirements**:
- Risk management system
- Data governance (bias examination)
- Technical documentation
- Record-keeping
- Transparency
- Human oversight
- Accuracy, robustness, cybersecurity

**Fairness implications**: Explicit bias testing and mitigation required for high-risk systems.

---

### GDPR Article 22
**Definition**: Provision in General Data Protection Regulation giving individuals right not to be subject to purely automated decision-making.

**Scope**: Decisions significantly affecting individuals, without human involvement.

**Rights**:
- Right not to be subject to purely automated decisions (with exceptions)
- Right to meaningful information about logic involved
- Right to human intervention
- Right to contest decision
- Right to explanation

**Exceptions**: Contract necessity, legal authorization, explicit consent.

**Fairness implications**: 
- Human oversight required (aligns with fairness governance)
- Explanation requirement encourages interpretability
- Right to contest enables fairness review

---

### Disparate Treatment vs. Disparate Impact
**Context**: U.S. anti-discrimination law (Title VII Civil Rights Act).

**Disparate Treatment**:
- **Definition**: Intentional discrimination based on protected characteristics
- **Example**: Explicitly using race in hiring decision
- **Legal standard**: Proof of discriminatory intent required
- **AI context**: Using protected attributes as input features

**Disparate Impact**:
- **Definition**: Facially neutral practice with disproportionate adverse effect on protected group
- **Example**: Height requirement disproportionately excludes women
- **Legal standard**: Statistical showing of disproportionate impact (80% rule)
- **AI context**: Model appears neutral but produces biased outcomes

**Fairness relevance**: Most AI fairness issues are disparate impact (unintentional but measurable bias).

---

### Technical Documentation (EU AI Act)
**Definition**: Comprehensive documentation required by EU AI Act covering AI system's design, development, and performance.

**Required contents**:
- General description and intended purpose
- Design specifications and architecture
- Data governance (sources, processing, bias mitigation)
- Training methodology
- Validation and testing procedures
- Performance metrics (overall and disaggregated)
- Human oversight measures
- Risk management approach

**Fairness alignment**: Overlap with model cards, FDRs, fairness documentation.

**Audience**: Regulators, auditors, conformity assessment bodies.

---

### Conformity Assessment
**Definition**: Process to demonstrate AI system complies with EU AI Act requirements.

**Approaches**:
- **Internal control** (Annex VI): Provider self-assessment
- **Third-party assessment** (Annex VII): External auditor

**High-risk systems**: Conformity assessment required before market placement.

**Documentation**: Technical file + quality management system.

**Fairness relevance**: Must demonstrate bias testing and mitigation.

---

## Practical Application Terms

### Feedback Loop Bias
**Definition**: Dynamic amplification of initial biases through system-user interaction over time.

**Context**: Primarily recommendation systems.

**Mechanism**:
1. System shows biased recommendations
2. Users engage with biased content (only option presented)
3. System interprets engagement as preference
4. System doubles down on bias
5. Bias amplifies over time

**Example**: News recommender shows mostly conservative articles → user clicks (no alternative) → system thinks user prefers conservative content → shows even more conservative articles.

**Mitigation**:
- Exploration policies (show diverse content)
- Popularity discounting
- Longitudinal fairness monitoring

---

### Filter Bubble
**Definition**: Personalization algorithms creating echo chambers by showing users only content aligning with existing preferences.

**Consequence**: Reduced exposure to diverse viewpoints, information fragmentation.

**Fairness concern**: May disproportionately affect certain demographics, reducing their access to diverse information.

**Measurement**: Content diversity metrics; % of recommendations outside user's typical consumption.

**Mitigation**: Exploration policies, diversity constraints in ranking.

---

### Red-Teaming
**Definition**: Systematic testing of AI systems using adversarial approaches to identify vulnerabilities.

**Fairness context**: Deliberately attempting to elicit biased, stereotypical, or discriminatory outputs.

**Process**:
1. Diverse team generates adversarial prompts/inputs
2. Test system with edge cases, unusual phrasings
3. Document failures and bias patterns
4. Iterate fixes and retest

**Frequency**: Quarterly for high-risk systems, especially LLMs.

**Example**: Testing if LLM generates stereotypical job descriptions when prompted with different names/demographics.

---

### Stereotype Threat
**Definition**: Psychological phenomenon where individuals underperform due to anxiety about confirming negative stereotypes about their group.

**Classic study**: Steele & Aronson (1995) - Black students performed worse on tests when told it measured intelligence (activating stereotype).

**AI relevance**: 
- Biased AI systems may trigger stereotype threat
- User-facing bias disclosures must be carefully worded to avoid inducing threat
- Performance differences in training data may partly reflect stereotype threat (not just ability)

**Implication**: AI fairness intersects with psychological impacts, not just statistical metrics.

---

### Bias-Variance-Fairness Trade-off
**Definition**: Extension of classic bias-variance trade-off including fairness as third dimension.

**Classic trade-off**: 
- Low bias (complex model) → High variance (overfitting)
- Low variance (simple model) → High bias (underfitting)

**Fairness dimension**:
- Adding fairness constraints typically reduces task performance slightly
- Must balance: Task accuracy + Generalization + Fairness

**Practical implication**: Perfect task performance + perfect fairness often impossible; trade-offs necessary.

**Governance**: Fairness Decision Records document accepted trade-offs.

---

## Cross-References

**For implementation details**: See Architecture Quick Reference
**For incident response**: See Emergency Response Playbook
**For regulatory requirements**: See Regulatory Quick Reference
**For sprint integration**: See Sprint Planning Checklist
**For organizational structure**: See Fairness Implementation Playbook

---

## Quick Lookup Tables

### Fairness Metrics Comparison

| Metric | Formula | Use Case | Typical Threshold |
|--------|---------|----------|-------------------|
| Demographic Parity | P(Ŷ=1\|A=a) = P(Ŷ=1\|A=b) | Representation, access | ≤0.05 difference |
| Equal Opportunity | P(Ŷ=1\|Y=1,A=a) = P(Ŷ=1\|Y=1,A=b) | Qualification matters | ≤0.03 difference |
| Equalized Odds | TPR and FPR parity | Both errors matter | ≤0.03 for each |
| Calibration | P(Y=1\|Ŷ=p,A=a) = p | Probability estimates | Visual inspection |

---

### Technical Interventions by Stage

| Stage | Intervention Type | Examples | Model Agnostic? |
|-------|-------------------|----------|-----------------|
| Pre-processing | Data-level | Resampling, reweighting | ✓ Yes |
| In-processing | Model-level | Adversarial debiasing, fairness constraints | ✗ No |
| Post-processing | Decision-level | Threshold optimization, score adjustment | ✓ Yes |

---

### Risk Level Fairness Requirements

| Risk Level | Capacity % | Intersections | Testing | Lead Involvement |
|------------|------------|---------------|---------|------------------|
| Critical | 30-40% | ≥3 | Extensive (500+ counterfactual) | All sprints |
| High | 25-30% | ≥2 | Rigorous (200+ counterfactual) | High-risk stories |
| Medium | 20-25% | ≥1 | Moderate (100+ counterfactual) | As needed |
| Low | 15-20% | Optional | Basic (50+ counterfactual) | Optional |

---

## Additional Resources

**Academic foundations**: 
- Fairness and Machine Learning (fairmlbook.org)
- ACM FAccT conference proceedings

**Practical tools**:
- AI Fairness 360 (IBM)
- Fairlearn (Microsoft)
- What-If Tool (Google)

**Regulatory guidance**:
- EU AI Act official text
- NIST AI Risk Management Framework
- Algorithmic Accountability Act (proposed U.S.)


