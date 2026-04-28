# Iterated Prisoner's Dilemma with Active Inference Agents

A computational simulation of two agents playing the Iterated Prisoner's Dilemma (IPD) using Active Inference, a framework from theoretical neuroscience that models decision-making as free energy minimization.

## What This Is

This project models how cooperation can emerge between self-interested agents when their decisions are driven not by fixed rules but by probabilistic belief updating and epistemic curiosity.

Each agent:
- Maintains a learned transition model of the environment (Dirichlet learning)
- Infers hidden states from observations using a Bayesian likelihood model
- Selects actions by minimizing Expected Free Energy (EFE), trading off reward maximization against information gain
- Updates its world model after each interaction

## Why It Matters for AI Alignment

The core alignment question this simulation addresses is: **under what conditions do agents with misaligned individual incentives converge on cooperative behavior?**

This is directly relevant to multi-agent AI systems where:
- Agents optimize for individual objectives but must coexist
- Trust and cooperation are not hardcoded but must emerge from interaction
- Epistemic drive (curiosity) may promote or hinder cooperation

## Key Parameters

| Parameter | Description |
|-----------|-------------|
| `η` (eta) | Learning rate, controls how fast agents update their world model |
| `α` (alpha) | Action precision, controls how deterministically agents exploit beliefs |
| `γ` (gamma) | Epistemic weighting, controls how much agents value information gain |

## What Was Found

- **Learning rate (η):** Moderate learning rates produce the highest cooperation. Too slow and agents never adapt. Too fast and agents overfit to recent outcomes.
- **Action precision (α):** Higher precision increases exploitation of learned beliefs, generally improving cooperation once a good model is learned.
- **Epistemic weighting (γ):** Epistemic drive has a nuanced effect. Small values promote cooperation while high values can destabilize it.
- **Emergent strategies:** Agents spontaneously develop tit-for-tat and win-stay-lose-shift patterns without these being explicitly programmed.

## Visualizations

The notebook includes:
- Cumulative and rolling cooperation rates over time
- EFE trajectories for both agents (cooperate vs defect)
- Cumulative reward comparison
- Parameter sweep heatmaps (η x η, α x α, η x α, γ x γ) with statistical significance markers
- KL divergence plots tracking learning progress
- Strategy analysis (TFT and WSLS metrics across learning rates)

## Structure

```
IPD-simulation/
│
├── IPD_simulation.ipynb   # Full simulation and analysis notebook
└── README.md
```

## Background

This project was developed as part of a Master's thesis in Cognitive Science exploring predictive coding and active inference as frameworks for modeling social cognition and multi-agent interaction.

Active inference is a theory of brain function proposed by Karl Friston, in which agents act to minimize surprise, or more precisely, to minimize a variational bound on surprise called free energy. Applying this to the IPD connects neuroscientific models of cognition to open questions in AI alignment and multi-agent systems.

## Dependencies

```
numpy
matplotlib
scipy
seaborn
pandas
```

## Author

Armin, Cognitive Science researcher interested in the intersection of predictive coding, active inference, and AI alignment.
