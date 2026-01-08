# Day 2 — Incentive Functions and Reward Geometry

## Overview

Day 2 deepens our understanding of **what the protocol actually rewards** and **how reward geometry shapes agent behavior**.

In incentive-driven AI networks like Bittensor, the system does not reward “quality” in an absolute sense. Instead, it transforms observable signals through a scoring and allocation pipeline into **relative, often non-linear rewards**.

This transformation determines:

* Which strategies are economically dominant
* Which behaviors proliferate
* Where rule-level pathologies and failures emerge

---

## 1. Formal Model of Reward Allocation

We model a simplified epoch-based reward system.

### Definitions

* Let there be `N` miners, indexed by `i`
* Each miner receives a raw evaluation score `s_i ≥ 0`
* The protocol emits `E` tokens per epoch
* A reward function maps scores to rewards `r_i` such that:

[
\sum_{i=1}^N r_i = E
]

A canonical proportional allocation rule is:

[
r_i = E \cdot \frac{s_i^\alpha}{\sum_{j=1}^N s_j^\alpha}
]

where `α ≥ 0` controls reward curvature.

### Special Cases

* `α = 1` → linear proportional rewards
* `α > 1` → convex amplification (winner-take-more)
* `0 < α < 1` → concave compression (egalitarian smoothing)
* `α → 0` → near-uniform distribution

**Key observation:**
Small changes in `α` can produce qualitatively different incentive regimes.

---

## 2. Reward Geometry and Failure Modes

### 2.1 Linear Geometry (`α = 1`)

**Intuition:** rewards scale proportionally with score.

**Strengths**

* Simple
* Predictable
* Transparent

**Risks**

* If scores are cheap to inflate, linearity offers no protection
* Relative ranking always matters, even for trivial score improvements

---

### 2.2 Convex Geometry (`α > 1`)

**Intuition:** exceptional performance is disproportionately rewarded.

**Consequences**

* Small advantages at the top yield large reward gains
* Encourages arms-race dynamics
* Amplifies noise and evaluation bias

**Systemic Risk**
Convexity incentivizes agents to optimize *the scoring metric itself*, not the underlying utility.

---

### 2.3 Concave Geometry (`0 < α < 1`)

**Intuition:** reward differences are flattened.

**Benefits**

* Reduced variance
* Limits dominance by a single actor

**Trade-off**

* Weak marginal incentive to invest in costly improvements
* Encourages free-riding near the mean

---

### 2.4 Thresholds and Reward Cliffs

Real-world scoring systems often include:

* Minimum qualification thresholds
* Discontinuous reward jumps

**Effect**

* Creates bifurcation zones
* Strong incentives for risky or manipulative strategies near the threshold
* Small score perturbations cause large economic outcomes

---

### 2.5 Temporal Effects

* **Short windows** → high variance, burst exploitation
* **Long windows** → robustness, but vulnerable to slow poisoning

No window length is universally safe — only trade-offs exist.

---

## 3. Strategic Implications

### 3.1 Goodhart’s Law (Formalized)

> When a measure becomes a target, it ceases to be a good measure.

Let:

* `u_i` = true (unobservable) utility
* `s_i = f(u_i, ε_i)` = observed score with noise or manipulation `ε_i`

As agents optimize `s_i`, the correlation `Corr(s_i, u_i)` degrades — especially under convex reward geometry.

---

### 3.2 Overfitting to Evaluation Distributions

Validators evaluate on finite, repeated samples.

**Result**

* Agents overfit to the evaluation distribution
* High scores on validation ≠ general usefulness

---

### 3.3 Coordination and Relative-Share Exploits

Because rewards depend on *relative* scores:

* Coordinated agents can reduce the effective denominator
* Apparent robustness can be manufactured through mutual reinforcement

These behaviors remain rule-compliant and difficult to detect.

---

### 3.4 Low-Cost / High-Return Regions

If scoring is sensitive to cheap, repeatable signals:

* Small engineering effort yields outsized rewards
* System selects for metric exploitation over intelligence

---

### 3.5 Long-Term Memory Poisoning

When historical scores influence future rewards:

* Gradual, legal optimization can permanently bias baselines
* Reversals become costly and destabilizing

---

## 4. Diagnostic Metrics

Early warning indicators for incentive failure:

1. **Score / Reward Concentration**

   * Gini coefficient
   * Top-k reward share

2. **Score–Utility Drift**

   * Declining correlation with external or downstream metrics

3. **Temporal Volatility**

   * Short-term spikes without long-term persistence

4. **Cross-Validation Variance**

   * High fold variance implies fragile scoring

5. **Reward Churn vs Participation Churn**

   * High reward volatility with stable participants indicates scoring instability

---

## 5. Designer-Level Checklist (Conceptual)

* Avoid excessive convexity unless scoring is manipulation-resistant
* Rotate and obscure validation samples
* Balance smoothing windows against responsiveness
* Monitor concentration metrics continuously
* Use auxiliary signals to reduce pressure on a single metric

---

## Closing Questions for Day 3

* How are validators selected and incentivized?
* What information asymmetries exist between miners and validators?
* Which evaluation steps are observable, predictable, or gameable?

**Day 3** will examine **evaluation mechanisms and information asymmetry** in detail.
