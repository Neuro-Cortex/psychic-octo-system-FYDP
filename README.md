# Interaction-Aware Causal Feature Identification and Adaptive Activation Steering for Safer Large Language Models

<p align="center">

**FYDP | Final Year Design Project**

*Towards understanding causal interactions between internal safety features and improving LLM safety through adaptive activation steering.*

</p>

---

## 1. Project Overview

Large Language Models (LLMs) can generate harmful responses when exposed to jailbreak prompts or adversarial instructions. Although these models contain internal safety-related representations, identifying which internal features causally contribute to safe behavior remains challenging.

Existing activation steering methods often focus on individual features or fixed combinations of features. However, interactions between features may produce **synergistic, antagonistic, or context-dependent effects** that cannot be understood by examining features independently.

This project proposes an interaction-aware framework for identifying causal safety features and dynamically steering their activations to improve model safety while preserving helpfulness and fluency.

## 2. Research Objectives

- Identify internal safety-related features using Sparse Autoencoders (SAEs).
- Measure the individual causal effects of identified features.
- Discover pairwise causal interactions, including synergy and antagonism.
- Investigate how causal interactions change across different contexts.
- Develop an adaptive activation steering mechanism.
- Improve harmful-prompt resistance while preserving benign response quality.

## 3. Research Gap

Existing approaches face several limitations:

1. Correlation-based feature identification does not necessarily establish causal importance.
2. Individual feature analysis may overlook interactions between multiple safety features.
3. Fixed activation steering may fail when feature interactions change across contexts.
4. Aggressive safety steering may increase over-refusal and reduce helpfulness.

**Our research direction:** Move beyond individual feature identification toward interaction-aware causal discovery and context-adaptive activation steering.

## 4. Proposed Novel Contributions

### Contribution 1: Interaction-Aware Causal Feature Identification

Identify individual and pairwise causal effects of internal safety features through controlled interventions.

### Contribution 2: Causal Synergy and Antagonism Discovery

Measure whether two features jointly produce stronger or weaker effects than their independent contributions.

Proposed interaction measure:

\[
I_{ij}=Y(\{i,j\})-Y(\{i\})-Y(\{j\})+Y(\varnothing)
\]

Where:
- \(I_{ij}>0\): Positive synergy.
- \(I_{ij}<0\): Negative interaction or antagonism.
- \(I_{ij}\approx 0\): Approximately additive effects.

### Contribution 3: Context-Dependent Interaction Analysis

Investigate whether the same feature pair behaves differently under different prompt contexts, including benign, harmful, and adversarial prompts.

### Contribution 4: Adaptive Activation Steering

Develop an interaction-aware steering strategy that dynamically selects feature combinations and steering strengths based on their measured causal effects.

General steering formulation:

\[
h'=h+\sum_i\alpha_i d_i
\]

Where:
- \(h\) = Original model activation.
- \(d_i\) = Direction associated with feature \(i\).
- \(\alpha_i\) = Adaptive steering coefficient.
- \(h'\) = Modified activation.

## 5. Proposed Methodology

The project follows a multi-stage research pipeline:

**Stage 1: Model Selection**
- Select the primary LLM.
- Establish a baseline model for evaluation.

**Stage 2: Sparse Feature Discovery**
- Apply Sparse Autoencoders (SAEs).
- Extract candidate internal features.
- Identify potentially safety-related features.

**Stage 3: Individual Causal Evaluation**
- Perform activation ablation and intervention.
- Measure feature necessity and sufficiency.
- Estimate individual causal effects.

**Stage 4: Pairwise Causal Interaction Discovery**
- Test feature pairs through joint interventions.
- Calculate synergy and antagonism.
- Construct an interaction graph.

**Stage 5: Context-Dependent Analysis**
- Evaluate interactions across different prompt contexts.
- Identify interaction changes and reversals.

**Stage 6: Adaptive Activation Steering**
- Select relevant causal feature combinations.
- Optimize steering strengths.
- Apply context-aware activation interventions.

**Stage 7: Experimental Evaluation**
- Compare the proposed method with existing baselines.
- Evaluate safety, helpfulness, fluency, and robustness.

## 6. Models and Datasets

### Models

| Model | Purpose |
|---|---|
| Gemma-2-2B-IT | Primary research model |
| Pythia-70M | Pipeline development and debugging |

### Evaluation Datasets

| Dataset | Purpose |
|---|---|
| HarmBench | Harmful prompt evaluation |
| XSTest | Testing over-refusal and appropriate refusals |
| Held-out prompt transformations | Generalization and robustness evaluation |

## 7. Experimental Baselines

The proposed framework will be compared against:

- Original model without steering.
- Individual feature steering.
- Fixed pairwise feature steering.
- Context-aware individual feature steering.
- Existing SAE-based steering approaches.
- Proposed interaction-aware adaptive steering.

## 8. Evaluation Metrics

| Metric | Evaluation Purpose |
|---|---|
| Attack Success Rate (ASR) | Resistance to harmful prompts |
| Benign Refusal Rate | Avoiding unnecessary refusals |
| Helpfulness | Maintaining useful responses |
| Fluency | Preserving response quality |
| Causal Effect | Measuring intervention impact |
| Intervention Cost | Measuring computational overhead |
| Robustness | Evaluating generalization across contexts |

## 9. Expected Outcomes

- A framework for identifying causal safety features.
- A method for quantifying pairwise causal interactions.
- An interaction graph representing synergy and antagonism.
- A context-aware adaptive activation steering algorithm.
- Experimental evidence regarding safety–utility trade-offs.
- An evaluation of generalization across different prompt contexts.

*These are research objectives and expected outcomes, not yet experimentally validated findings.*

## 10. Proposed Technology Stack

- **Programming Language:** Python
- **Deep Learning:** PyTorch
- **Model Ecosystem:** Hugging Face Transformers
- **Interpretability:** Sparse Autoencoders (SAEs)
- **Experiment Tracking:** To be selected
- **Version Control:** Git and GitHub

## 11. Repository Structure

```text
FYDP/
│
├── README.md
│
├── configs/
│   └── model_config.yaml
│
├── data/
│   ├── raw/
│   └── processed/
│
├── src/
│   ├── feature_discovery/
│   ├── causal_analysis/
│   ├── interaction_analysis/
│   ├── adaptive_steering/
│   └── evaluation/
│
├── experiments/
│   ├── individual_features/
│   ├── pairwise_interactions/
│   └── adaptive_steering/
│
├── results/
│   ├── metrics/
│   ├── plots/
│   └── analysis/
│
├── notebooks/
│
├── requirements.txt
│
└── .gitignore
```

## 12. Research Scope

This project is designed as a one-year research project with moderate computational resources.

The primary focus is on causal feature identification, pairwise interaction discovery, context-dependent causal analysis, and adaptive activation steering.

The experimental implementation and evaluation will determine the effectiveness and limitations of the proposed framework.

## 13. Project Information

- **Project Type:** Final Year Design Project (FYDP)
- **Research Domain:** Artificial Intelligence and Explainable AI
- **Subdomain:** Mechanistic Interpretability and LLM Safety
- **Primary Research Focus:** Causal Feature Identification and Activation Steering
- **Project Status:** Research and Development

---

**Research Goal:** To discover how internal safety features causally interact and use those interactions to develop more reliable, adaptive, and safer Large Language Models.
