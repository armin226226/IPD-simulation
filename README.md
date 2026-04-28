# Iterated Prisoner's Dilemma with Active Inference Agents

A computational simulation of two agents playing the Iterated Prisoner's Dilemma (IPD) using Active Inference, a framework from theoretical neuroscience that models decision-making as free energy minimization.

## What This Is

This project models how cooperation can emerge between self-interested agents when their decisions are driven not by fixed rules but by probabilistic belief updating and epistemic curiosity.

Each agent:
- Maintains a learned transition model of the environment using Dirichlet learning
- Infers hidden states from observations using a Bayesian likelihood model
- Selects actions by minimizing Expected Free Energy (EFE), trading off reward maximization against information gain
- Updates its world model after each interaction

No strategies are hardcoded. Cooperation, if it emerges, does so entirely through inference and preference-driven learning.

## Background

Active inference is a theory of brain function proposed by Karl Friston, in which agents act to minimize surprise, or more precisely, to minimize a variational bound on surprise called free energy. This project applies that framework to a classic social dilemma to study whether and how cooperative behavior can self-organize through continuous belief updating.

This simulation was developed as part of a Master's thesis in Cognitive Science exploring predictive coding and active inference as frameworks for modeling social cognition and multi-agent interaction.

## Key Parameters

| Parameter | Description |
|-----------|-------------|
| `η` (eta) | Learning rate, controls how fast agents update their world model |
| `α` (alpha) | Action precision, controls how deterministically agents exploit their beliefs |
| `γ` (gamma) | Epistemic weighting, controls how much agents value information gain |

## What Was Found

**Baseline two-agent dynamics:** Under default parameters (η=0.6, α=6, γ=0), agents follow a consistent three-phase progression. Early trials produce oscillating cooperation and defection as agents hold near-uniform beliefs. A transient surge in unilateral defection follows. Finally, agents lock into sustained mutual cooperation as their learned transition models align and free energy minimization begins to consistently favor CC outcomes.

**Learning rate symmetry:** Sweeping learning rates across both agents revealed that matched learning speeds are critical. Cooperation peaks strongly along the diagonal where both agents update at similar rates. When one agent learns significantly faster than the other, their transition models fall out of sync, breaking the conditions needed for cooperative lock-in and producing persistent defection or prolonged oscillation instead.

**Action precision:** Cooperation follows an inverted-U relationship with precision. Very low values keep agents too stochastic and exploratory. Very high values make them overly rigid and unable to adapt. Intermediate precision, roughly between 7 and 12, best balances exploration and exploitation and produces the highest cooperation rates.

**Epistemic weighting:** A small amount of epistemic drive, around 0.2 to 0.4, accelerates the discovery of mutual cooperation by favoring uncertainty-reducing actions. Excessive epistemic weighting above 0.5 destabilizes cooperation, as agents over-prioritize information gain at the expense of exploiting known cooperative payoffs.

**Emergent strategies:** Across learning rate sweeps, agents spontaneously develop Win-Stay Lose-Shift and tit-for-tat patterns without these being programmed. Higher learning rates strengthen cooperative inertia but reduce the reliability of punitive responses after defection.

**Three-agent scaling:** Adding a third agent under baseline parameters reduced sustained cooperation, with full mutual cooperation collapsing into defection. Increasing action precision compensated for this, reinstating stable three-way cooperation. This mirrors empirical findings that cooperation declines with group size unless cognitive parameters are carefully tuned.

## Visualizations

The notebook includes:
- Cumulative and rolling cooperation rates over time
- EFE trajectories for both agents (cooperate vs defect)
- Cumulative reward comparison across agents
- Parameter sweep heatmaps (η x η, α x α, η x α, γ x γ) with statistical significance markers
- KL divergence plots tracking learning progress over trials
- Strategy analysis covering tit-for-tat and win-stay lose-shift metrics across learning rates

## Structure

```
IPD-simulation/
│
├── IPD_simulation.ipynb   # Full simulation and analysis notebook
└── README.md
```

## Dependencies

```
numpy
matplotlib
scipy
seaborn
pandas
```

## Author

Armin, Cognitive Science researcher interested in predictive coding, active inference, and computational modeling of social cognition.
