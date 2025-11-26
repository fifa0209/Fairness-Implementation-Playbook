# Architecture-Specific Quick Reference

## Deep Learning Systems

### Primary Challenge
Representation entanglement (protected attributes implicitly encoded in latent space)

### Key Interventions
1. **Adversarial Debiasing**
   - Add discriminator network predicting protected attributes from representations
   - Use gradient reversal to minimize discriminator accuracy
   - Target: <60% protected attribute prediction accuracy

2. **Disentangled Representation Learning**
   - Separate task-relevant features from demographic correlates
   - Use specialized architectures (VAE variants, β-VAE)

3. **Fair Fine-Tuning**
   - Assess inherited biases from pre-trained models
   - Apply targeted fine-tuning on balanced datasets

### Evaluation
- Measure demographic predictability at each layer
- Counterfactual evaluation on test set
- Intersectional disaggregation of performance metrics

### Code Example
```python
def fairness_aware_loss(predictions, labels, embeddings, sensitive_attrs):
    # Task loss
    task_loss = nn.CrossEntropyLoss()(predictions, labels)
    
    # Adversarial fairness loss
    discriminator_preds = discriminator(embeddings)
    adversarial_loss = -nn.CrossEntropyLoss()(discriminator_preds, sensitive_attrs)
    
    # Combined loss with fairness weight
    total_loss = task_loss + lambda_fairness * adversarial_loss
    
    return total_loss
```

## Recommendation Systems

### Primary Challenge
Feedback loops amplify initial biases through dynamic user-system interaction

### Key Interventions
1. **Exploration Policies**
   - ε-greedy: Reserve portion of recommendations for exploration
   - Thompson sampling: Probabilistic exploration
   - Ensures diverse content exposure

2. **Dynamic Popularity Discounting**
   - Adjust scores of high-exposure items downward
   - Prevents runaway popularity effects
   - Formula: adjusted_score = base_score × (1 - α × log(exposure_count))

3. **Multi-Stakeholder Fairness**
   - Balance user satisfaction, provider representation, platform goals
   - Amortized fairness ranking for position bias
   - Governance process for adjusting stakeholder weights

### Evaluation
- Longitudinal fairness tracking (not just snapshot)
- Exposure distribution analysis across item providers
- Filter bubble detection metrics
- Multi-sided marketplace fairness

### Code Example
```python
def fair_ranking_with_exploration(candidates, user_profile, epsilon=0.1):
    # Exploitation: Standard relevance-based ranking
    relevance_scores = model.predict(candidates, user_profile)
    
    # Exploration: Random selection for diversity
    if random.random() < epsilon:
        return random.sample(candidates, k=top_k)
    
    # Apply popularity discounting
    exposure_counts = get_exposure_history(candidates)
    adjusted_scores = relevance_scores * (1 - 0.3 * np.log1p(exposure_counts))
    
    # Rank and return
    return rank_by_score(candidates, adjusted_scores)
```

## Large Language Models (LLMs)

### Primary Challenge
Scale, emergent behaviors, pre-training data bias amplification

### Key Interventions
1. **Prompt-Based Fairness**
   - Explicit fairness directives in system prompts
   - Chain-of-thought prompting to elicit fair reasoning
   - Example: "Consider diverse perspectives. Avoid stereotypes."

2. **Fair Fine-Tuning**
   - Balanced datasets across demographic dimensions
   - Counterfactual data augmentation
   - RLHF (Reinforcement Learning from Human Feedback) prioritizing fairness

3. **Safety Guardrails**
   - Output filters detecting biased responses
   - Real-time bias classifiers on generations
   - Fallback responses for detected bias

### Evaluation
- Red-teaming with adversarial prompts
- Counterfactual generation testing (change demographic, measure output change)
- Stereotype detection benchmarks (e.g., BBQ, StereoSet)
- Human evaluation with diverse raters

### Governance Requirements
- Rapid response protocols for emergent bias patterns
- Continuous monitoring (LLMs behavior can drift)
- Regular re-evaluation cycles (quarterly minimum)

### Code Example
```python
def fair_llm_generation(prompt, model, bias_classifier):
    # System prompt with fairness directive
    system_prompt = """You are a helpful assistant. Consider diverse 
    perspectives and avoid stereotypes. If discussing people, be inclusive 
    and avoid generalizations based on protected attributes."""
    
    # Generate response
    response = model.generate(system_prompt + prompt)
    
    # Safety guardrail: Check for bias
    bias_score = bias_classifier.predict(response)
    
    if bias_score > threshold:
        # Log incident
        log_bias_incident(prompt, response, bias_score)
        # Return fallback
        return "I should be careful to avoid stereotypes. Let me rephrase..."
    
    return response
```

## Vision/Multi-Modal Systems

### Primary Challenge
Visual representation bias, cross-modal amplification, environmental disparities

### Key Interventions
1. **Visual Representation Fairness**
   - Adversarial techniques to remove protected attributes from visual embeddings
   - CNN layer analysis for demographic encoding

2. **Data Collection Equity**
   - Balanced representation across demographics AND environmental conditions
   - Augmentation simulating diverse lighting, angles, contexts

3. **Fair Fusion Architecture**
   - Adaptive fusion balancing modality influence
   - Prevent single-modality dominance
   - Modality-specific bias assessment before cross-modal integration

### Evaluation
- Disaggregated performance across demographic groups AND contexts
- Cross-modal consistency checks
- Environmental robustness testing (lighting, weather, camera quality)

### Implementation Sequence
1. Address modality-specific bias first (e.g., vision bias, text bias separately)
2. Then tackle cross-modal amplification
3. Finally, ensure environmental robustness

## Implementation Checklist

### Pre-Implementation
- [ ] Architecture analysis for bias pathways
- [ ] Protected attribute identification
- [ ] Fairness metric selection
- [ ] Baseline fairness evaluation

### During Implementation
- [ ] Architecture-specific interventions applied
- [ ] Regular fairness testing during development
- [ ] Intersectional evaluation framework
- [ ] Trade-off documentation

### Post-Implementation
- [ ] Comprehensive fairness validation
- [ ] Monitoring configuration
- [ ] Documentation completion
- [ ] Governance approval

## Common Pitfalls

### Deep Learning
- **Pitfall**: Only removing explicit protected attributes
- **Solution**: Address representation-level entanglement

### Recommendation Systems
- **Pitfall**: Ignoring feedback loops
- **Solution**: Implement exploration and popularity discounting

### LLMs
- **Pitfall**: Assuming base model fairness
- **Solution**: Comprehensive testing and guardrails

### Multi-Modal
- **Pitfall**: Single-modality bias assessment
- **Solution**: Cross-modal consistency checking