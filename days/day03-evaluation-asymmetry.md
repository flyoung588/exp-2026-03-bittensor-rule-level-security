Day 3 — Evaluation Mechanisms and Information Asymmetry
Overview

Day 3 examines the evaluation layer, where raw agent behavior is transformed into scores that determine economic outcomes.

This layer is critical because it introduces information asymmetry:

Validators observe only partial, delayed, and noisy signals

Miners optimize behavior with incomplete but exploitable knowledge of the evaluation process

Most rule-level vulnerabilities in AI + Crypto systems do not originate from cryptography or consensus — they emerge here.

1. Roles and Asymmetric Visibility
1.1 What Validators Can Observe

Validators typically observe:

Model outputs on sampled inputs

Response latency

Basic metadata (success / failure, format compliance)

Limited historical performance summaries

They cannot directly observe:

Internal reasoning

Training data provenance

Generalization outside the evaluation distribution

Intentional manipulation strategies

Thus, validators score proxies, not intelligence.

1.2 What Miners Can Control

Miners control:

Model architecture and inference pipeline

Caching and shortcut mechanisms

Conditional behavior based on input detection

Resource allocation across queries

Crucially, miners can adapt faster than validators can redesign evaluation.

This temporal advantage compounds over epochs.

2. Sampling, Latency, and Noise
2.1 Finite Sampling Effects

Evaluation uses finite samples:

Limited number of prompts

Reused or weakly randomized inputs

Implication:
Agents can overfit to evaluation distributions without improving true capability.

2.2 Latency as a Signal

Latency is often used as a secondary metric.

However:

Low latency does not imply intelligence

Precomputation and caching can dominate scores

Adaptive pipelines can behave differently under evaluation vs production

Latency becomes a gameable proxy.

2.3 Noise and Score Variance

All evaluations include noise:

Stochastic model outputs

Network variability

Hardware contention

Noise introduces selection instability:

Small random advantages get amplified by reward geometry

Early luck can lock in long-term dominance

3. Information Asymmetry as a Strategic Surface
3.1 The Asymmetry Gap

Define:

E_v = evaluator knowledge

E_m = miner knowledge

When E_m > E_v, optimization pressure flows toward exploiting evaluator blind spots.

This is structural, not malicious.

3.2 Adaptive Miner Strategies (Conceptual)

Without violating rules, miners may:

Specialize for evaluation-time behavior

Detect evaluator fingerprints

Trade generality for score reliability

Sacrifice robustness for short-term dominance

These strategies are economically rational under asymmetric observation.

4. Temporal Dynamics and Feedback Loops

Evaluation systems operate in feedback loops:

Validator scores miners

Rewards shift miner population

Population shift alters evaluation statistics

Validators react with delay

This delay creates control lag, a known instability source in dynamic systems.

5. Failure Modes at the Evaluation Layer

Common rule-level failures include:

Overfitting masked as progress

Latency-optimized but brittle agents

Homogenization of miner behavior

Difficulty distinguishing intelligence from optimization artifacts

Once entrenched, these failures are costly to reverse.

6. Design Tensions (Unavoidable)

There is no perfect evaluation system.

Designers must trade off:

Transparency vs exploitability

Responsiveness vs stability

Measurement richness vs attack surface

Security here is about damage containment, not elimination.

Closing Questions for Day 4

How are validators themselves incentivized?

Can validator rewards diverge from network health?

What happens when evaluators optimize for their own metrics?

Day 4 will analyze validator incentives and second-order incentive failures.
