# screening_decision_ml
Translating screening risk scores into capacity-constrained, value-based decisions

## Overview
This repository demonstrates how healthcare organizations can translate risk predictions into operational screening decisions under real-world constraints such as limited outreach capacity, budget, and regulatory accountability.

Rather than focusing on model accuracy alone, this project centers on decision-making:

- Who should be contacted for screening?
- How many can realistically be contacted?
- What is the expected yield of outreach?
- What happens if capacity expands or contracts?
- How confident can we be that outreach caused an increase in screening?
This reflects how population health, payer, and value-based care organizations actually operate.

---
## Problem Statement

Healthcare organizations often:

- build or purchase risk models,
- evaluate them using ROC/AUC,

In practice:

- Outreach capacity is limited.
- Budgets are fixed.
- Thresholds are policy decisions, not mathematical ones.
- Over-contacting wastes resources.
- Under-contacting misses preventable disease.

This project reframes screening analytics as a constrained decision problem.

## Conceptual Framing
## Key Principle
**Models rank patients.
Policy determines the cutoff.**

This repository explicitly separates:

- Prediction (risk ranking)
- Decision (threshold selection under capacity)
- Impact (what outreach actually changes)
## Data Overview
The data used in this project mirrors real clinical and administrative structures:

- Screening eligibility logic
- Longitudinal utilization features
- Demographics and clinical history
- Outreach indicators
To ensure privacy and reusability:

- Feature structure is realistic
- Outcomes and intervention indicators may be synthetically generated
- Decision logic remains fully real

The goal is to demonstrate how decisions are made, not to disclose sensitive data.
## Modeling Approach
Multiple transparent models are used:

- Logistic regression (L1 and L2)
- Tree-based models for comparison

Models are treated as **ranking mechanisms**, not truth machines.

What we do not optimize for:

- Maximum AUC
- Complex architectures
- Black-box performance

What we do optimize for:

- Stable ranking
- Interpretability
- Decision robustness
## Decision Layer (Core Contribution)

This project introduces an explicit decision layer, where most real-world analytics fail.

Capacity-Based Evaluation
For a given outreach capacity **C** (e.g., top 1%, 3%, 5% of eligible members), we compute:

- PPV@C (expected yield)
- Number of screenings completed
- Cost per screened member
- Marginal benefit of expanding capacity

This allows leadership to ask:
- *What do we gain by contacting 1,000 more members?
- *Where do returns diminish?
- *Who gets dropped when budgets shrink?

These are **policy decisions** ,not modeling choices.

---

## Causal & Impact Considerations

Outreach effectiveness is evaluated using pragmatic causal framing:

- Propensity modeling for outreach
- Overlap and balance checks
- Conservative ATE estimation
- Sensitivity analysis
  
Importantly:

- We avoid overclaiming
- We distinguish association from impact
- We clearly state what cannot be inferred
  
This reflects how responsible organizations defend decisions to regulators and auditors.

## Value-Based Care Context

This work is explicitly aligned with:

- Value-based payment models
- Preventive care incentives
- Cost-effectiveness considerations
- Equity and access concerns
The system is designed to answer:

- *Is this outreach strategy worth funding?*
- *Who benefits most under constrained resources?*
- *How does this align with VBP incentives?*
  
## What This Repository Demonstrates

This project shows the ability to:

- Build reproducible healthcare analytics pipelines
- Translate ML outputs into operational decisions
- Reason about thresholds, capacity, and yield
- Apply causal thinking without overstatement
