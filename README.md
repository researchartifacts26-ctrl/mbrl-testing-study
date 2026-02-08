# Anonymous Artifact – Empirical Study on Testing Model-Based Reinforcement Learning Systems
  This repository contains the **anonymous research artifact** accompanying an empirical study on the applicability and effectiveness of existing RL testing frameworks when applied to **Model-Based Reinforcement Learning (MBRL)** systems.
  The artifact is prepared for **double-blind review** and contains all code, notebooks, and data required to reproduce the reported experimental results.

---
## 1. Artifact Overview

  The artifact consists of **seven executable Jupyter notebooks**, each corresponding to one evaluation environment and agent type:
  
  | Notebook | Agent | Environment |
  |--------|------|------------|
  | N01_DynaQ_Taxi.ipynb | Dyna-Q | Taxi |
  | N02_DynaQ_Frozenlake.ipynb | Dyna-Q | FrozenLake |
  | N03_MuZero_Connect4.ipynb | MuZero | Connect4 |
  | N04_MuZero_Cartpole.ipynb | MuZero | CartPole |
  | N05_PETS_Pendulum.ipynb | PETS | Pendulum |
  | N06_DreamerV3_Crafter.ipynb | DreamerV3 | Crafter |
  | N07_MuZero_Lunalander.ipynb | MuZero | LunarLander |
  
  Each notebook:
  - loads a **fixed, pre-trained agent**
  - executes 18 **RL testing frameworks**
  - computes standardized metrics (FR, TTF, APFD, APFD-time)
  - generates tables and plots identical to those reported in the paper
  - 
## 2. Repository Structure
mbrl-testing-frameworks-empirical-study/
├── notebooks/              # All experiment notebooks (one per agent–environment pair)
│   ├── N01_DynaQ_Taxi.ipynb
│   ├── N02_DynaQ_Frozenlake.ipynb
│   ├── N03_MuZero_Connect4.ipynb
│   ├── N04_MuZero_Cartpole.ipynb
│   ├── N05_PETS_Pendulum.ipynb
│   ├── N06_DreamerV3_Crafter.ipynb
│   └── N07_MuZero_Lunalander.ipynb
│
├── agents/                 # Fixed, pre-trained agent components used for testing
│   ├── dynaq/
│   │   ├── taxi/
│   │   └── frozenlake/
│   ├── muzero/
│   │   ├── connect4/
│   │   ├── cartpole/
│   │   └── lunalander/
│   ├── pets/
│   │   └── pendulum/
│   └── dreamerv3/
│       └── crafter/        # DreamerV3 agent (agent.pkl via Zenodo)
│
├── results/                # Generated results (created after notebook execution)
│   ├── taxi/
│   ├── frozenlake/
│   ├── connect4/
│   ├── pendulum/
│   ├── cartpole/
│   ├── lunalander/
│   └── crafter/
│
├── data/                   # Auxiliary data and test pools
│   └── test_pools/
│       ├── connect4_pool.py
│       └── connect4_pool.pkl
│
├── envs/                   # Custom environment implementations
│   └── connect4.py
│
├── metrics/                # Metric utilities (duplicated inside notebooks for self-containment)
│
├── .git/                   # Git metadata (not part of the artifact logic)
├── .gitignore
└── README.md

  The `results/` directory is populated automatically when notebooks are executed.
  
## 3. Running the Artifact
  
  ### Option A: Google Colab (Recommended)
  Each notebook includes a **Google Colab–specific setup cell**.
  Steps:
    1. Upload the repository to Google Drive
    2. Open a notebook from the `notebooks/` directory
    3. Run all cells sequentially
  
  The notebooks automatically create required output folders.
  

  ### Option B: Local Execution
  Each notebook also includes a **local path configuration cell**, for example:
  ```python
  AGENT_ROOT = Path("mbrl-testing-frameworks-empirical-study/agents/muzero/cartpole")
  RESULTS_DIR = Path("mbrl-testing-frameworks-empirical-study/results/cartpole")
  
  
  To run locally:
    -Clone this repository
    -Ensure Python ≥ 3.9
    -Run the notebooks using Jupyter


  ## 4. Large Model Files (DreamerV3)
    The DreamerV3 agent checkpoint (agent.pkl) is intentionally not included in this repository due to file size constraints.
    It is publicly available via Zenodo: (🔗 https://zenodo.org/records/18528220)
    To run the Crafter experiment with the real DreamerV3 policy:
      -Download agent.pkl from Zenodo
      -Place it under: agents/dreamerv3/crafter/
      -In N06_DreamerV3_Crafter.ipynb, set: (USE_REAL_DREAMER = True)
    By default, the notebook runs with a competent fallback policy that preserves: action distribution characteristics, interaction frequency, and oracle semantics. This ensures the notebook is fully executable even without the large binary.


  ## 5. Expected Outputs
      After executing a notebook, the following are generated under results/<environment>/:
      1- tables/
          single-row metrics per framework
      2- figs/
          -Failure Rate bar plots
          -Cumulative Failure vs Tests
          -Cumulative Failure vs Time
      3-raw_single/
          per-episode failure logs
      All outputs correspond directly to figures and tables reported in the paper.

## 6 . Anonymity Statement
    -This repository is anonymized for double-blind review:
    -no author names or affiliations are included
    -no identifying metadata is present
    -external resources (e.g., Zenodo) are referenced without attribution
