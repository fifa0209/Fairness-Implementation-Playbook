# Adaptability Guidelines

## Overview
This section provides guidance for adapting the Fairness Implementation Playbook across different domains, problem types, organizational scales, and maturity levels.

## 6.1 Domain Adaptation

### Healthcare AI
- **Risk Profile**: Often high-risk (diagnosis, treatment recommendations)
- **Key Modifications**:
  - **Protected attributes**: Add disability status, genetic information per GINA
  - **Fairness metrics**: Emphasize clinical validity across demographic groups, not just statistical parity
  - **Stakeholders**: Include patient advocates, clinical ethicists, medical board representatives in governance
  - **Regulatory**: Add HIPAA privacy considerations, FDA medical device regulations
  - **Architecture**: Strong emphasis on explainability for clinical decision support (not just fairness)

### Financial Services
- **Risk Profile**: High-risk (credit decisions, insurance pricing)
- **Key Modifications**:
  - **Protected attributes**: Per ECOA, include marital status, national origin
  - **Fairness metrics**: Emphasize equal opportunity (access to credit) over demographic parity
  - **Regulatory**: Add ECOA, Fair Housing Act, state-specific consumer protection laws
  - **Evidence**: Heightened documentation for adverse action notices
  - **Architecture**: Focus on proxy detection (zip code, names as proxies for protected attributes)

### Education
- **Risk Profile**: High-risk (admissions, financial aid, tracking)
- **Key Modifications**:
  - **Protected attributes**: Add first-generation status, socioeconomic status
  - **Fairness metrics**: Balance between merit-based and equity-based measures
  - **Stakeholders**: Strong student/family representation in governance
  - **Regulatory**: FERPA privacy, Title IX equity considerations
  - **Intersectionality**: Critical focus on multiply-marginalized students (e.g., low-income + first-gen + underrepresented minority)

## 6.2 Problem Type Adaptation

### Classification (Binary/Multi-class)
- Use standard group fairness metrics (demographic parity, equal opportunity, equalized odds)
- Implement post-processing threshold optimization when appropriate
- Focus on confusion matrix disaggregation across groups

### Regression
- Adapt fairness metrics: Use error rate parity, calibration across groups
- Challenge: Continuous outcomes make "parity" definitions less clear
- Technique: Bin predictions into categories for fairness assessment

### Ranking/Recommendation
- Emphasize exposure fairness and position bias
- Implement feedback loop management (exploration policies, popularity discounting)
- Multi-stakeholder fairness considerations (users, item providers, platform)
- Longitudinal evaluation required (fairness over time, not just snapshots)

### Generative AI (LLMs, Diffusion Models)
- Challenge: Emergent behaviors, high output diversity
- Techniques: Prompt-based fairness, RLHF, output filtering
- Evaluation: Red-teaming, counterfactual generation testing
- Governance: Rapid response protocols for unexpected bias patterns
- Ongoing vigilance due to emergent properties

## 6.3 Scale Adaptation

### Small Organizations (<50 employees)
- **Governance**: Assign fairness to existing roles (part-time capacity: 10-20%)
- **Scrum**: Simplify to core practices (enhanced user stories, basic DoD)
- **Architecture**: Leverage open-source fairness libraries, avoid custom implementations
- **Compliance**: Focus on highest-risk systems only, use templates for documentation

### Medium Organizations (50-1000 employees)
- **Governance**: Hybrid model with central CoE (1-2 FTE) + embedded champions
- **Scrum**: Full Fair AI Scrum implementation with 15-30% capacity allocation
- **Architecture**: Architecture-specific interventions for high-risk systems
- **Compliance**: Unified compliance framework with automated evidence collection

### Large Enterprises (>1000 employees)
- **Governance**: Full Center of Excellence (5-10 FTE) + embedded champions in each BU
- **Scrum**: Comprehensive implementation across all teams with dedicated fairness sprint roles
- **Architecture**: Custom fairness infrastructure, centralized ML platform with fairness tooling
- **Compliance**: Automated compliance pipeline, dedicated legal/regulatory team

## 6.4 Maturity Level Adaptation

### Stage 1 (Starting Out)
- **Focus**: Risk classification, basic governance roles, core Scrum practices
- **Timeline**: 6 months to establish foundations
- **Quick wins**: Enhanced user stories, RACI matrices, basic monitoring

### Stage 2 (Developing)
- **Focus**: Architecture-specific interventions, comprehensive monitoring, full compliance framework
- **Timeline**: 6-12 months to build systematic practices
- **Depth**: Intersectional analysis, advanced technical interventions, evidence automation

### Stage 3 (Mature)
- **Focus**: Continuous improvement, industry leadership, advanced techniques
- **Timeline**: 12+ months of sustained implementation
- **Innovation**: Custom fairness research, contributing to open-source fairness tools, thought leadership

## Implementation Roadmap by Maturity

### Stage 1 (Months 1-6)
- Conduct AI system portfolio review and risk classification
- Define fairness leadership roles and secure commitments
- Train teams on Fair AI Scrum practices
- Implement basic monitoring dashboards

### Stage 2 (Months 7-12)
- Deploy architecture-specific interventions for priority systems
- Establish comprehensive compliance framework
- Implement automated evidence collection
- Conduct first external fairness audit

### Stage 3 (Year 2+)
- Scale practices across all development teams
- Contribute to industry standards and open-source tools
- Establish thought leadership through case studies and publications
- Implement predictive fairness risk models

## Common Adaptation Challenges

### Resource Constraints
- **Challenge**: Limited budget and personnel for fairness implementation
- **Solution**: Start with highest-risk systems, use open-source tools, assign part-time responsibilities

### Technical Complexity
- **Challenge**: Advanced architectures require specialized fairness knowledge
- **Solution**: Leverage architecture cookbook, partner with academic institutions, hire specialized talent

### Regulatory Uncertainty
- **Challenge**: Evolving regulatory landscape creates compliance uncertainty
- **Solution**: Implement to highest common standard, maintain regulatory watch, engage with policymakers

### Cultural Resistance
- **Challenge**: Organizational resistance to fairness requirements and transparency
- **Solution**: Executive sponsorship, clear business case, progressive disclosure of limitations