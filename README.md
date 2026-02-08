# Anonymous Artifact – Empirical Study on Testing Model-Based Reinforcement Learning Systems

This repository contains the **anonymous research artifact** accompanying an empirical study on the applicability and effectiveness of existing **Reinforcement Learning (RL) testing frameworks** when applied to **Model-Based Reinforcement Learning (MBRL)** systems.

The artifact is prepared for **double-blind review** and enables full reproduction of the experimental results reported in the paper.

---

## Table of Contents
- [Artifact Overview](#artifact-overview)
- [Repository Structure](#repository-structure)
- [Running the Artifact](#running-the-artifact)
  - [Google Colab (Recommended)](#google-colab-recommended)
  - [Local Execution](#local-execution)
- [Large Model Files (DreamerV3)](#large-model-files-dreamerv3)
- [Expected Outputs](#expected-outputs)
- [Anonymity Statement](#anonymity-statement)

---

## Artifact Overview

The artifact consists of **seven executable Jupyter notebooks**, each corresponding to one environment–agent pair:

| Notebook | Agent | Environment |
|--------|------|------------|
| `N01_DynaQ_Taxi.ipynb` | Dyna-Q | Taxi |
| `N02_DynaQ_Frozenlake.ipynb` | Dyna-Q | FrozenLake |
| `N03_MuZero_Connect4.ipynb` | MuZero | Connect4 |
| `N04_MuZero_Cartpole.ipynb` | MuZero | CartPole |
| `N05_PETS_Pendulum.ipynb` | PETS | Pendulum |
| `N06_DreamerV3_Crafter.ipynb` | DreamerV3 | Crafter |
| `N07_MuZero_Lunalander.ipynb` | MuZero | LunarLander |

Each notebook:
- loads a **fixed, pre-trained agent**
- executes **multiple RL testing frameworks**
- computes standardized metrics (FR, TTF, APFD, APFD-time)
- generates tables and plots used in the paper

---

## Repository Structure

```text
mbrl-testing-frameworks-empirical-study/
├── notebooks/        # All experiment notebooks
├── agents/           # Pre-trained agent components
├── results/          # Generated results (tables, plots, raw logs)
├── data/             # Test pools (e.g., Connect4)
├── envs/             # Custom environments (e.g., Connect4)
├── metrics/          # Metric utilities (also defined inside notebooks)
The results/ directory is populated automatically when notebooks are executed.

##Anonymity Statement
  -This repository is fully anonymized for double-blind review:
  -no author names or affiliations are included
  -no identifying metadata is present
  -external resources (e.g., Zenodo) are referenced without attribution
