# Sprint Planning Fairness Integration Checklist

---

## Table of Contents

1. [Pre-Planning Preparation](#pre-planning-preparation)
2. [During Sprint Planning](#during-sprint-planning)
3. [Story Review Framework](#story-review-framework)
4. [Definition of Done (Fairness-Enhanced)](#definition-of-done-fairness-enhanced)
5. [Capacity Allocation Guidelines](#capacity-allocation-guidelines)
6. [RACI Integration](#raci-integration)
7. [Exit Criteria](#exit-criteria)
8. [Post-Planning Actions](#post-planning-actions)
9. [Risk-Based Planning Tiers](#risk-based-planning-tiers)
10. [Sprint Templates by System Risk](#sprint-templates-by-system-risk)
11. [Common Pitfalls and Solutions](#common-pitfalls-and-solutions)
12. [Appendices](#appendices)

---

## 1. Pre-Planning Preparation

### 1.1 Review Fairness Backlog (1-2 Days Before Planning)

**Responsibility**: Team Fairness Champion  
**Time Required**: 1-2 hours

#### Actions:
- [ ] **Review previous sprint fairness items**
  - Identify incomplete fairness stories from last sprint
  - Document reasons for incomplete work (technical debt, blocked, deferred)
  - Prioritize carryover items for this sprint
  
- [ ] **Check governance requirements**
  - Review AI Ethics Committee decisions from past month
  - Identify new organizational fairness standards or policies
  - Check for regulatory updates affecting fairness requirements
  - Review updated fairness thresholds or metrics
  
- [ ] **Analyze monitoring alerts**
  - Review fairness monitoring dashboard for drift or violations
  - Document any production fairness issues requiring attention
  - Identify patterns in user complaints or feedback
  - Check incident reports for unresolved fairness concerns
  
- [ ] **Update risk assessment**
  - Re-evaluate risk levels for upcoming features
  - Identify new fairness risks from product roadmap changes
  - Document external factors (regulatory, market, competitive) affecting fairness priorities

#### Deliverables:
- Updated fairness backlog with priorities
- Risk assessment summary document
- List of governance-mandated fairness requirements
- Production issues requiring sprint attention

---

### 1.2 Capacity Planning (1 Day Before Planning)

**Responsibility**: Scrum Master + Team Fairness Champion  
**Time Required**: 30-60 minutes

#### Actions:
- [ ] **Calculate fairness capacity allocation**
  - Target: 15-30% of total sprint capacity for AI systems
  - Formula: `Fairness Points = Total Sprint Capacity × Allocation %`
  - Example: 40-point sprint → 6-12 points for fairness work
  - Document rationale for allocation percentage this sprint
  
- [ ] **Confirm team availability**
  - Verify Fairness Champion availability (10-20% time commitment)
  - Check availability of ML Engineers for fairness implementation
  - Confirm QA Engineer availability for fairness testing
  - Schedule Technical Fairness Lead consultation if needed
  
- [ ] **Schedule fairness review sessions**
  - Mid-sprint fairness checkpoint (30-60 min)
  - Pre-demo fairness review (30 min)
  - Fairness retrospective slot (15-30 min)
  - Consultation sessions with Technical Fairness Lead (as needed)
  
- [ ] **Allocate buffer capacity**
  - Reserve 10-15% capacity for unexpected fairness work
  - Plan for potential fairness-performance trade-off discussions
  - Account for escalations requiring Technical Fairness Lead involvement
  - Buffer for compliance documentation or audit requests

#### Deliverables:
- Fairness capacity allocation decision (% and story points)
- Team availability matrix
- Sprint calendar with fairness review sessions scheduled
- Buffer allocation plan

---

### 1.3 Preparation Materials

**Responsibility**: Product Owner + Team Fairness Champion  
**Time Required**: 1-2 hours

#### Actions:
- [ ] **Gather reference materials**
  - Current fairness standards document
  - Relevant Fairness Decision Records (FDRs)
  - RACI matrix for fairness decisions
  - User story fairness template (SAFE/FAIR framework)
  - Previous sprint fairness metrics and outcomes
  
- [ ] **Prepare fairness evaluation datasets**
  - Verify test data availability for protected groups
  - Ensure minimum sample sizes per group (typically 50+ per group)
  - Check data quality and representativeness
  - Identify any data gaps requiring mitigation
  
- [ ] **Tool and infrastructure readiness**
  - Confirm fairness evaluation framework availability
  - Check monitoring infrastructure for new features
  - Verify access to demographic data for testing (with privacy controls)
  - Ensure documentation tools (model cards, FDRs) are accessible
  
- [ ] **Pre-identify consultation needs**
  - Flag stories requiring Technical Fairness Lead review
  - Identify stories needing Legal consultation
  - Note stories requiring Domain Specialist input
  - Plan timing for external consultations

#### Deliverables:
- Reference materials package
- Data readiness assessment
- Tool access verification
- Consultation scheduling plan

---

## 2. During Sprint Planning

### 2.1 Opening (15 minutes)

**Participants**: Full Team + Product Owner + Fairness Champion

#### Agenda:
- [ ] **Sprint goal announcement**
  - Product Owner presents sprint goal
  - Highlight fairness-critical features in sprint
  - Clarify any governance mandates affecting sprint
  
- [ ] **Fairness context setting**
  - Fairness Champion reviews fairness priorities for sprint
  - Present production fairness status (any issues to address)
  - Remind team of fairness capacity allocation
  - Highlight any new fairness standards or requirements
  
- [ ] **Risk overview**
  - Review high-risk stories flagged in backlog
  - Identify known fairness challenges or trade-offs
  - Discuss escalation paths if fairness issues arise
  
- [ ] **Success criteria preview**
  - Preview key fairness metrics for sprint
  - Set expectations for fairness DoD gates
  - Clarify fairness demo expectations for sprint review

---

### 2.2 User Story Review (60-90 minutes)

**Process**: Review each story for fairness completeness using SAFE/FAIR framework

#### For Each User Story:

**Step 1: Fairness Dimension Check (5 minutes per story)**

- [ ] **SAFE Framework Completeness**
  - **S - Specific Protected Attributes**: Are all relevant attributes identified?
    - Demographics: Gender, race, age, disability, socioeconomic status
    - Intersections: Key combinations documented (e.g., gender × race)
    - Domain-specific: Healthcare (genetics), Financial (marital status), Employment (veteran status)
  
  - **A - Actionable Fairness Definition**: Are metrics and thresholds defined?
    - Primary metric selected (e.g., Equal Opportunity, Demographic Parity)
    - Specific thresholds documented (e.g., TPR parity ≤0.03)
    - Secondary/tertiary metrics identified if applicable
  
  - **F - Feature Integration Points**: Where does fairness touch the code?
    - Data pipeline fairness checks
    - Model fairness interventions
    - API fairness metric logging
    - UI fairness disclosure or controls
  
  - **E - Expected Outcome Measures**: Are success criteria quantified?
    - Fairness metrics with specific targets
    - Performance metrics (accuracy, latency)
    - Business metrics affected

- [ ] **FAIR Acceptance Criteria Completeness**
  - **F - Fairness Metrics Thresholds**: Specific, testable criteria defined
  - **A - Auditing Requirements**: Tests specified (counterfactual, red-team, proxy analysis)
  - **I - Intersectional Analysis**: Multiply-marginalized groups evaluated
  - **R - Reporting Guidelines**: Dashboard updates, model cards, FDRs planned

**Decision Point**: Story complete enough to plan? If no → defer to backlog refinement

---

**Step 2: Story Point Estimation (5-10 minutes per story)**

- [ ] **Separate functional and fairness estimation**
  - Estimate functional work (feature development, performance optimization)
  - Estimate fairness work separately (bias audit, mitigation, intersectional testing)
  - Sum for total story points
  
- [ ] **Fairness work breakdown**
  - Data bias audit: [X points]
  - Fairness intervention implementation: [Y points]
  - Fairness testing and evaluation: [Z points]
  - Documentation (model cards, FDRs): [W points]
  - Monitoring setup: [V points]
  
- [ ] **Validate estimates**
  - Compare to similar past stories
  - Account for team's fairness maturity level
  - Factor in complexity of intersectional analysis
  - Include buffer for fairness-performance iterations

**Common Estimation Pitfalls**:
- ❌ Underestimating bias mitigation complexity (often 2x initial estimate)
- ❌ Forgetting documentation time (model cards, FDRs)
- ❌ Not accounting for consultation time (Legal, Technical Fairness Lead)
- ✅ Use historical data from previous sprints to calibrate

---

**Step 3: Risk Assessment and Mitigation (5 minutes per high-risk story)**

- [ ] **Identify fairness risks**
  - Technical risks: Data quality, model complexity, intervention effectiveness
  - Process risks: Insufficient consultation, unclear thresholds, missing expertise
  - Outcome risks: Fairness-performance trade-offs, stakeholder disagreement
  - Compliance risks: Regulatory requirements, audit readiness
  
- [ ] **Plan mitigation strategies**
  - Early consultation with Technical Fairness Lead
  - Phased implementation with checkpoints
  - Fallback plans for fairness-performance trade-offs
  - Pre-scheduled escalation meetings if trade-offs anticipated
  
- [ ] **Document escalation paths**
  - Team level → Technical Fairness Lead → Chief AI Ethics Officer
  - Timing: When to escalate (e.g., fairness threshold not achievable)
  - Communication: Who needs to be informed (per RACI matrix)
  
- [ ] **Plan contingencies**
  - Scope reduction options if fairness work exceeds estimate
  - Alternative fairness interventions if first approach fails
  - Emergency consultation access (Technical Fairness Lead, Legal)

---

### 2.3 Task Breakdown (30-45 minutes)

**Responsibility**: Team collectively, facilitated by Scrum Master

#### For Each Story:

- [ ] **Break down functional tasks**
  - Feature development tasks (coding, testing, deployment)
  - Performance optimization tasks
  - Integration tasks
  
- [ ] **Break down fairness tasks**
  - **Data bias audit tasks**:
    - Collect data for protected groups
    - Analyze baseline fairness metrics
    - Identify proxy variables
    - Document data limitations
  
  - **Fairness intervention tasks**:
    - Implement chosen intervention (e.g., adversarial debiasing, threshold optimization)
    - Validate intervention effectiveness
    - Measure fairness-performance trade-offs
    - Iterate if thresholds not met
  
  - **Testing tasks**:
    - Disaggregated performance testing
    - Intersectional analysis (key combinations)
    - Counterfactual testing (if applicable)
    - Red-team testing (adversarial inputs)
    - Proxy variable analysis
  
  - **Documentation tasks**:
    - Update model card with fairness properties
    - Create/update Fairness Decision Record (if trade-offs made)
    - Document limitations and safeguards
    - Update technical documentation
  
  - **Monitoring tasks**:
    - Configure fairness metric tracking
    - Set up alerting thresholds
    - Update dashboards
    - Test monitoring in pre-prod

- [ ] **Identify dependencies**
  - Tool dependencies: Fairness evaluation framework, monitoring infrastructure
  - Data dependencies: Demographic data access, test datasets
  - People dependencies: Technical Fairness Lead consultation, Legal review
  - Timeline dependencies: Approval gates, audit milestones
  
- [ ] **Assign owners**
  - Primary owner for each task (per RACI Responsible)
  - Backup owner for critical path tasks
  - Fairness Champion as reviewer for fairness tasks
  - QA Engineer for fairness testing coordination

---

### 2.4 Commitment and Closing (15 minutes)

- [ ] **Review sprint commitment**
  - Total sprint capacity vs. committed work
  - Fairness capacity allocation achieved (15-30% target)
  - High-risk stories adequately planned and resourced
  - Team consensus on achievability
  
- [ ] **Confirm fairness priorities**
  - Top 3 fairness goals for this sprint
  - Critical fairness metrics to achieve
  - Mandatory vs. stretch fairness work
  
- [ ] **Schedule checkpoints**
  - Mid-sprint fairness review (Day 4-5 of 2-week sprint)
  - Pre-demo fairness validation (Day 9)
  - Sprint review fairness demo preparation (Day 10)
  
- [ ] **Communication plan**
  - Inform stakeholders of fairness work this sprint
  - Schedule consultations with Technical Fairness Lead, Legal, etc.
  - Plan communication if fairness issues arise (escalation protocol)

---

## 3. Story Review Framework

### 3.1 Impact Assessment Questions

**Ask for Every Story**:

#### 3.1.1 Differential Impact
- **Q1**: Does this story impact different demographic groups differently?
  - If YES → High fairness scrutiny required
  - If NO → Document why not (may still need fairness consideration)
  - If UNSURE → Assume yes and plan accordingly
  
- **Q2**: What protected attributes are relevant to this feature?
  - Legal protected classes: Race, sex, age, disability, religion, national origin
  - Domain-specific: Socioeconomic status, first-generation, health status, etc.
  - Proxy risks: Zip code, name, language, school attended
  
- **Q3**: Are there intersectional considerations we're missing?
  - Key intersections: Gender × race, age × disability, race × socioeconomic
  - Multiply-marginalized groups: Black women, older workers with disabilities
  - Edge cases: Non-binary gender, multi-racial individuals
  
- **Q4**: What is the impact severity if fairness fails?
  - **Critical**: Affects livelihood, health, liberty (employment, healthcare, criminal justice)
  - **High**: Affects opportunities or resources (education, credit, housing)
  - **Medium**: Affects user experience or satisfaction
  - **Low**: Minimal individual impact

---

### 3.2 Metric Selection Questions

- **Q1**: What fairness metric is appropriate for this functionality?
  - **Equal Opportunity** (TPR parity): When qualification matters (hiring, admissions)
  - **Demographic Parity** (selection rate parity): When representation critical
  - **Equalized Odds** (TPR + FPR parity): When both false positives and negatives matter
  - **Calibration**: When probability estimates used for decision-making
  - **Individual Fairness**: When treating similar individuals similarly is paramount
  
- **Q2**: What thresholds should we set for success?
  - Organizational standards (from fairness governance)
  - Regulatory requirements (e.g., 80% rule for disparate impact)
  - Industry benchmarks
  - Technical feasibility constraints
  - Example thresholds: TPR parity ≤0.03, Demographic parity ≤0.05
  
- **Q3**: How will we measure intersectional performance?
  - Define key intersections to evaluate (typically 2-3 attribute combinations)
  - Set thresholds for worst-case gaps (e.g., intersectional gap ≤0.04)
  - Plan evaluation for multiply-marginalized groups
  - Identify sample size requirements (minimum 50 per intersection)
  
- **Q4**: What are baseline fairness metrics before intervention?
  - Measure current state (if applicable, e.g., existing system being updated)
  - Document historical performance
  - Set improvement targets relative to baseline

---

### 3.3 Implementation Consideration Questions

- **Q1**: What technical interventions might be needed?
  - Pre-processing: Data re-sampling, re-weighting
  - In-processing: Adversarial debiasing, fairness constraints, regularization
  - Post-processing: Threshold optimization, score adjustment
  - Hybrid approaches combining multiple interventions
  
- **Q2**: What data requirements exist for fairness evaluation?
  - Protected attribute data availability and access controls
  - Sample size sufficiency (≥50 per group minimum, ≥100 preferred)
  - Data quality and representativeness
  - Historical bias in data requiring mitigation
  
- **Q3**: What monitoring will be implemented?
  - Real-time fairness metric tracking
  - Drift detection for fairness metrics
  - Alerting thresholds and escalation
  - Dashboard updates for stakeholders
  
- **Q4**: What fairness-performance trade-offs are anticipated?
  - Expected accuracy impact (historical: typically 2-5% for strong fairness)
  - Latency or computational cost increases
  - Complexity trade-offs
  - Business metric impacts

---

### 3.4 Risk Management Questions

- **Q1**: What trade-offs might emerge during implementation?
  - Fairness vs. accuracy
  - Fairness across different groups (can't optimize all simultaneously)
  - Fairness vs. business objectives
  - Fairness vs. user experience (e.g., more questions for equitable assessment)
  
- **Q2**: What are the failure modes for fairness?
  - **Technical failure**: Intervention doesn't improve fairness or worsens it
  - **Data failure**: Insufficient or biased data for evaluation
  - **Threshold failure**: Can't achieve target fairness thresholds
  - **Drift failure**: Fairness degrades over time in production
  
- **Q3**: What safeguards need to be implemented?
  - Human review for edge cases
  - Fallback mechanisms if fairness monitoring detects issues
  - Alert thresholds triggering manual review
  - Kill switch for critical fairness violations
  
- **Q4**: What escalation is required?
  - To Technical Fairness Lead: When thresholds not achievable with planned intervention
  - To Chief AI Ethics Officer: When major fairness-performance trade-offs required
  - To Legal: When compliance implications unclear
  - To Domain Specialist: When fairness definitions ambiguous

---

## 4. Definition of Done (Fairness-Enhanced)

### 4.1 Standard DoD (Functional)

**All stories must meet**:
- [ ] All functional acceptance criteria met
- [ ] Code review completed and approved
- [ ] Unit tests written and passing (≥80% coverage)
- [ ] Integration tests passing
- [ ] Documentation updated (technical docs, API docs)
- [ ] Deployed to staging/pre-production environment
- [ ] Product Owner acceptance

---

### 4.2 Fairness DoD Gate (CRITICAL - No story complete without this)

**Responsibility**: Team Fairness Champion (Accountable per RACI)  
**Gate Keeper**: Fairness Champion must approve before story marked done

#### 4.2.1 Fairness Testing Complete

- [ ] **Disaggregated performance testing**
  - Metrics calculated for all protected groups
  - Minimum sample sizes achieved (≥50 per group)
  - Performance documented in disaggregated dashboard
  - No group excluded from evaluation
  
- [ ] **Intersectional analysis performed**
  - Key intersections evaluated (per SAFE framework)
  - Worst-case gaps identified and documented
  - Multiply-marginalized groups specifically examined
  - Sample size limitations documented if insufficient data
  
- [ ] **Counterfactual testing (for high-stakes decisions)**
  - Test cases designed (typically 100-500 depending on risk)
  - Predictions stable when only protected attributes change
  - Maximum score difference documented (typically ≤0.5 on 0-1 scale)
  - Failures investigated and explained
  
- [ ] **Red-team testing for adversarial inputs**
  - Adversarial test cases designed (edge cases, manipulated inputs)
  - System resilience to bias exploitation tested
  - Vulnerabilities documented and mitigated
  - Severity of vulnerabilities assessed
  
- [ ] **Proxy variable analysis**
  - Potential proxies identified (names, zip codes, language patterns)
  - Correlation with protected attributes measured
  - High-correlation proxies removed or mitigated
  - Residual proxy risks documented

---

#### 4.2.2 Fairness Metrics Within Thresholds

- [ ] **Primary fairness metric achieved**
  - Metric value calculated and documented
  - Threshold met (e.g., TPR parity ≤0.03)
  - If threshold not met: Escalation to Technical Fairness Lead completed
  - If trade-off accepted: Fairness Decision Record (FDR) created and approved
  
- [ ] **Secondary fairness metrics evaluated**
  - Secondary metrics calculated (e.g., demographic parity if primary is equal opportunity)
  - Documented even if not gate criteria
  - Flagged if concerning (even if not blocking)
  
- [ ] **Intersectional fairness gaps within limits**
  - Worst-case intersectional gap documented
  - Threshold met (typically ≤0.04)
  - Multiply-marginalized groups specifically assessed
  
- [ ] **Performance metrics acceptable**
  - Overall accuracy/performance documented
  - Performance trade-off acceptable (per governance standards)
  - No group experiences unacceptable performance degradation

---

#### 4.2.3 Documentation Complete

- [ ] **Model card updated**
  - Fairness metrics section populated
  - Protected attributes used documented
  - Fairness interventions applied described
  - Known limitations disclosed
  - Intended use and out-of-scope uses clarified
  - Evaluation dataset characteristics documented
  
- [ ] **Fairness Decision Record (FDR) created if applicable**
  - Required for: Major fairness-performance trade-offs, threshold exceptions, novel fairness approaches
  - FDR follows template (per playbook)
  - All RACI stakeholders consulted and documented
  - Approved by Accountable party (Technical Fairness Lead or Chief AI Ethics Officer)
  
- [ ] **Limitations documented with safeguards**
  - Known fairness limitations explicitly stated
  - Mitigation strategies documented
  - Monitoring plan for ongoing evaluation
  - User-facing disclosures (if applicable)
  
- [ ] **Technical documentation updated**
  - Fairness intervention code documented
  - Evaluation methodology described
  - Configuration parameters explained
  - Deployment instructions include fairness checks

---

#### 4.2.4 Monitoring Configured

- [ ] **Fairness metrics tracked in production**
  - Key fairness metrics logged continuously
  - Disaggregated metrics calculated (not just overall)
  - Metrics accessible via dashboard
  - Historical trends visualized
  
- [ ] **Alert thresholds set**
  - Critical alerts: Immediate notification (e.g., TPR gap >0.07)
  - Major alerts: Daily review (e.g., demographic parity violation)
  - Minor alerts: Weekly review (e.g., drift >5%)
  - Alert recipients configured (on-call, Fairness Champion, Technical Fairness Lead)
  
- [ ] **Dashboards updated**
  - New feature fairness metrics visible
  - Disaggregated views available
  - Intersectional drill-down enabled (if feasible)
  - Comparison to baseline or historical data
  
- [ ] **Ongoing evaluation documented**
  - Review frequency defined (daily, weekly, monthly)
  - Review responsibility assigned (ML Engineer, Fairness Champion)
  - Escalation triggers documented
  - Re-evaluation schedule set (e.g., quarterly deep-dive)

---

#### 4.2.5 Governance and Compliance

- [ ] **Required approvals obtained**
  - Fairness Champion approval (always required)
  - Technical Fairness Lead approval (for high-risk features)
  - Legal approval (if compliance implications)
  - Domain Specialist approval (for threshold decisions)
  
- [ ] **Stakeholders informed**
  - Product Owner informed of fairness status
  - Technical Fairness Lead informed (for high-risk features)
  - Relevant teams informed (if cross-team dependencies)
  - Users informed (if fairness disclosures required)
  
- [ ] **Compliance evidence collected**
  - Test results saved for audit trail
  - Fairness evaluation reports archived
  - Model card versioned and stored
  - FDR linked to feature/story for traceability
  
- [ ] **Deployment checklist completed**
  - Pre-deployment fairness validation passed
  - Production monitoring verified
  - Rollback plan includes fairness monitoring
  - Post-deployment fairness review scheduled

---

### 4.3 Fairness DoD Enforcement

**Process**:
1. Developer completes story and requests Fairness Champion review
2. Fairness Champion reviews all fairness DoD criteria
3. If all criteria met → Fairness Champion approves, story moves to Product Owner for final acceptance
4. If criteria not met → Fairness Champion blocks story, documents gaps, works with developer to address
5. If criteria cannot be met → Escalate to Technical Fairness Lead for trade-off decision

**Common Scenarios**:
- **Scenario 1**: Fairness threshold not met despite best efforts
  - **Action**: Escalate to Technical Fairness Lead
  - **Outcome**: Either adjust threshold (with FDR), implement stronger intervention, or defer feature
  
- **Scenario 2**: Insufficient data for intersectional analysis
  - **Action**: Document limitation, implement mitigation (e.g., human review for affected groups)
  - **Outcome**: Story can proceed with documented limitation and safeguard
  
- **Scenario 3**: Fairness-performance trade-off worse than anticipated
  - **Action**: Escalate to Technical Fairness Lead and Product Owner
  - **Outcome**: Decision on acceptable trade-off, documented in FDR

---

## 5. Capacity Allocation Guidelines

### 5.1 Target Allocation by System Risk

| System Risk Level | Fairness Capacity % | Rationale |
|-------------------|---------------------|-----------|
| **High-Risk** (Employment, Credit, Healthcare, Criminal Justice) | 25-30% | Extensive intersectional analysis, rigorous testing, comprehensive documentation required |
| **Medium-Risk** (Education, Personalization with significant impact) | 20-25% | Moderate fairness requirements, some intersectional analysis needed |
| **Low-Risk** (Content recommendation, non-critical personalization) | 15-20% | Basic fairness evaluation, monitoring, documentation |
| **Non-AI Features** (Traditional software) | 0-5% | Minimal fairness work, may have indirect fairness implications |

### 5.2 Allocation by Sprint Phase

**Sprint 0-1 (Baseline Establishment)**:
- Fairness capacity: 30-40% (higher than steady state)
- Focus: Data bias audit, baseline metrics, tool setup, team training
- Rationale: Upfront investment in fairness infrastructure

**Sprint 2-4 (Active Development)**:
- Fairness capacity: 25-30% (target range)
- Focus: Fairness intervention implementation, iterative testing, threshold achievement
- Rationale: Intensive fairness work during feature development

**Sprint 5+ (Maintenance)**:
- Fairness capacity: 15-20% (steady state)
- Focus: Monitoring, drift detection, documentation updates, periodic re-evaluation
- Rationale: Ongoing fairness assurance with less intensive effort

---

### 5.3 Capacity Allocation Worksheet

**Total Sprint Capacity**: ______ story points (based on team velocity)

**Fairness Target %**: ______ % (based on system risk level)

**Fairness Capacity**: ______ story points (Total × Target %)

**Breakdown**:
- Data bias audit: ______ points (___%)
- Fairness intervention implementation: ______ points (___%)
- Fairness testing and evaluation: ______ points (___%)
- Intersectional analysis: ______ points (___%)
- Documentation (model cards, FDRs): ______ points (___%)
- Monitoring setup: ______ points (___%)
- Consultation and meetings: ______ points (___%)
- Buffer for unexpected fairness work: ______ points (___%)

**Total Fairness Allocation**: ______ points

**Validation**:
- [ ] Fairness allocation meets target % (±5% acceptable)
- [ ] Team consensus on allocation achievability
- [ ] High-risk stories adequately resourced
- [ ] Buffer allocated (10-15% of fairness capacity)

---

### 5.4 Adjusting Capacity Mid-Sprint

**Scenario**: Fairness work exceeds estimate

**Options**:
1. **Use buffer capacity** (10-15% reserved for this purpose)
2. **Defer lower-priority functional work** (with Product Owner approval)
3. **Reduce scope of current story** (functional features, not fairness requirements)
4. **Extend sprint** (rare, requires team and stakeholder agreement)
5. **Defer fairness work to next sprint** (ONLY if low-risk and approved by Technical Fairness Lead)

**Decision Process**:
- Team Fairness Champion identifies capacity gap
- Discuss options with Scrum Master and Product Owner

## 6. RACI Integration

### 6.1 Overview

The RACI matrix defines roles and responsibilities for fairness-related decisions throughout the sprint. This ensures accountability, prevents bottlenecks, and clarifies escalation paths.

**RACI Definitions**:
- **R (Responsible)**: Does the work to complete the task
- **A (Accountable)**: Ultimately answerable for completion and has veto power
- **C (Consulted)**: Provides input before decisions/actions
- **I (Informed)**: Kept up-to-date on progress and outcomes

---

### 6.2 Sprint Planning RACI Matrix

| Activity | Team Fairness Champion | ML Engineer | QA Engineer | Product Owner | Technical Fairness Lead | Chief AI Ethics Officer | Legal | Domain Specialist |
|----------|------------------------|-------------|-------------|---------------|------------------------|------------------------|-------|-------------------|
| **Pre-Planning Fairness Backlog Review** | R, A | C | I | C | C | I | - | - |
| **Capacity Allocation Decision** | C | C | C | C | A | I | - | - |
| **Story Fairness Assessment** | R, A | C | C | I | C | - | - | C |
| **Fairness Metric Selection** | R | C | C | C | A | I | - | C |
| **Threshold Setting** | C | C | - | C | A | C | C | C |
| **Story Point Estimation (Fairness Work)** | R, A | R | C | I | C | - | - | - |
| **Risk Assessment** | R, A | C | C | I | C | I | - | - |
| **Task Breakdown (Fairness Tasks)** | R, A | R | R | I | C | - | - | - |

---

### 6.3 Development and Testing RACI Matrix

| Activity | Team Fairness Champion | ML Engineer | QA Engineer | Product Owner | Technical Fairness Lead | Chief AI Ethics Officer | Legal | Domain Specialist |
|----------|------------------------|-------------|-------------|---------------|------------------------|------------------------|-------|-------------------|
| **Data Bias Audit** | A | R | C | I | C | - | - | - |
| **Fairness Intervention Implementation** | A | R | C | I | C | - | - | - |
| **Disaggregated Performance Testing** | A | C | R | I | C | - | - | - |
| **Intersectional Analysis** | A | R | R | I | C | - | - | C |
| **Counterfactual Testing** | A | C | R | I | C | - | - | - |
| **Red-Team Testing** | C | C | R, A | I | C | - | - | - |
| **Proxy Variable Analysis** | A | R | C | I | C | - | - | - |
| **Model Card Updates** | A | R | C | I | C | - | - | - |
| **Fairness Decision Record Creation** | R | C | C | I | A | C | C | C |
| **Monitoring Configuration** | A | R | C | I | C | - | - | - |

---

### 6.4 Gate and Approval RACI Matrix

| Decision/Approval | Team Fairness Champion | ML Engineer | QA Engineer | Product Owner | Technical Fairness Lead | Chief AI Ethics Officer | Legal | Domain Specialist |
|-------------------|------------------------|-------------|-------------|---------------|------------------------|------------------------|-------|-------------------|
| **Fairness DoD Gate Approval** | A | I | I | I | C | - | - | - |
| **Story Completion Approval** | C | I | I | A | I | - | - | - |
| **Fairness Threshold Exception** | C | I | - | C | A | C | C | C |
| **Major Fairness-Performance Trade-off** | C | C | - | C | A | C | C | C |
| **High-Risk Feature Deployment** | C | C | - | C | A | C | C | - |
| **FDR Approval (Standard)** | C | C | - | C | A | I | C | C |
| **FDR Approval (Critical Systems)** | C | C | - | C | C | A | C | C |
| **Compliance Sign-off** | I | I | - | I | C | C | A | - |

---

### 6.5 RACI Application Guidelines

#### 6.5.1 When to Consult (C) vs. Inform (I)

**Consult** when:
- Decision significantly impacts their domain
- Their expertise is needed for decision quality
- They have stake in the outcome
- Regulatory or compliance implications exist

**Inform** when:
- They need awareness but not input
- Decision already made but affects their work
- Transparency required for governance
- Audit trail documentation needed

#### 6.5.2 Escalation Based on RACI

**Standard Escalation Path**:
1. **Team Level** (Team Fairness Champion Accountable)
   - Routine fairness decisions
   - Standard threshold achievement
   - Common fairness interventions

2. **Technical Fairness Lead Level** (Technical Fairness Lead Accountable)
   - Fairness thresholds not achievable
   - Novel fairness interventions
   - Significant fairness-performance trade-offs
   - High-risk feature deployment

3. **Chief AI Ethics Officer Level** (Chief AI Ethics Officer Accountable)
   - Critical system fairness decisions
   - Major organizational policy implications
   - Cross-system fairness standards
   - Governance framework changes

4. **Legal Level** (Legal Accountable)
   - Regulatory compliance questions
   - Legal risk assessments
   - Disclosure requirements
   - Audit defense preparation

#### 6.5.3 Consultation Timing

| Consultation Type | When to Initiate | Duration | Preparation Required |
|-------------------|------------------|----------|---------------------|
| **Technical Fairness Lead (Routine)** | During sprint planning for high-risk stories | 30-60 min | Story details, baseline metrics, proposed approach |
| **Technical Fairness Lead (Escalation)** | As soon as threshold issues identified | 60-90 min | Full analysis, alternatives explored, impact assessment |
| **Legal Consultation** | Pre-planning for compliance-critical features | 60-120 min | Feature description, user impact analysis, risk assessment |
| **Domain Specialist** | During story refinement | 30-45 min | Fairness metric options, threshold proposals |
| **Chief AI Ethics Officer** | For major trade-offs (2-3 days notice) | 60-90 min | Complete analysis, stakeholder input, recommendation |

---

### 6.6 Common RACI Pitfalls

| Pitfall | Impact | Solution |
|---------|--------|----------|
| **Too many people Accountable** | Diffused responsibility, decision paralysis | One Accountable per activity; escalate if disagreement |
| **Consulted not given sufficient time** | Poor decisions, resentment, rework | Schedule consultations during sprint planning; allow 2-3 days for complex consultations |
| **Informed stakeholders surprised** | Trust issues, governance breakdowns | Automated notifications; dashboard updates; sprint review attendance |
| **Responsible without Accountable buy-in** | Wasted effort, scope creep | Accountable approves work plan before Responsible begins |
| **Skipping Consulted to save time** | Compliance issues, technical debt, rework | Non-negotiable for high-risk decisions; document in FDR |

---

## 7. Exit Criteria

### 7.1 Purpose

Exit criteria define the conditions that must be met before the sprint can be considered complete from a fairness perspective. These criteria prevent fairness debt and ensure production readiness.

---

### 7.2 Mandatory Exit Criteria

**All criteria must be met; no exceptions without Chief AI Ethics Officer approval**

#### 7.2.1 All Committed Stories Meet Fairness DoD

- [ ] **Every story marked "Done" has passed Fairness DoD Gate**
  - Fairness Champion approval documented for each story
  - No fairness DoD criteria waived without FDR
  - All testing complete (disaggregated, intersectional, counterfactual, red-team, proxy)
  
- [ ] **High-risk stories have Technical Fairness Lead sign-off**
  - Documented approval in story or FDR
  - All Technical Fairness Lead feedback addressed
  - Deployment checklist completed

#### 7.2.2 No Critical Fairness Defects Open

- [ ] **Zero Severity 1 (Critical) fairness defects**
  - Severity 1: Violates fairness threshold by >50% (e.g., TPR gap 0.045 when threshold 0.03)
  - All critical defects resolved or FDR created with time-bound remediation plan
  
- [ ] **Severity 2 (Major) fairness defects have mitigation plan**
  - Severity 2: Violates fairness threshold by 10-50%
  - Mitigation plan documented and approved by Technical Fairness Lead
  - Timeline for resolution established (next sprint or specific date)

#### 7.2.3 Production Monitoring Operational

- [ ] **Fairness monitoring deployed and validated**
  - Fairness metrics logging correctly in production environment
  - Dashboards displaying data correctly
  - Alerts tested and working
  - On-call rotation aware of fairness alerts
  
- [ ] **Baseline metrics captured**
  - Pre-sprint fairness metrics documented
  - Post-sprint fairness metrics documented
  - Comparison shows improvement or stability (no regression)

#### 7.2.4 Documentation Complete and Accessible

- [ ] **All model cards updated**
  - Current fairness properties documented
  - Known limitations disclosed
  - Intended use and out-of-scope uses clarified
  
- [ ] **FDRs created and approved for major decisions**
  - All RACI stakeholders consulted and documented
  - Approved by Accountable party
  - Linked to relevant stories for traceability
  
- [ ] **Audit trail preserved**
  - Test results archived
  - Evaluation reports saved
  - Configuration parameters documented
  - Deployment evidence collected

---

### 7.3 Conditional Exit Criteria

**Required based on system risk or sprint content**

#### 7.3.1 High-Risk Systems (Employment, Credit, Healthcare, Criminal Justice)

- [ ] **External audit readiness achieved**
  - All compliance evidence collected and organized
  - Evaluation methodology documented in detail
  - Test datasets preserved with documentation
  - Fairness intervention code thoroughly documented
  
- [ ] **Legal review completed**
  - Disclosure language approved
  - Compliance with applicable regulations verified
  - Risk mitigation strategies reviewed
  
- [ ] **Stakeholder communication completed**
  - Users informed of fairness properties (if applicable)
  - Internal stakeholders briefed on fairness status
  - Executive summary prepared for governance committee

#### 7.3.2 New Fairness Interventions or Methodologies

- [ ] **Technical Fairness Lead validation**
  - Novel approach reviewed and approved
  - Methodology documented for reuse
  - Lessons learned captured
  
- [ ] **Peer review completed**
  - Another ML engineer reviewed approach
  - Fairness Champion from another team reviewed (if available)
  - External expert consulted (if warranted)

#### 7.3.3 First Production Deployment of AI Feature

- [ ] **Phased rollout plan approved**
  - Gradual rollout strategy defined (e.g., 5% â†' 25% â†' 100%)
  - Rollback triggers defined (including fairness metrics)
  - Fairness monitoring more intensive during rollout
  
- [ ] **Post-deployment evaluation scheduled**
  - Week 1, Week 4, and Month 3 fairness reviews scheduled
  - Responsible parties assigned
  - Success criteria for continuing rollout defined

---

### 7.4 Exit Criteria Validation Process

#### 7.4.1 Sprint Review Fairness Check (Day 9-10 of Sprint)

**Responsibility**: Team Fairness Champion  
**Duration**: 30-60 minutes  
**Participants**: Fairness Champion, Scrum Master, Product Owner, (Technical Fairness Lead for high-risk sprints)

**Agenda**:
1. Review each committed story against Fairness DoD
2. Verify all mandatory exit criteria met
3. Verify conditional exit criteria met (if applicable)
4. Identify any gaps or risks
5. Make go/no-go decision for sprint completion

**Outcomes**:
- **Green (Go)**: All exit criteria met; sprint can close
- **Yellow (Conditional Go)**: Minor gaps exist; mitigation plan in place; sprint can close with documented risks
- **Red (No-Go)**: Critical gaps exist; sprint cannot close until resolved

#### 7.4.2 Handling "No-Go" Scenarios

**Option 1: Extend Sprint (Rare)**
- Requires: Team consensus + Product Owner approval + stakeholder communication
- Typical extension: 2-3 days
- Focus: Resolve critical fairness gaps only

**Option 2: Descope Features (Preferred)**
- Incomplete fairness work returns to backlog
- Feature not deployed until fairness DoD met
- No partial deployment of AI features with fairness gaps

**Option 3: Emergency Exception (Very Rare)**
- Requires: Chief AI Ethics Officer approval + Legal consultation + FDR
- Only for: Time-sensitive business needs with acceptable risk profile
- Must include: Time-bound remediation plan, enhanced monitoring, manual fallback

---

### 7.5 Exit Criteria Checklist

**Use this checklist during sprint review fairness check**

#### Mandatory Criteria

- [ ] All committed stories passed Fairness DoD Gate (Fairness Champion approval documented)
- [ ] Zero Severity 1 (Critical) fairness defects open
- [ ] Severity 2 (Major) fairness defects have approved mitigation plans
- [ ] Production fairness monitoring deployed and validated
- [ ] Baseline and post-sprint fairness metrics documented
- [ ] All model cards updated with current fairness properties
- [ ] FDRs created and approved for major decisions
- [ ] Audit trail preserved (test results, evaluation reports, configurations)

#### Conditional Criteria (if applicable)

- [ ] High-risk systems: External audit readiness achieved
- [ ] High-risk systems: Legal review completed
- [ ] High-risk systems: Stakeholder communication completed
- [ ] New interventions: Technical Fairness Lead validation obtained
- [ ] New interventions: Peer review completed
- [ ] First deployment: Phased rollout plan approved
- [ ] First deployment: Post-deployment evaluation scheduled

#### Decision

- [ ] **GREEN (Go)**: All criteria met; sprint complete
- [ ] **YELLOW (Conditional Go)**: Minor gaps with documented mitigation; sprint complete with monitoring
- [ ] **RED (No-Go)**: Critical gaps; sprint cannot close

**If RED, action required**: ☐ Extend Sprint  ☐ Descope Features  ☐ Emergency Exception (requires Chief AI Ethics Officer approval)

---

## 8. Post-Planning Actions

### 8.1 Immediate Actions (Within 24 Hours of Sprint Planning)

#### 8.1.1 Communication and Alignment

**Responsibility**: Scrum Master + Team Fairness Champion

- [ ] **Stakeholder notification**
  - Send sprint summary to Technical Fairness Lead (for high-risk sprints)
  - Notify Legal if compliance-critical work planned
  - Inform Domain Specialists of consultation needs
  - Alert on-call team about upcoming fairness monitoring changes
  
- [ ] **Cross-team coordination**
  - Notify dependent teams of fairness work that may affect them
  - Coordinate with data engineering for protected attribute data access
  - Align with platform teams on monitoring infrastructure needs
  - Schedule shared resources (evaluation frameworks, test environments)
  
- [ ] **Internal team alignment**
  - Ensure all team members understand their fairness responsibilities
  - Clarify RACI roles for each story
  - Confirm availability for mid-sprint fairness checkpoint
  - Address any questions or concerns from team members

#### 8.1.2 Environment and Tool Setup

**Responsibility**: ML Engineer + DevOps

- [ ] **Development environment configuration**
  - Fairness evaluation libraries installed and tested
  - Access to protected attribute data verified (with privacy controls)
  - Test datasets prepared and accessible
  - Monitoring test environment configured
  
- [ ] **Tool validation**
  - Fairness evaluation framework functional
  - Dashboard access confirmed for all team members
  - Alert testing completed
  - Documentation tools (model cards, FDRs) accessible
  
- [ ] **Data readiness verification**
  - Protected attribute data available with correct access controls
  - Sample sizes sufficient for planned evaluations (â‰¥50 per group)
  - Data quality checks passed
  - Intersectional subgroups identified and data availability confirmed

#### 8.1.3 Sprint Board Setup

**Responsibility**: Scrum Master

- [ ] **Fairness task visibility**
  - Fairness tasks tagged or labeled distinctly (e.g., "Fairness" label)
  - Fairness capacity allocation visible on sprint board
  - Critical path fairness tasks highlighted
  - Dependencies on external consultations marked
  
- [ ] **Tracking mechanisms**
  - Fairness story points tracked separately from functional points
  - Burndown chart includes fairness work
  - Fairness DoD checklist visible for each story
  - Escalation status indicator for high-risk stories
  
- [ ] **Calendar integration**
  - Mid-sprint fairness checkpoint scheduled and visible
  - Consultation sessions with Technical Fairness Lead/Legal/Domain Specialists scheduled
  - Pre-demo fairness validation session scheduled
  - Sprint review fairness check scheduled

---

### 8.2 Ongoing Actions (Throughout Sprint)

#### 8.2.1 Daily Stand-up Fairness Integration

**Responsibility**: Team Fairness Champion (facilitates fairness discussion)

**Daily Stand-up Fairness Questions** (2-3 minutes):
- Are any fairness tasks blocked?
- Do we need to escalate any fairness issues?
- Are we on track with fairness capacity allocation?
- Any surprises in fairness testing or evaluation?

**Escalation Triggers** (require immediate discussion):
- Fairness threshold not achievable with planned intervention
- Fairness testing reveals unexpected issues
- Data quality or availability problems
- Consultation delays impacting critical path

#### 8.2.2 Mid-Sprint Fairness Checkpoint

**Timing**: Day 4-5 of 2-week sprint  
**Duration**: 30-60 minutes  
**Responsibility**: Team Fairness Champion (leads)  
**Participants**: Fairness Champion, ML Engineers, QA Engineer, Scrum Master, (Product Owner optional)

**Agenda**:

1. **Fairness Work Progress Review** (15 minutes)
   - Review completed fairness tasks vs. planned
   - Check fairness story points burned vs. target
   - Identify any fairness work behind schedule
   - Discuss blockers or impediments

2. **Early Results Review** (15 minutes)
   - Review preliminary fairness evaluation results
   - Identify any concerning patterns or issues
   - Discuss if fairness thresholds appear achievable
   - Flag stories at risk of not meeting Fairness DoD

3. **Adjustment Planning** (15 minutes)
   - Decide if capacity reallocation needed
   - Plan escalations if thresholds at risk
   - Adjust scope if necessary (with Product Owner)
   - Schedule additional consultations if needed

4. **Action Items** (5 minutes)
   - Document decisions and action items
   - Assign owners and deadlines
   - Escalate to Technical Fairness Lead if necessary
   - Update sprint board and tracking

**Outputs**:
- Mid-sprint fairness status report
- Adjusted plan (if needed)
- Escalations initiated (if needed)
- Action items with owners

#### 8.2.3 Continuous Monitoring and Communication

**Daily**:
- [ ] Fairness Champion reviews progress on fairness tasks
- [ ] Team discusses fairness blockers in stand-up
- [ ] Update sprint board with fairness task status

**Every 2-3 days**:
- [ ] Review early fairness evaluation results
- [ ] Check in with ML Engineers on fairness intervention progress
- [ ] Verify consultation sessions remain scheduled

**Weekly**:
- [ ] Fairness Champion reports to Technical Fairness Lead (for high-risk sprints)
- [ ] Review fairness capacity burn vs. plan
- [ ] Assess risk of not meeting fairness exit criteria

---

### 8.3 Pre-Sprint Review Actions (Day 8-9 of Sprint)

#### 8.3.1 Fairness Demo Preparation

**Responsibility**: Team Fairness Champion + ML Engineer

- [ ] **Prepare fairness metrics presentation**
  - Disaggregated performance metrics visualized
  - Intersectional analysis results summarized
  - Fairness threshold achievement documented
  - Comparison to baseline or historical data
  
- [ ] **Prepare demo of fairness features**
  - Show fairness monitoring dashboard
  - Demonstrate fairness evaluation process
  - Walk through model card updates
  - Present FDRs (if created)
  
- [ ] **Prepare limitations and safeguards discussion**
  - Known fairness limitations clearly stated
  - Mitigation strategies explained
  - Monitoring plan for ongoing evaluation
  - User-facing disclosures (if applicable)

#### 8.3.2 Exit Criteria Pre-Check

**Responsibility**: Team Fairness Champion

- [ ] Review all committed stories against Fairness DoD (use checklist from Section 4.2)
- [ ] Review mandatory exit criteria (from Section 7.2)
- [ ] Review conditional exit criteria if applicable (from Section 7.3)
- [ ] Identify any gaps or risks
- [ ] Plan remediation for gaps (or prepare for descoping discussion)
- [ ] Prepare for sprint review fairness check (Section 7.4.1)

#### 8.3.3 Documentation Finalization

**Responsibility**: ML Engineer + Team Fairness Champion

- [ ] **Model cards finalized**
  - All sections complete and accurate
  - Reviewed for clarity and completeness
  - Version controlled and accessible
  
- [ ] **FDRs completed and approved**
  - All RACI stakeholders signed off
  - Linked to relevant stories
  - Archived for audit trail
  
- [ ] **Technical documentation updated**
  - Fairness intervention code documented
  - Evaluation methodology described
  - Configuration parameters explained
  - Deployment instructions include fairness checks

---

### 8.4 Post-Sprint Review Actions (Within 48 Hours)

#### 8.4.1 Sprint Retrospective Fairness Component

**Timing**: Standard sprint retrospective  
**Duration**: 15-30 minutes of retrospective dedicated to fairness  
**Responsibility**: Team Fairness Champion (facilitates fairness discussion)

**Fairness Retrospective Questions**:

1. **What went well with fairness work this sprint?**
   - Effective fairness interventions
   - Smooth consultation processes
   - Good collaboration on fairness testing
   - Adequate capacity allocation

2. **What didn't go well with fairness work?**
   - Fairness work underestimated
   - Thresholds difficult to achieve
   - Data availability issues
   - Consultation delays or gaps

3. **What should we improve for next sprint?**
   - Estimation accuracy
   - Earlier escalation of issues
   - Better integration of fairness and functional work
   - Improved tooling or processes

4. **Action items for improvement**
   - Specific, measurable, assigned, time-bound
   - Document in retrospective notes
   - Carry forward to next sprint planning

#### 8.4.2 Fairness Metrics Analysis

**Responsibility**: Team Fairness Champion

- [ ] **Calculate sprint fairness metrics**
  - Fairness story points completed vs. planned
  - Fairness capacity % actual vs. target
  - Number of fairness DoD gates passed on first attempt
  - Number of fairness escalations required
  - Time to resolve fairness issues (average)
  
- [ ] **Trend analysis**
  - Compare to previous sprints
  - Identify improving or worsening patterns
  - Assess team fairness maturity trajectory
  
- [ ] **Report to Technical Fairness Lead**
  - Sprint fairness summary
  - Key achievements and challenges
  - Lessons learned
  - Recommendations for organizational improvements

#### 8.4.3 Knowledge Capture and Sharing

**Responsibility**: Team Fairness Champion + ML Engineer

- [ ] **Document lessons learned**
  - Effective fairness interventions (what worked, what didn't)
  - Estimation insights (what took longer/shorter than expected)
  - Process improvements discovered
  - Tool or methodology innovations
  
- [ ] **Share knowledge with organization**
  - Update team wiki or knowledge base
  - Present at fairness community of practice meeting
  - Contribute to organizational fairness playbook
  - Mentor other teams starting fairness integration
  
- [ ] **Update templates and checklists**
  - Refine story template based on learnings
  - Update estimation guidelines
  - Improve DoD checklist
  - Enhance retrospective questions

#### 8.4.4 Backlog Grooming for Next Sprint

**Responsibility**: Product Owner + Team Fairness Champion

- [ ] **Review fairness backlog**
  - Prioritize carryover fairness work
  - Identify new fairness requirements from roadmap
  - Incorporate learnings into backlog items
  - Estimate upcoming fairness work based on sprint experience
  
- [ ] **Prepare for next sprint planning**
  - Flag high-risk stories requiring early consultation
  - Identify stories needing fairness deep dive in refinement
  - Schedule pre-planning consultations if needed
  - Update fairness risk assessment for backlog items

---

### 8.5 Post-Planning Action Checklist

**Immediate (Within 24 Hours)**:
- [ ] Stakeholder notification completed (Technical Fairness Lead, Legal, Domain Specialists)
- [ ] Cross-team coordination completed
- [ ] Internal team alignment achieved
- [ ] Development environment configured and validated
- [ ] Tools validated and accessible
- [ ] Data readiness verified
- [ ] Sprint board setup with fairness visibility
- [ ] Calendar integration completed (all sessions scheduled)

**Ongoing (Throughout Sprint)**:
- [ ] Daily stand-up fairness integration (2-3 min daily)
- [ ] Mid-sprint fairness checkpoint conducted (Day 4-5)
- [ ] Continuous monitoring and communication maintained
- [ ] Fairness Champion reviews progress daily
- [ ] Weekly reporting to Technical Fairness Lead (high-risk sprints)

**Pre-Sprint Review (Day 8-9)**:
- [ ] Fairness demo prepared
- [ ] Exit criteria pre-check completed
- [ ] Documentation finalized (model cards, FDRs, technical docs)

**Post-Sprint Review (Within 48 Hours)**:
- [ ] Fairness retrospective component conducted (15-30 min)
- [ ] Sprint fairness metrics calculated and analyzed
- [ ] Report to Technical Fairness Lead submitted
- [ ] Lessons learned documented and shared
- [ ] Templates and checklists updated
- [ ] Backlog grooming for next sprint completed

---

## 9. Risk-Based Planning Tiers

### 9.1 Purpose and Scope

Different AI systems carry different levels of risk based on their impact on individuals and society. This section provides tiered guidance for sprint planning based on system risk level, ensuring appropriate rigor without over-engineering low-risk systems.

**Risk Assessment Dimensions**:
1. **Impact Severity**: What's at stake for affected individuals?
2. **Decision Autonomy**: How much human oversight exists?
3. **Scale**: How many people are affected?
4. **Reversibility**: Can harm be easily corrected?
5. **Vulnerability**: Are affected populations vulnerable or marginalized?

---

### 9.2 Risk Level Definitions

#### 9.2.1 Critical Risk Systems

**Definition**: Systems whose failures could result in severe harm to life, liberty, or livelihood with limited recourse.

**Examples**:
- Criminal justice risk assessments (recidivism, bail, sentencing)
- Healthcare diagnosis or treatment recommendations
- Employment hiring or termination decisions
- Child welfare risk assessments
- Asylum or immigration decisions

**Characteristics**:
- High impact severity (life, liberty, livelihood at stake)
- Limited human oversight or rubber-stamping of AI decisions
- Affects vulnerable populations
- Harm difficult or impossible to reverse
- High scale (thousands to millions affected)

**Fairness Planning Requirements**:
- 30-40% sprint capacity for fairness
- Technical Fairness Lead involved in all sprints
- Chief AI Ethics Officer approval for major decisions
- Legal review mandatory
- External audit readiness required
- Extensive intersectional analysis (â‰¥3 attribute combinations)
- Rigorous counterfactual testing (â‰¥500 test cases)
- Quarterly deep-dive fairness evaluations
- Continuous production monitoring with immediate alerts

---



### 9.2.2 High Risk Systems

**Definition**: Systems that significantly impact opportunities, resources, or quality of life, with some human oversight but substantial AI influence.

**Examples**:
- Credit lending decisions (mortgages, loans, credit cards)
- University admissions
- Employee performance evaluation and promotion
- Insurance underwriting (health, life, auto)
- Housing allocation and rental screening
- Public benefits eligibility determination
- Content moderation at scale (hate speech, misinformation)

**Characteristics**:
- Significant impact on opportunities or resources
- Moderate human oversight (review on appeal or sample basis)
- Affects large populations
- Harm reversible but costly or time-consuming
- May affect vulnerable populations

**Fairness Planning Requirements**:
- 25-30% sprint capacity for fairness
- Technical Fairness Lead consultation for high-risk stories
- Legal review for compliance-critical features
- Intersectional analysis (≥2 attribute combinations)
- Counterfactual testing (≥200 test cases)
- Bi-annual deep-dive fairness evaluations
- Production monitoring with daily review

---

#### 9.2.3 Medium Risk Systems

**Definition**: Systems that personalize or customize experiences with moderate impact on user outcomes, with human control retained.

**Examples**:
- Job candidate ranking (with human final decision)
- Educational content recommendation and adaptive learning
- News and information feed ranking
- Customer service routing and prioritization
- Advertising targeting (non-discriminatory categories)
- Fraud detection (with human review)
- Personalized health and fitness recommendations

**Characteristics**:
- Moderate impact on user experience or outcomes
- Strong human oversight or user control
- Users can opt-out or override
- Harm easily reversible
- Broad population (not specifically vulnerable groups)

**Fairness Planning Requirements**:
- 20-25% sprint capacity for fairness
- Technical Fairness Lead consultation as needed
- Intersectional analysis (≥1 attribute combination)
- Counterfactual testing (≥100 test cases for key scenarios)
- Annual deep-dive fairness evaluations
- Production monitoring with weekly review

---

#### 9.2.4 Low Risk Systems

**Definition**: Systems with minimal individual impact, primarily affecting user experience or convenience with full user control.

**Examples**:
- Entertainment content recommendation (movies, music, games)
- Product recommendation (non-essential goods)
- Search ranking (commercial products)
- Personalized UI/UX (themes, layouts, notifications)
- Chatbots for general information
- Spam filtering
- Image and photo enhancement

**Characteristics**:
- Low individual impact (convenience, entertainment)
- Full user control and easy override
- Harm minimal and easily reversible
- Not affecting vulnerable populations specifically
- Primary concern is user satisfaction, not equity

**Fairness Planning Requirements**:
- 15-20% sprint capacity for fairness
- Technical Fairness Lead consultation optional
- Basic disaggregated performance testing
- Intersectional analysis optional (if feasible)
- Counterfactual testing (≥50 test cases, if applicable)
- Periodic fairness evaluations (annually or when major changes)
- Production monitoring with monthly review

---

#### 9.2.5 Minimal Risk / Non-AI Systems

**Definition**: Traditional software systems or AI systems with no differential impact across demographic groups.

**Examples**:
- Internal tools (bug tracking, documentation)
- Infrastructure (load balancing, caching)
- Data processing pipelines (ETL, batch jobs)
- Monitoring and alerting systems
- Non-personalized features (universal UI components)

**Characteristics**:
- No differential impact across groups
- No personalization or decision-making
- Technical functionality only

**Fairness Planning Requirements**:
- 0-5% sprint capacity (only if indirect fairness implications)
- No formal fairness evaluation required
- Basic consideration of accessibility and inclusivity
- No mandatory fairness DoD gates

---

### 9.3 Risk Assessment Worksheet

Use this worksheet during sprint planning to determine the appropriate risk tier for features.

#### Step 1: Impact Assessment

**Question 1: What is at stake for affected individuals?**
- [ ] Life, liberty, or livelihood (employment, housing, healthcare, criminal justice) → **Critical Risk**
- [ ] Significant opportunities or resources (credit, education, insurance) → **High Risk**
- [ ] Moderate impact on experience or outcomes → **Medium Risk**
- [ ] Minimal impact (convenience, entertainment) → **Low Risk**
- [ ] No differential impact → **Minimal Risk**

**Question 2: What is the decision autonomy level?**
- [ ] Fully automated or rubber-stamped by humans → **+1 risk level**
- [ ] Moderate human oversight (review on appeal or sample) → **No change**
- [ ] Strong human oversight or user control → **-1 risk level**

**Question 3: What is the scale of impact?**
- [ ] Millions of people affected → **+1 risk level** (if already High/Critical)
- [ ] Thousands to hundreds of thousands affected → **No change**
- [ ] Hundreds or fewer affected → **-1 risk level** (if Low or Medium)

**Question 4: Is harm easily reversible?**
- [ ] No, harm is permanent or very difficult to reverse → **+1 risk level**
- [ ] Harm reversible but costly or time-consuming → **No change**
- [ ] Harm easily and quickly reversible → **-1 risk level**

**Question 5: Are vulnerable populations specifically affected?**
- [ ] Yes, system specifically targets vulnerable groups → **+1 risk level**
- [ ] System affects general population including some vulnerable groups → **No change**
- [ ] System primarily affects non-vulnerable populations → **-1 risk level**

#### Step 2: Determine Risk Tier

After answering questions above, determine the risk tier:

**Final Risk Tier**: ☐ Critical  ☐ High  ☐ Medium  ☐ Low  ☐ Minimal

**Rationale** (document key factors):
- Primary impact: ___________________________________
- Decision autonomy: ___________________________________
- Key vulnerabilities: ___________________________________

**Approvals Required**:
- [ ] Team Fairness Champion (always required)
- [ ] Technical Fairness Lead (if High or Critical)
- [ ] Chief AI Ethics Officer (if Critical)
- [ ] Legal (if compliance implications)

---

### 9.4 Risk Tier Planning Guidelines Summary

| Risk Tier | Fairness Capacity | Technical Lead Involvement | Key Requirements |
|-----------|-------------------|---------------------------|------------------|
| **Critical** | 30-40% | All sprints, mandatory | External audit readiness, Chief AI Ethics Officer approval, legal review, extensive intersectional analysis, rigorous testing (≥500 counterfactual), continuous monitoring |
| **High** | 25-30% | High-risk stories | Legal review for compliance, intersectional analysis (≥2 combinations), counterfactual testing (≥200), bi-annual evaluations, daily monitoring |
| **Medium** | 20-25% | As needed | Intersectional analysis (≥1 combination), counterfactual testing (≥100), annual evaluations, weekly monitoring |
| **Low** | 15-20% | Optional | Basic disaggregated testing, optional intersectional analysis, counterfactual testing (≥50), annual evaluations, monthly monitoring |
| **Minimal** | 0-5% | Not required | Basic accessibility/inclusivity, no formal fairness gates |

---

## 10. Sprint Templates by System Risk

### 10.1 Purpose

These templates provide pre-configured sprint planning structures based on system risk level, ensuring appropriate rigor and efficiency.

---

### 10.2 Critical Risk System Sprint Template

**Use for**: Criminal justice, healthcare diagnosis, employment hiring, child welfare

#### Pre-Planning (3-5 Days Before)

**Week Before Sprint**:
- [ ] Technical Fairness Lead meeting (60-90 min) - review roadmap and upcoming features
- [ ] Legal consultation scheduled (if new features with compliance implications)
- [ ] External audit preparation materials reviewed
- [ ] Fairness evaluation datasets validated (sample size ≥100 per group, ≥50 per intersection)

**2-3 Days Before Sprint**:
- [ ] Fairness Champion reviews backlog with Technical Fairness Lead
- [ ] High-risk stories flagged and pre-assessed
- [ ] Required consultations scheduled (Domain Specialist, Legal)
- [ ] Capacity allocation pre-approved (30-40% target)

**Day Before Sprint**:
- [ ] All team members review fairness standards and previous sprint outcomes
- [ ] Monitoring dashboard reviewed for production issues
- [ ] Risk assessment updated with any regulatory changes

#### Sprint Planning (3-4 Hours)

**Opening (20 minutes)**:
- Sprint goal presentation with fairness context
- Technical Fairness Lead presents key fairness priorities
- Review of any production fairness incidents or concerns
- Governance mandate review (new regulations, policies)

**Story Review (120-150 minutes)**:
- **Per Story Time**: 20-30 minutes (thorough review required)
- SAFE/FAIR framework completeness check
- Risk assessment with mitigation planning
- Intersectional analysis planning (≥3 attribute combinations)
- Counterfactual testing strategy (≥500 test cases)
- Fairness-performance trade-off discussion
- Escalation path clarification

**Task Breakdown (60 minutes)**:
- Detailed fairness task decomposition
- Explicit consultation tasks (Technical Fairness Lead, Legal, Domain Specialist)
- Documentation tasks (model cards, FDRs, compliance evidence)
- Monitoring and alerting configuration
- External audit preparation tasks

**Commitment (20 minutes)**:
- Technical Fairness Lead confirms feasibility
- Capacity allocation validation (30-40% achieved)
- Communication plan to Chief AI Ethics Officer
- External stakeholder notification plan

#### During Sprint

**Daily Activities**:
- Daily stand-up includes mandatory fairness update (5 min)
- Fairness Champion checks progress on critical path fairness tasks
- Technical Fairness Lead available for quick consultations (15-30 min slots)

**Day 2-3**:
- [ ] Baseline fairness metrics captured and reviewed with Technical Fairness Lead

**Day 4-5 (Mid-Sprint Checkpoint)**:
- [ ] Formal fairness checkpoint with Technical Fairness Lead (60-90 min)
- [ ] Preliminary results reviewed
- [ ] Escalation to Chief AI Ethics Officer if needed
- [ ] Capacity reallocation if necessary

**Day 6-7**:
- [ ] Intersectional analysis results reviewed
- [ ] Counterfactual testing progress assessed
- [ ] FDR drafting begun (if trade-offs identified)

**Day 8-9 (Pre-Demo)**:
- [ ] Complete fairness DoD validation (90 min)
- [ ] Technical Fairness Lead sign-off for all stories
- [ ] External audit evidence collected and organized
- [ ] Legal review completed (if needed)
- [ ] Compliance documentation finalized

**Day 10 (Sprint Review)**:
- [ ] Fairness demo to stakeholders (30-45 min)
- [ ] Technical Fairness Lead presents fairness outcomes
- [ ] Chief AI Ethics Officer informed of major decisions
- [ ] External stakeholders notified (if applicable)

#### Post-Sprint

**Within 24 Hours**:
- [ ] Fairness retrospective with Technical Fairness Lead (45 min)
- [ ] Lessons learned documented
- [ ] Report to Chief AI Ethics Officer (sprint summary)
- [ ] External audit materials archived

**Within 1 Week**:
- [ ] Post-deployment monitoring review (Day 1, Day 3, Day 7)
- [ ] Fairness metrics trend analysis
- [ ] Knowledge sharing session with organization
- [ ] Next sprint high-risk stories identified and pre-planning initiated

---

### 10.3 High Risk System Sprint Template

**Use for**: Credit decisions, university admissions, employee performance evaluation, insurance underwriting

#### Pre-Planning (2-3 Days Before)

**2-3 Days Before Sprint**:
- [ ] Fairness Champion reviews backlog and production monitoring
- [ ] Technical Fairness Lead consultation scheduled for high-risk stories (30-60 min)
- [ ] Legal consultation scheduled if compliance-critical features (60 min)
- [ ] Capacity allocation determined (25-30% target)

**Day Before Sprint**:
- [ ] High-risk stories flagged and pre-assessed
- [ ] Fairness evaluation datasets validated (sample size ≥75 per group)
- [ ] Required domain specialist consultations scheduled

#### Sprint Planning (2.5-3 Hours)

**Opening (15 minutes)**:
- Sprint goal with fairness priorities
- Review production fairness status
- Governance updates (regulations, organizational policies)

**Story Review (90-120 minutes)**:
- **Per Story Time**: 15-20 minutes
- SAFE/FAIR completeness check
- Risk assessment
- Intersectional analysis planning (≥2 attribute combinations)
- Counterfactual testing strategy (≥200 test cases)
- Fairness-performance trade-off discussion

**Task Breakdown (45 minutes)**:
- Fairness task decomposition
- Consultation tasks (Technical Fairness Lead for high-risk stories, Legal if needed)
- Documentation tasks (model cards, FDRs)
- Monitoring configuration

**Commitment (15 minutes)**:
- Capacity validation (25-30% achieved)
- Technical Fairness Lead informed of high-risk work
- Communication plan

#### During Sprint

**Daily Activities**:
- Daily stand-up includes fairness update (3 min)
- Fairness Champion monitors progress

**Day 4-5 (Mid-Sprint Checkpoint)**:
- [ ] Fairness checkpoint (45-60 min)
- [ ] Preliminary results reviewed
- [ ] Technical Fairness Lead consulted if threshold issues

**Day 8-9 (Pre-Demo)**:
- [ ] Fairness DoD validation (60 min)
- [ ] Technical Fairness Lead sign-off for high-risk stories
- [ ] Legal review if needed
- [ ] Compliance documentation completed

**Day 10 (Sprint Review)**:
- [ ] Fairness demo (20-30 min)
- [ ] Stakeholder communication

#### Post-Sprint

**Within 24 Hours**:
- [ ] Fairness retrospective (30 min)
- [ ] Report to Technical Fairness Lead
- [ ] Lessons learned documented

**Within 1 Week**:
- [ ] Post-deployment monitoring (Day 1, Day 7)
- [ ] Next sprint planning preparation

---

### 10.4 Medium Risk System Sprint Template

**Use for**: Job candidate ranking, educational content recommendation, news feed ranking, fraud detection

#### Pre-Planning (1-2 Days Before)

**1-2 Days Before Sprint**:
- [ ] Fairness Champion reviews backlog
- [ ] Production monitoring reviewed for issues
- [ ] Capacity allocation determined (20-25% target)
- [ ] Domain specialist consultation scheduled if needed (30 min)

**Day Before Sprint**:
- [ ] Fairness evaluation datasets validated (sample size ≥50 per group)
- [ ] High-priority fairness work identified

#### Sprint Planning (2-2.5 Hours)

**Opening (10 minutes)**:
- Sprint goal with fairness context
- Production fairness status

**Story Review (60-90 minutes)**:
- **Per Story Time**: 10-15 minutes
- SAFE/FAIR completeness check
- Basic risk assessment
- Intersectional analysis planning (≥1 attribute combination)
- Counterfactual testing strategy (≥100 test cases)

**Task Breakdown (30 minutes)**:
- Fairness task decomposition
- Documentation tasks (model cards)
- Monitoring configuration

**Commitment (10 minutes)**:
- Capacity validation (20-25% achieved)

#### During Sprint

**Daily Activities**:
- Daily stand-up includes fairness update (2 min)

**Day 4-5 (Mid-Sprint Checkpoint)**:
- [ ] Fairness checkpoint (30-45 min)
- [ ] Preliminary results reviewed

**Day 9 (Pre-Demo)**:
- [ ] Fairness DoD validation (45 min)
- [ ] Technical Fairness Lead consulted if issues

**Day 10 (Sprint Review)**:
- [ ] Fairness demo (15-20 min)

#### Post-Sprint

**Within 48 Hours**:
- [ ] Fairness retrospective (20 min)
- [ ] Lessons learned documented

---

### 10.5 Low Risk System Sprint Template

**Use for**: Entertainment recommendation, product recommendation, personalized UI/UX

#### Pre-Planning (1 Day Before)

**Day Before Sprint**:
- [ ] Fairness Champion reviews backlog
- [ ] Capacity allocation determined (15-20% target)
- [ ] Basic fairness datasets validated

#### Sprint Planning (1.5-2 Hours)

**Opening (5 minutes)**:
- Sprint goal mention of fairness work

**Story Review (45-60 minutes)**:
- **Per Story Time**: 5-10 minutes
- Basic SAFE framework check
- Disaggregated testing planning
- Basic counterfactual testing if applicable (≥50 test cases)

**Task Breakdown (20 minutes)**:
- Basic fairness tasks
- Simple documentation

**Commitment (5 minutes)**:
- Capacity validation (15-20% achieved)

#### During Sprint

**Day 5 (Mid-Sprint Check)**:
- [ ] Quick fairness checkpoint (15-30 min)

**Day 9 (Pre-Demo)**:
- [ ] Basic fairness DoD validation (30 min)

**Day 10 (Sprint Review)**:
- [ ] Brief fairness mention in demo (5-10 min)

#### Post-Sprint

**Within 48 Hours**:
- [ ] Brief fairness retrospective (15 min)

---

### 10.6 Template Selection Guide

**Use this decision tree to select the appropriate template**:

1. **What is the system risk level?** (Use Section 9.3 Risk Assessment Worksheet)
   - Critical → Use Section 10.2
   - High → Use Section 10.3
   - Medium → Use Section 10.4
   - Low → Use Section 10.5
   - Minimal → No formal template needed

2. **Is this the first sprint for this AI feature?**
   - Yes → Add 5-10% more fairness capacity for baseline establishment
   - No → Use standard allocation

3. **Are there new regulatory requirements?**
   - Yes → Escalate one risk level for this sprint (e.g., High → Critical planning rigor)
   - No → Use standard template

4. **Has there been a recent production fairness incident?**
   - Yes → Add enhanced monitoring tasks and 10-15% more capacity
   - No → Use standard template

---

## 11. Common Pitfalls and Solutions

### 11.1 Estimation and Planning Pitfalls

#### Pitfall 1: Underestimating Fairness Work Complexity

**Symptoms**:
- Fairness tasks consistently spill over to next sprint
- Team frequently works overtime on fairness testing
- Fairness DoD gates block story completion at last minute

**Root Causes**:
- Treating fairness as "checkbox" rather than substantial engineering work
- Not accounting for iterative nature of bias mitigation
- Underestimating intersectional analysis complexity
- Forgetting documentation time (model cards, FDRs)

**Solutions**:
- **Estimation Rule of Thumb**: Fairness work typically 20-40% of functional work for AI features
- **Use Historical Data**: Track actual vs. estimated fairness work; calibrate estimates quarterly
- **Explicit Breakdown**: Always decompose fairness work into subtasks during planning
  - Data bias audit: X points
  - Intervention implementation: Y points
  - Testing (disaggregated, intersectional, counterfactual, red-team, proxy): Z points
  - Documentation: W points
  - Monitoring: V points
- **Buffer Allocation**: Reserve 10-15% of fairness capacity for unexpected complexity
- **Early Warning System**: Flag at mid-sprint checkpoint if fairness work >50% complete

**Example Fix**:
- **Before**: "Story: Build credit scoring model - 8 points (includes fairness)"
- **After**: "Story: Build credit scoring model - Functional: 8 points, Fairness: 4 points (data audit: 1, intervention: 1.5, testing: 1, docs: 0.5) - Total: 12 points"

---

#### Pitfall 2: Planning Fairness Work Too Late in Sprint

**Symptoms**:
- Fairness testing starts on Day 8-9 of 10-day sprint
- No time to iterate if thresholds not met
- Rushed documentation and FDRs
- Stories fail Fairness DoD at last minute

**Root Causes**:
- Treating fairness as final QA step rather than integral development activity
- Waiting for "complete" feature before fairness evaluation
- Sequential rather than parallel work planning

**Solutions**:
- **Parallel Planning**: Schedule fairness work alongside functional work, not after
  - Day 1-2: Functional development **AND** data bias audit
  - Day 3-5: Feature implementation **AND** fairness intervention implementation
  - Day 6-7: Functional testing **AND** fairness testing
  - Day 8-9: Integration **AND** documentation
- **Early Baseline**: Capture baseline fairness metrics on Day 1-2 using existing/similar models
- **Iterative Evaluation**: Test fairness at each development milestone, not just end
- **Front-Load Risky Work**: Schedule highest-risk fairness work (intersectional analysis, counterfactual testing) for Days 4-6, not Days 8-9

**Example Fix**:
- **Before**: Days 1-7 functional dev, Days 8-10 fairness testing
- **After**: 
  - Days 1-2: Functional setup + data bias audit
  - Days 3-5: Feature dev + fairness intervention
  - Days 6-7: Testing (functional + fairness in parallel)
  - Days 8-9: Integration + documentation
  - Day 10: Demo prep

---

#### Pitfall 3: Inadequate Capacity Allocation

**Symptoms**:
- Fairness capacity consistently <15% of sprint
- Fairness work treated as "if we have time"
- Technical debt accumulation in fairness domain
- Frequent fairness DoD waivers or exceptions

**Root Causes**:
- Pressure to maximize feature velocity
- Lack of organizational commitment to fairness
- Treating fairness as "nice to have" rather than requirement
- Product Owner unfamiliar with fairness requirements

**Solutions**:
- **Mandatory Minimum**: Set organizational policy for minimum fairness capacity (15-30% based on risk)
- **Governance Backing**: Technical Fairness Lead or Chief AI Ethics Officer enforces capacity allocation
- **Velocity Adjustment**: Count fairness points toward team velocity; make visible in reporting
- **Product Owner Education**: Train Product Owners on fairness requirements and compliance implications
- **Risk-Based Allocation**: Use Section 9 risk tiers to determine non-negotiable capacity levels

**Example Fix**:
- **Before**: 40-point sprint, 4 points (10%) fairness work, frequently deferred
- **After**: 40-point sprint, 10 points (25%) fairness work for high-risk system, protected by governance policy, Product Owner educated on compliance necessity

---

### 11.2 Technical Execution Pitfalls

#### Pitfall 4: Insufficient Data for Fairness Evaluation

**Symptoms**:
- Protected attribute data unavailable or low quality
- Sample sizes too small for reliable evaluation (<50 per group)
- Intersectional subgroups have <10 samples
- Cannot compute fairness metrics due to data gaps

**Root Causes**:
- Data collection not prioritized in product design
- Privacy concerns not balanced with fairness needs
- Demographic data not collected historically
- Edge cases and rare intersections not considered

**Solutions**:
- **Data Requirements in DoR (Definition of Ready)**: Story cannot be planned without:
  - Protected attribute data availability confirmed
  - Sample size sufficiency validated (≥50 per group, ≥100 preferred)
  - Intersectional subgroups identified with sample sizes
  - Data quality assessment completed
- **Synthetic Data Strategy**: When real data insufficient, generate synthetic data preserving statistical properties
- **Privacy-Preserving Collection**: Use techniques like federated learning, differential privacy, or aggregate-only analysis
- **Proxy Analysis Fallback**: If protected attributes unavailable, analyze proxy variables (with explicit documentation of limitations)
- **Minimum Viable Population**: Define minimum sample sizes in organizational fairness standards; defer features if not met

**Example Fix**:
- **Before**: Start sprint, discover demographic data unavailable on Day 6
- **After**: Pre-planning data readiness check; identify gap; defer story or implement privacy-preserving data collection before sprint

---

#### Pitfall 5: Fairness-Performance Trade-off Paralysis

**Symptoms**:
- Team stuck debating acceptable accuracy loss
- Fairness thresholds not achieved but no escalation
- Stories blocked for entire sprint on trade-off decision
- Inconsistent trade-off decisions across stories

**Root Causes**:
- No pre-defined organizational trade-off guidance
- Unclear escalation path or decision authority
- Fear of making "wrong" decision
- Lack of stakeholder input on trade-off priorities

**Solutions**:
- **Pre-Defined Trade-off Thresholds**: Organizational guidance on acceptable performance loss
  - Example: "Up to 3% accuracy loss acceptable for achieving fairness thresholds in high-risk systems"
- **Early Escalation Protocol**: Escalate to Technical Fairness Lead within 1 day of identifying threshold risk, not at sprint end
- **Decision Matrix**: Use framework for trade-off decisions:
  - If performance loss <X% and fairness threshold achieved → Proceed
  - If performance loss X-Y% and fairness threshold achieved → Technical Fairness Lead approval
  - If performance loss >Y% → Chief AI Ethics Officer decision
- **FDR for Major Trade-offs**: Document rationale, alternatives considered, stakeholder input, approval
- **Time-Boxed Exploration**: Allocate 2-3 days for intervention exploration; escalate if no solution found

**Example Fix**:
- **Before**: Team debates accuracy vs. fairness for 5 days, misses sprint commitment
- **After**: Day 3 - identify 4% accuracy loss needed for fairness threshold; Day 4 - escalate to Technical Fairness Lead per policy; Day 5 - approved via FDR; proceed with implementation

---

#### Pitfall 6: Inadequate Intersectional Analysis

**Symptoms**:
- Only single-attribute fairness evaluated (e.g., gender, not gender × race)
- Multiply-marginalized groups overlooked
- Fairness violations discovered post-deployment for intersections
- User complaints from intersectional groups

**Root Causes**:
- Complexity of intersectional analysis underestimated
- Sample size challenges for intersections
- Lack of understanding of intersectionality importance
- Tooling doesn't support intersectional evaluation

**Solutions**:
- **Mandatory Intersections by Risk Level**:
  - Critical/High Risk: ≥2-3 intersections (e.g., gender × race, age × disability)
  - Medium Risk: ≥1 intersection
  - Low Risk: Optional but encouraged
- **Early Intersection Identification**: During story refinement, explicitly list key intersections to evaluate
- **Sample Size Planning**: Ensure ≥50 samples per intersection (may require oversampling or synthetic data)
- **Worst-Case Gap Metric**: Track maximum fairness gap across all intersections (not just average)
- **Tooling Investment**: Implement or procure fairness evaluation tools supporting intersectional analysis
- **Consultation**: Engage Domain Specialists to identify most vulnerable intersections

**Example Fix**:
- **Before**: Evaluate gender fairness only; deploy; discover disparity for Black women specifically
- **After**: Pre-planning - identify gender × race as key intersection; ensure data availability; test before deployment; discover and mitigate issue before launch

---

### 11.3 Process and Communication Pitfalls

#### Pitfall 7: Fairness Champion Bottleneck

**Symptoms**:
- Fairness Champion overwhelmed, blocking progress
- Fairness work waits for Fairness Champion availability
- Fairness Champion working 40+ hours/week on fairness (if 20% role)
- Other team members deskilled on fairness

**Root Causes**:
- Fairness Champion doing all fairness work, not just coordination
- Lack of shared fairness responsibility across team
- Insufficient fairness training for other team members
- Unclear RACI (Fairness Champion Accountable for everything)

**Solutions**:
- **Distributed Responsibility**: RACI clarification
  - Fairness Champion: Accountable (approves, coordinates, guides), not Responsible for all work
  - ML Engineers: Responsible for implementation, testing
  - QA Engineers: Responsible for fairness test execution
  - Product Owner: Responsible for priority decisions
- **Team Training**: Invest in fairness training for all team members (not just Champion)
- **Pair Programming**: Fairness Champion pairs with ML Engineers, gradually transferring skills
- **Capacity Monitoring**: If Fairness Champion >30% capacity on fairness, escalate to leadership for team upskilling or additional support
- **Documentation**: Create team-specific fairness playbook reducing need for Champion consultation on routine decisions

**Example Fix**:
- **Before**: Fairness Champion does all bias audits, testing, documentation; works 60 hours/week
- **After**: ML Engineers do bias audits and testing (Champion reviews); QA Engineers execute fairness tests; Champion coordinates and approves (20 hours/week)

---

#### Pitfall 8: Inadequate Stakeholder Communication

**Symptoms**:
- Technical Fairness Lead surprised by decisions at sprint review
- Legal discovers compliance issues post-deployment
- Product Owner unaware of fairness-performance trade-offs
- Users surprised by fairness limitations or safeguards

**Root Causes**:
- Communication plan not established during sprint planning
- Treating fairness as technical detail not strategic concern
- Escalations happening too late
- Stakeholders not understanding their RACI role

**Solutions**:
- **Communication Plan in Sprint Planning**: Explicitly plan stakeholder communication
  - Who needs to be informed? (per RACI Informed)
  - Who needs to be consulted? (per RACI Consulted)
  - When? (upfront, mid-sprint, pre-demo, post-demo)
  - How? (email, meeting, dashboard, demo)
- **Proactive Escalation**: Don't wait for sprint review; escalate issues within 24-48 hours of identification
- **Regular Updates**: For high-risk systems, weekly updates to Technical Fairness Lead
- **Demo Preparation**: Ensure stakeholders see fairness demo before sprint review (no surprises)
- **User-Facing Communication**: Plan user disclosures or documentation updates alongside feature work

**Example Fix**:
- **Before**: Major fairness-performance trade-off decided by team; Technical Fairness Lead learns at sprint review; objects; rework required
- **After**: Day 3 - identify trade-off; Day 4 - consult Technical Fairness Lead; Day 5 - FDR approved; proceed with informed stakeholder buy-in

---

#### Pitfall 9: Documentation Debt

**Symptoms**:
- Model cards outdated or incomplete
- FDRs created but not maintained
- Fairness decisions undocumented, institutional knowledge lost
- Audit trail gaps

**Root Causes**:
- Documentation treated as post-sprint activity, often skipped
- Underestimating documentation time
- No template or guidance for model cards/FDRs
- Documentation not enforced in Fairness DoD

**Solutions**:
- **Documentation in DoD**: Non-negotiable Fairness DoD criteria (Section 4.2.3)
  - Model card updated and reviewed
  - FDR created if trade-offs or exceptions
  - Technical documentation complete
- **Explicit Story Points**: Allocate 0.5-1 point per story for documentation
- **Living Documentation**: Update incrementally throughout sprint, not at end
  - Day 1-2: Draft model card sections
  - Day 3-5: Update as decisions made
  - Day 8-9: Finalize and review
- **Templates and Tools**: Provide easy-to-use templates (see Appendix)
- **Automated Tooling**: Integrate model cards into CI/CD; auto-populate what's possible (metrics, datasets)
- **Fairness Champion Review**: Champion reviews documentation before approving Fairness DoD

**Example Fix**:
- **Before**: Sprint ends, documentation deferred, never completed
- **After**: Documentation tasks explicit in sprint plan; 1 point allocated; incrementally updated; reviewed before Fairness DoD approval

---

#### Pitfall 10: Ignoring Production Monitoring

**Symptoms**:
- Fairness metrics degrade in production unnoticed
- Alerts configured but never reviewed
- Dashboard exists but no one looks at it
- Fairness drift discovered months later via user complaints or audit

**Root Causes**:
- Monitoring treated as "set and forget"
- No clear owner for ongoing fairness monitoring
- Alert fatigue (too many low-priority alerts)
- Monitoring not integrated into operational rhythms

**Solutions**:
- **Monitoring Ownership**: Explicit RACI for production fairness monitoring
  - Daily review: On-call engineer or ML Engineer
  - Weekly review: Team Fairness Champion
  - Monthly deep-dive: Technical Fairness Lead (for high-risk systems)
- **Alert Prioritization**: Three-tier alerting
  - Critical (immediate): Fairness threshold violation >50% (e.g., TPR gap 0.045 when threshold 0.03)
  - Major (daily review): Fairness threshold violation 10-50%
  - Minor (weekly review): Drift >5% from baseline
- **Operational Integration**: Add fairness monitoring to:
  - Daily stand-ups: "Any fairness alerts?"
  - Weekly team meetings: Quick dashboard review
  - Monthly SRE/ops reviews: Fairness trends
- **Automated Reporting**: Weekly fairness monitoring summary emailed to team and Technical Fairness Lead
- **Scheduled Re-evaluation**: Quarterly deep-dive fairness evaluation (not just passive monitoring)

**Example Fix**:
- **Before**: Dashboard created; no one assigned to monitor; drift unnoticed for 3 months
- **After**: ML Engineer on-call reviews daily; Fairness Champion reviews weekly; automated weekly report; monthly deep-dive scheduled; drift caught within 1 week

---

### 11.4 Pitfall Prevention Checklist

Use this checklist during sprint planning and retrospectives to prevent common pitfalls:

**Estimation and Planning**:
- [ ] Fairness work explicitly estimated and broken down (Pitfall 1)
- [ ] Fairness work scheduled in parallel with functional work, not sequentially (Pitfall 2)
- [ ] Fairness capacity allocation meets risk-based target (Pitfall 3)
- [ ] Buffer allocated for unexpected fairness complexity (10-15%)

**Technical Execution**:
- [ ] Data readiness validated before sprint (sample sizes, quality) (Pitfall 4)
- [ ] Trade-off escalation protocol clarified and early escalation planned (Pitfall 5)
- [ ] Key intersections identified and sample sizes confirmed (Pitfall 6)

**Process and Communication**:
- [ ] RACI clarified with distributed fairness responsibility (Pitfall 7)
- [ ] Stakeholder communication plan established (who, when, how) (Pitfall 8)
- [ ] Documentation tasks explicit with story points allocated (Pitfall 9)
- [ ] Production monitoring ownership assigned and review rhythm established (Pitfall 10)

---

## 12. Appendices

### 12.1 Appendix A: Glossary of Terms

**Accountable (RACI)**: The person ultimately answerable for the correct and thorough completion of a task; has veto power; only one person can be Accountable per task.

**Adversarial Debiasing**: A machine learning technique using adversarial networks to remove bias by making it difficult for a model to predict protected attributes from learned representations.

**Baseline Fairness Metrics**: Fairness metrics measured before any intervention, providing a comparison point for evaluating improvement.

**Calibration**: A fairness metric requiring that predicted probabilities match actual outcome rates across groups (e.g., if model predicts 70% probability of success, 70% should actually succeed in each group).

**Consulted (RACI)**: A person whose input is sought before a decision is made or action taken; two-way communication.

**Counterfactual Testing**: A testing approach that changes only protected attributes in test cases to verify the model's predictions remain stable and fair.

**Critical Risk System**: AI systems whose failures could result in severe harm to life, liberty, or livelihood with limited recourse (e.g., criminal justice, healthcare diagnosis).

**Definition of Done (DoD)**: Shared understanding of what it means for a story to be complete; includes functional and fairness criteria.

**Definition of Ready (DoR)**: Shared understanding of when a story has sufficient detail to be planned and worked on.

**Demographic Parity**: A fairness metric requiring that the positive prediction rate (or selection rate) is equal across protected groups.

**Disaggregated Performance Testing**: Evaluating model performance separately for each demographic group rather than only overall.

**Equal Opportunity**: A fairness metric requiring that the true positive rate (sensitivity/recall) is equal across protected groups.

**Equalized Odds**: A fairness metric requiring that both true positive rates and false positive rates are equal across protected groups.

**FAIR Acceptance Criteria**: Framework for defining fairness acceptance criteria - Fairness metrics thresholds, Auditing requirements, Intersectional analysis, Reporting guidelines.

**Fairness Champion**: Designated team member responsible for coordinating fairness work and ensuring fairness standards are met (typically 10-20% of their time).

**Fairness Decision Record (FDR)**: Documentation of significant fairness decisions, trade-offs, alternatives considered, stakeholder consultations, and approvals.

**Fairness DoD Gate**: Mandatory checkpoint where Fairness Champion verifies all fairness Definition of Done criteria are met before story completion.

**High Risk System**: AI systems that significantly impact opportunities, resources, or quality of life with some human oversight (e.g., credit lending, university admissions).

**Individual Fairness**: A fairness concept requiring that similar individuals receive similar treatment by the AI system.

**Informed (RACI)**: A person kept up-to-date on progress and decisions; one-way communication for awareness.

**Intersectional Analysis**: Evaluating fairness for individuals belonging to multiple protected groups simultaneously (e.g., gender × race) to identify disproportionate impact on multiply-marginalized populations.

**Low Risk System**: AI systems with minimal individual impact, primarily affecting user experience or convenience with full user control (e.g., entertainment recommendation).

**Medium Risk System**: AI systems that personalize experiences with moderate impact on user outcomes, with human control retained (e.g., job candidate ranking with human decision).

**Model Card**: Standardized documentation for machine learning models including intended use, performance metrics, fairness properties, limitations, and evaluation details.

**Multiply-Marginalized Groups**: Individuals belonging to multiple protected or disadvantaged groups (e.g., older Black women with disabilities).

**Post-Processing Intervention**: Fairness interventions applied after model training, such as threshold optimization or score adjustment.

**Pre-Processing Intervention**: Fairness interventions applied to training data before model training, such as resampling or reweighting.

**Protected Attributes**: Characteristics legally or ethically protected from discrimination, such as race, gender, age, disability, religion.

**Proxy Variables**: Variables correlated with protected attributes that could indirectly enable discrimination (e.g., zip code as proxy for race).

**RACI Matrix**: Responsibility Assignment Matrix defining Responsible, Accountable, Consulted, and Informed roles for each task or decision.

**Red-Team Testing**: Adversarial testing designed to find vulnerabilities, including attempts to exploit fairness weaknesses.

**Responsible (RACI)**: The person who does the work to complete the task; can be multiple people.

**SAFE Framework**: Framework for defining fairness in user stories - Specific protected attributes, Actionable fairness definitions, Feature integration points, Expected outcome measures.

**Technical Fairness Lead**: Organizational role providing expertise and oversight on fairness across teams; approves major fairness decisions.

**Threshold Optimization**: A post-processing technique adjusting decision thresholds differently for different groups to achieve fairness.

---

### 12.2 Appendix B: User Story Fairness Template

Use this template when writing user stories for AI features requiring fairness consideration:

```
**Story Title**: [Concise description]

**As a** [user type]  
**I want** [functionality]  
**So that** [benefit/value]

**SAFE Framework**:

**S - Specific Protected Attributes**:
- Primary attributes: [e.g., race, gender, age, disability]
- Domain-specific attributes: [e.g., socioeconomic status, first-generation]
- Key intersections: [e.g., gender × race, age × disability]
- Proxy risks: [e.g., zip code, name, language]

**A - Actionable Fairness Definition**:
- Primary metric: [e.g., Equal Opportunity (TPR parity)]
- Threshold: [e.g., TPR difference ≤0.03 across groups]
- Secondary metrics: [e.g., Demographic Parity, Calibration]
- Justification: [Why this metric appropriate for this use case]

**F - Feature Integration Points**:
- Data pipeline: [Where fairness checks needed in data processing]
- Model: [Fairness intervention approach - pre/in/post-processing]
- API: [Fairness metric logging, monitoring hooks]
- UI: [User-facing disclosures, controls, explanations]

**E - Expected Outcome Measures**:
- Fairness metrics: [Specific targets, e.g., TPR gap ≤0.03]
- Performance metrics: [Acceptable performance levels, e.g., accuracy ≥85%]
- Business metrics: [Impact on KPIs]

**FAIR Acceptance Criteria**:

**F - Fairness Metrics Thresholds**:
- [ ] TPR parity across [protected groups] within ±0.03
- [ ] Demographic parity across [protected groups] within ±0.05
- [ ] Intersectional gap (worst-case) ≤0.04
- [ ] [Other specific thresholds]

**A - Auditing Requirements**:
- [ ] Disaggregated performance testing completed (all groups, n≥50)
- [ ] Intersectional analysis for [specific intersections] completed
- [ ] Counterfactual testing with ≥[number] test cases
- [ ] Red-team testing for adversarial inputs
- [ ] Proxy variable analysis completed

**I - Intersectional Analysis**:
- [ ] Key intersections evaluated: [list specific combinations]
- [ ] Minimum sample size met (≥50 per intersection)
- [ ] Worst-case intersectional gap documented
- [ ] Multiply-marginalized groups specifically assessed

**R - Reporting Guidelines**:
- [ ] Model card updated with fairness properties
- [ ] Fairness Decision Record created (if trade-offs made)
- [ ] Dashboard updated with disaggregated metrics
- [ ] Limitations and safeguards documented
- [ ] Monitoring configured (metrics, alerts, thresholds)

**Risk Assessment**:
- System risk level: [Critical/High/Medium/Low]
- Impact if fairness fails: [Describe potential harm]
- Affected population: [Who is impacted]
- Mitigation strategies: [Key safeguards]

**Dependencies**:
- Data: [Protected attribute data, sample sizes]
- Tools: [Fairness evaluation framework, monitoring]
- People: [Technical Fairness Lead consultation, Legal review]

**Consultation Required**:
- [ ] Technical Fairness Lead (timing: [when])
- [ ] Legal (timing: [when])
- [ ] Domain Specialist (timing: [when])

**Estimated Story Points**:
- Functional work: [X] points
- Fairness work: [Y] points
  - Data bias audit: [A] points
  - Fairness intervention: [B] points
  - Testing and evaluation: [C] points
  - Documentation: [D] points
  - Monitoring: [E] points
- Total: [X+Y] points
```

---

### 12.3 Appendix C: Fairness Decision Record (FDR) Template

Use this template when documenting significant fairness decisions, especially trade-offs:

```
**Fairness Decision Record (FDR)**

**FDR ID**: FDR-[YYYY-MM-DD]-[SequenceNumber]  
**Date**: [Date]  
**Status**: [Draft/Under Review/Approved/Superseded]  
**System/Feature**: [Name and description]  
**Risk Level**: [Critical/High/Medium/Low]

---

**1. Decision Summary**

**What decision was made?**
[One-sentence summary of the decision]

**Why was this decision necessary?**
[Brief context - what problem or trade-off prompted this decision]

---

**2. Context and Background**

**Feature Description**:
[What does the feature do? Who does it affect?]

**Fairness Challenge**:
[What fairness issue arose? Why couldn't standard approaches resolve it?]

**Stakeholders Affected**:
[Which user groups, demographic groups, or business stakeholders affected]

---

**3. Options Considered**

**Option 1**: [Name]
- Description: [What is this approach?]
- Pros: [Advantages]
- Cons: [Disadvantages]
- Fairness metrics: [Expected fairness performance]
- Performance metrics: [Expected model performance]
- Business impact: [Effect on KPIs]

**Option 2**: [Name]
- Description: [What is this approach?]
- Pros: [Advantages]
- Cons: [Disadvantages]
- Fairness metrics: [Expected fairness performance]
- Performance metrics: [Expected model performance]
- Business impact: [Effect on KPIs]

**Option 3**: [Name] (if applicable)
- [Same structure as above]

---

**4. Decision and Rationale**

**Selected Option**: [Option X]

**Rationale**:
[Why was this option chosen? What factors were most important? How were competing values balanced?]

**Key Trade-offs Accepted**:
- [e.g., 3% accuracy loss for 0.02 reduction in TPR gap]
- [e.g., Slightly higher computational cost for better fairness]

**Why Trade-offs Acceptable**:
[Explain why benefits outweigh costs; reference organizational values, legal requirements, ethical principles]

---

**5. Stakeholder Consultation**

**Consulted** (RACI - C):
- [Name, Role]: [Input provided, date]
- [Name, Role]: [Input provided, date]

**Informed** (RACI - I):
- [Name, Role]: [Informed on date]
- [Name, Role]: [Informed on date]

**Key Objections or Concerns Raised**:
[Any dissenting views or concerns? How were they addressed or mitigated?]

---

**6. Implementation Details**

**Fairness Intervention Applied**:
[Technical details of the chosen approach]

**Fairness Metrics Achieved**:
- Primary metric: [e.g., TPR parity = 0.027 (threshold 0.03)]
- Secondary metrics: [Values]
- Intersectional analysis: [Worst-case gap = X]

**Performance Impact**:
- Accuracy: [e.g., 87% (vs. 90% without intervention)]
- Latency: [e.g., +50ms]
- Other: [Any other performance impacts]

**Business Metrics Impact**:
- [e.g., Approval rate reduced by 2%]
- [e.g., User satisfaction unchanged]

---

**7. Limitations and Safeguards**

**Known Limitations**:
- [e.g., Insufficient data for [specific subgroup]]
- [e.g., Fairness intervention less effective for [scenario]]

**Safeguards Implemented**:
- [e.g., Human review for [edge cases]]
- [e.g., Enhanced monitoring for [at-risk groups]]
- [e.g., User disclosure of [limitations]]

**Ongoing Monitoring**:
- Metrics monitored: [List key metrics]
- Review frequency: [Daily/Weekly/Monthly]
- Escalation triggers: [When to re-evaluate decision]

---

**8. Approval and Sign-off**

**Accountable** (RACI - A):
- [Name, Role, Title]: ________________________  Date: __________
  - [ ] Approved  [ ] Rejected  [ ] Approved with conditions

**Conditions** (if applicable):
[Any conditions attached to approval, e.g., additional monitoring, re-evaluation timeline]

**Consulted** (RACI - C) - Acknowledgment:
- [Name, Role]: Consulted and input incorporated - Date: __________
- [Name, Role]: Consulted and input incorporated - Date: __________

---

**9. Review and Maintenance**

**Next Review Date**: [Date - typically 3-6 months or at next major feature update]

**Review Triggers**:
- [ ] Scheduled review date reached
- [ ] Fairness metrics degrade beyond acceptable limits
- [ ] Regulatory or policy changes
- [ ] User complaints or incidents related to fairness
- [ ] New data or evidence suggests decision should be reconsidered

**Superseded By**: [FDR ID if this decision later revised]

---

**10. Attachments and References**

- Link to user story: [URL]
- Link to evaluation report: [URL]
- Link to model card: [URL]
- Link to monitoring dashboard: [URL]
- Related FDRs: [FDR IDs]
- External references: [Papers, regulations, standards cited]
```

---

### 12.4 Appendix D: Model Card Fairness Section Template

Add this section to your organization's model card template:

```
**Fairness Properties**

**Protected Attributes Considered**:
- Primary attributes: [e.g., race, gender, age]
- Domain-specific: [e.g., socioeconomic status]
- Proxies analyzed: [e.g., zip code, name patterns]

**Fairness Metrics**:
- Primary metric: [e.g., Equal Opportunity (True Positive Rate parity)]
- Threshold: [e.g., TPR difference ≤0.03]
- Current performance:
  - Group A: [TPR = 0.85]
  - Group B: [TPR = 0.87]
  - Gap: [0.02, within threshold]

**Intersectional Analysis**:
- Key intersections evaluated: [e.g., gender × race]
- Worst-case gap: [e.g., 0.038 for Hispanic women vs. White men]
- Sample sizes: [Group A: n=150, Group B: n=120, etc.]

**Fairness Interventions Applied**:
- Pre-processing: [e.g., Resampling to balance training data]
- In-processing: [e.g., Adversarial debiasing during training]
- Post-processing: [e.g., Threshold optimization per group]

**Known Fairness Limitations**:
- [e.g., Limited data for Asian American subgroups (n=45)]
- [e.g., Fairness metrics optimized for binary gender; non-binary outcomes not separately evaluated due to sample size (n=12)]
- [e.g., Proxy variable 'zip code' remains in feature set due to strong predictive value; monitored for proxy discrimination]

**Mitigation Strategies for Limitations**:
- [e.g., Human review for all decisions affecting Asian American applicants]
- [e.g., Opt-in self-identification for non-binary individuals with manual review]
- [e.g., Monthly audit of zip code impact on protected groups]

**Fairness Monitoring**:
- Metrics tracked: [List of metrics logged in production]
- Monitoring frequency: [Daily aggregation, weekly review]
- Alert thresholds: [Critical: TPR gap >0.05, Major: TPR gap >0.04]
- Dashboard: [Link to monitoring dashboard]

**Re-evaluation Schedule**:
- Next fairness evaluation: [Date]
- Trigger conditions: [Performance drift >5%, policy changes, user complaints]

**Related Documentation**:
- Fairness Decision Records: [List FDR IDs]
- Evaluation reports: [Links]
- Regulatory compliance: [Relevant regulations met]
```

---

### 12.5 Appendix E: Sprint Fairness Metrics Dashboard

Track these metrics to monitor and improve fairness integration over time:

**Sprint-Level Metrics**:

1. **Fairness Capacity Allocation**
   - Target: [Based on risk level, e.g., 25-30%]
   - Actual: [% of sprint capacity spent on fairness work]
   - Trend: [Improving/Stable/Declining]

2. **Fairness DoD Pass Rate (First Attempt)**
   - Target: ≥80%
   - Actual: [% of stories passing Fairness DoD without rework]
   - Trend: [Improving/Stable/Declining]

3. **Fairness Escalations**
   - Count: [Number of escalations to Technical Fairness Lead this sprint]
   - Resolution time: [Average days to resolve]
   - Outcome: [Approved/Mitigated/Deferred]

4. **Estimation Accuracy**
   - Fairness work estimated: [Points]
   - Fairness work actual: [Points]
   - Variance: [Percentage over/under]

5. **Documentation Completeness**
   - Model cards updated: [Count]
   - FDRs created: [Count]
   - Documentation incomplete: [Count - should be 0]

**Feature-Level Metrics**:

6. **Fairness Threshold Achievement**
   - Stories meeting primary fairness threshold: [%]
   - Average gap to threshold: [e.g., TPR gap 0.025 vs. 0.03 threshold]
   - Fairness-performance trade-off magnitude: [e.g., -2.5% accuracy]

7. **Intersectional Analysis Coverage**
   - Intersections evaluated: [Count]
   - Worst-case intersectional gap: [Value]
   - Sample size sufficiency: [% of intersections with n≥50]

8. **Testing Coverage**
   - Disaggregated testing: [% of stories]
   - Counterfactual testing: [% of applicable stories]
   - Red-team testing: [% of high-risk stories]
   - Proxy analysis: [% of stories]

**Production Metrics**:

9. **Post-Deployment Fairness Stability**
   - Fairness drift from pre-deployment: [%]
   - Fairness alerts triggered: [Count - Critical/Major/Minor]
   - Mean time to detect fairness issues: [Days]
   - Mean time to resolve fairness issues: [Days]

10. **User Impact**
    - User complaints related to fairness: [Count]
    - Feature usage by demographic groups: [Distribution]
    - User satisfaction by demographic groups: [Scores]

**Organizational Maturity Metrics**:

11. **Team Fairness Maturity**
    - Fairness Champion availability: [% time spent]
    - Team members trained on fairness: [%]
    - Fairness knowledge sharing sessions: [Count this quarter]

12. **Process Improvement**
    - Common pitfalls avoided: [Count from Section 11]
    - Process improvements implemented: [Count]
    - Retrospective action items completed: [%]

---

### 12.6 Appendix F: Fairness Consultation Request Template

Use this template when requesting consultation from Technical Fairness Lead, Legal, or Domain Specialists:

```
**Fairness Consultation Request**

**Requestor**: [Name, Team]  
**Date**: [Date]  
**Urgency**: [Routine/High/Critical]  
**Requested Consultation By**: [Date needed]

---

**Consultation Type**:
- [ ] Technical Fairness Lead
- [ ] Legal
- [ ] Domain Specialist ([specify domain])
- [ ] Chief AI Ethics Officer

**Feature/Story**:
[Story ID, Title, Brief Description]

**Question or Decision Needed**:
[What specifically do you need consultation on?]

---

**Context**:

**System Risk Level**: [Critical/High/Medium/Low]

**Protected Attributes**: [List relevant attributes]

**Fairness Challenge**:
[Describe the fairness issue or trade-off you're facing]

**Current Status**:
[What have you tried? What are your preliminary findings?]

**Options Under Consideration**:
1. [Option A - brief description]
2. [Option B - brief description]
3. [Option C - brief description]

---

**Analysis Completed**:
- [ ] Baseline fairness metrics calculated
- [ ] Intersectional analysis performed
- [ ] Fairness interventions tested
- [ ] Performance impact assessed
- [ ] Relevant documentation reviewed (FDRs, model cards, regulations)

**Attached Materials**:
- [Link to evaluation report]
- [Link to user story]
- [Link to preliminary analysis]
- [Link to relevant FDRs]

---

**Specific Questions**:
1. [Specific question 1]
2. [Specific question 2]
3. [Specific question 3]

**Impact if Decision Delayed**:
[What happens if this consultation is delayed? Sprint impact? Deadline risks?]

**Proposed Meeting**:
- Duration needed: [30/60/90 minutes]
- Preferred dates/times: [Provide 3 options]
- Participants: [Who should attend from your team]
- Format: [In-person/Video call/Async review]

---

**Follow-up Actions**:
[After consultation, document decisions here and link to FDR if created]
```

---

### 12.7 Appendix G: Quick Reference - Fairness Work Estimation Guidelines

Use these rules of thumb for estimating fairness work:

**Data Bias Audit**: 0.5-2 points
- Simple: 0.5 points (existing data, few groups, basic analysis)
- Moderate: 1 point (new data collection, multiple groups, proxy analysis)
- Complex: 2 points (intersectional audit, data quality issues, synthetic data needed)

**Fairness Intervention Implementation**: 1-3 points
- Simple: 1 point (post-processing only, e.g., threshold adjustment)
- Moderate: 2 points (in-processing, e.g., fairness constraints in training)
- Complex: 3 points (novel intervention, multiple techniques, experimentation needed)

**Fairness Testing and Evaluation**: 1-4 points
- Low risk: 1 point (disaggregated testing only)
- Medium risk: 2 points (disaggregated + basic intersectional + counterfactual)
- High risk: 3 points (above + red-team + proxy analysis)
- Critical risk: 4 points (above + extensive intersectional + rigorous counterfactual)

**Intersectional Analysis**: 0.5-1.5 points per intersection
- 1 intersection: 0.5-1 point
- 2 intersections: 1-1.5 points
- 3+ intersections: 1.5-2 points (scale sublinearly, not linearly)

**Documentation**: 0.5-1 point per story
- Model card update: 0.25 points
- FDR creation: 0.5 points (if needed)
- Technical documentation: 0.25 points

**Monitoring Setup**: 0.5-1 point per story
- Simple: 0.5 points (logging only, existing dashboard)
- Complex: 1 point (new metrics, custom dashboard, alerting configuration)

**Consultation Time**: 0.25-0.5 points per consultation
- Include time for: Preparation, meeting, follow-up, documentation

**Buffer**: 10-15% of total fairness estimate
- For unexpected complexity, iteration, rework

**Example Estimation**:
```
Story: Credit scoring model for personal loans (High risk system)

Functional work: 8 points
Fairness work:
- Data bias audit (moderate): 1 point
- Fairness intervention (moderate - adversarial debiasing): 2 points
- Testing (high risk - disaggregated + 2 intersections + counterfactual 200 cases): 3 points
- Intersectional analysis (2 intersections): 1 point
- Documentation (model card + FDR): 0.75 points
- Monitoring (new metrics): 1 point
- Technical Fairness Lead consultation: 0.25 points
Subtotal fairness: 9 points
Buffer (15%): 1.35 points

Total: Functional 8 + Fairness 10.35 ≈ 18-19 points
```

---

### 12.8 Appendix H: Resources and Further Reading

**Organizational Resources**:
- AI Fairness & Agile Integration Playbook: [Internal link]
- Fairness Standards and Thresholds: [Internal link]
- Technical Fairness Lead office hours: [Schedule link]
- Fairness Community of Practice: [Slack channel or meeting schedule]
- Model Card Template: [Link]
- FDR Template: [Link]
- Fairness Evaluation Framework Documentation: [Link]

**External Resources**:

**Fairness Metrics and Concepts**:
- "Fairness Definitions Explained" - Verma & Rubin (2018)
- "On the (Im)possibility of Fairness" - Kleinberg et al. (2016)
- "Fairness and Machine Learning" - Barocas, Hardt, Narayanan (fairmlbook.org)

**Intersectionality**:
- "Intersectional Fairness" - Foulds et al. (2020)
- "The Trouble with Bias" - Blodgett et al. (2020)

**Practical Guidance**:
- Google's ML Fairness Guidelines: [Link]
- Microsoft's Fairness in AI: [Link]
- AI Fairness 360 Toolkit (IBM): [Link]
- Fairlearn (Microsoft): [Link]

**Regulatory and Legal**:
- EU AI Act: [Link]
- US Equal Credit Opportunity Act (ECOA)
- US Fair Housing Act
- GDPR (especially Article 22 on automated decision-making)

**Industry Standards**:
- ISO/IEC standards on AI trustworthiness
- NIST AI Risk Management Framework

---

**Document Version History**

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 2.0 | 2024-12-15 | Sections 9-12 added: Risk-Based Planning Tiers, Sprint Templates, Common Pitfalls, Appendices | AI Fairness & Agile Integration Working Group |
| 1.0 | 2024-11-01 | Initial release: Sections 1-8 | AI Fairness & Agile Integration Working Group |

---

**Feedback and Continuous Improvement**

This document is a living resource. Please provide feedback to improve it:
- Submit improvement suggestions: [Email or form link]
- Quarterly review meetings: [Schedule link]
- Document owner: [Name, contact]

**Acknowledgments**

This playbook was developed collaboratively by:
- AI Fairness Team
- Agile Transformation Team
- Engineering Leadership
- Legal and Compliance
- Product Management

With input from teams across [Organization Name] who piloted fairness integration approaches.

---
