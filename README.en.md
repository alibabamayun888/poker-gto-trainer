# Poker GTO Trainer | Texas Hold'em GTO and CFR Strategy Tool

[简体中文](README.md) | [繁體中文](README.zh-TW.md) | [English](README.en.md)

<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++17">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.10+">
  <img src="https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch 2.0+">
  <img src="https://img.shields.io/badge/GTO-Strategy-orange?style=for-the-badge" alt="GTO Strategy">
  <img src="https://img.shields.io/badge/CFR-Algorithm-blueviolet?style=for-the-badge" alt="CFR Algorithm">
</p>

<p align="center">
  <strong>A Texas Hold'em GTO strategy trainer and decision-analysis tool based on CFR and deep neural networks</strong><br>
  Supports heads-up and 1vN play, self-play training, strategy evaluation, API integration, and visualization
</p>

## Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [How CFR Works](#how-cfr-works)
- [Quick Start](#quick-start)
- [API Examples](#api-examples)
- [Training Workflow](#training-workflow)
- [Visualization](#visualization)
- [Performance](#performance)
- [Use Cases](#use-cases)
- [Repository Structure](#repository-structure)
- [FAQ](#faq)
- [License](#license)
- [Screenshots](#screenshots)
- [Contact](#contact)

## Overview

**Poker GTO Trainer** is a Texas Hold'em AI tool for developers, researchers, and poker strategy learners. It combines **Counterfactual Regret Minimization (CFR)** with **deep neural networks** to train, study, and validate Game Theory Optimal (GTO) strategies.

The project describes support for **heads-up through 1v9 multiplayer configurations**, self-play reinforcement learning, decision analysis, strategy evaluation, model export, developer APIs, and visualization. It is designed for Texas Hold'em GTO study, poker AI research, algorithm validation, AI practice, and game development.

## Features

### Core Capabilities

| Feature | Description |
| --- | --- |
| **GTO strategy learning** | Uses CFR iterations to learn strategies approaching Nash equilibrium |
| **Heads-up mode** | Heads-Up No-Limit Texas Hold'em play |
| **1vN multiplayer** | Supports 1v2, 1v3, 1v6, and 1v9 configurations |
| **Low-latency decisions** | Recorded single-step latency of 6–10 ms |
| **Self-play training** | Continuously improves strategies through self-play |
| **Decision visualization** | Displays action probabilities, expected value, and regret values |
| **Developer APIs** | Provides Python and C++ APIs for integration |

### Training and Evaluation

| Module | Purpose |
| --- | --- |
| **Self-play training** | Generates training data through large-scale self-play |
| **Strategy evaluation** | Evaluates against random strategies, rule-based baselines, and other AIs |
| **Opponent modeling** | Supports optional behavioral modeling and adaptive strategies |
| **Model export** | Exports trained strategy models for deployment |

## Architecture

| Layer | Technology | Purpose |
| --- | --- | --- |
| **Core engine** | C++17 / Boost.Asio | CFR computation and game-tree search |
| **Training framework** | Python 3.10+ / PyTorch 2.0+ | Neural-network training and strategy optimization |
| **Decision API** | Python / gRPC | Real-time decision service interface |
| **Visualization** | Python / Matplotlib / Streamlit | Interactive strategy analysis |
| **Data cache** | Redis | State caching and real-time synchronization |
| **Protocol** | Protobuf / gRPC | Cross-language service communication |

## How CFR Works

Counterfactual Regret Minimization is an iterative algorithm for solving **imperfect-information games** and is widely studied in poker AI and Texas Hold'em GTO research:

1. **Build the game tree** by traversing actions available at each information set.
2. **Calculate counterfactual values** for actions that could be taken.
3. **Update regret** based on the difference between action values.
4. **Average strategies** using accumulated regret.
5. **Iterate toward convergence** and an approximation of Nash equilibrium.

### Neural-Network Components

- **State encoder:** converts hole cards, community cards, and betting history into vectors.
- **Value network:** estimates counterfactual values for the current information set.
- **Policy network:** outputs a probability distribution over legal actions.

```text
Game state (hole cards + board + betting history)
                         ↓
                State encoder → vector
                         ↓
                Policy network → actions
                         ↓
                Value network → expected value
                         ↓
          Action, confidence, and expected value
```

## Quick Start

### Requirements

- **OS:** Ubuntu 20.04+ / CentOS 8+ / macOS 12+
- **Compiler:** GCC 9.4+ / Clang 12+
- **Build:** CMake 3.20+
- **Python:** 3.10+
- **PyTorch:** 2.0+
- **Redis:** 6.0+

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/alibabamayun888/poker-gto-trainer.git
cd poker-gto-trainer

# 2. Install Python dependencies
pip install -r requirements.txt

# 3. Build the C++ core
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)

# 4. Run tests
cd ..
python -m pytest tests/ -v
```

### Run a Match

```bash
# Heads-up
python main.py --mode=heads-up --model=models/gto-v1.pt

# 1v9 multiplayer
python main.py --mode=multiplayer --model=models/gto-v1.pt --opponents=9
```

## API Examples

### Python

```python
from poker_gto import GTOTrainer

trainer = GTOTrainer(model_path="models/gto-v1.pt")
state = {
    "hand": ["As", "Kd"],
    "community": ["Qh", "Jc", "Td"],
    "pot": 100,
    "to_call": 20,
}

decision = trainer.decide(state)
print(decision)
# {'action': 'raise', 'amount': 60, 'confidence': 0.85, 'ev': 45.2}
```

### C++

```cpp
#include "gto/trainer.hpp"

int main() {
    GTODecision decision = GTOTrainer::decide(hand, community, pot, toCall);
    std::cout << "Action: " << decision.action << std::endl;
    std::cout << "Confidence: " << decision.confidence << std::endl;
    return 0;
}
```

## Training Workflow

```bash
cp conf/train_example.yaml conf/train.yaml
vim conf/train.yaml
python main.py --mode=train --config=conf/train.yaml
python visualize/training_monitor.py --log=logs/training.log
python main.py --mode=eval --model=outputs/model-v1.pt
```

## Visualization

```bash
python visualize/decision_board.py --model=models/gto-v1.pt
python visualize/strategy_heatmap.py --model=models/gto-v1.pt --position=BTN
```

## Performance

Recorded environment: AMD EPYC 2×128 cores, 2 TB RAM, Ubuntu 22.04.

| Metric | Recorded value |
| --- | --- |
| **Decision latency** | 6–10 ms per step |
| **Heads-up win rate vs random strategy** | 85% |
| **Heads-up win rate vs rule-based baseline** | 72% |
| **Heads-up win rate vs CFR baseline** | 58% |
| **Training convergence** | 15 days / 99 models |
| **Maximum table configuration** | 1v9 |

> Results depend on hardware, compiler options, model revision, and test configuration. Record the complete environment when reproducing or citing benchmarks.

## Use Cases

| Use case | Description |
| --- | --- |
| **Strategy study** | Learn Texas Hold'em GTO through AI decision analysis |
| **AI practice** | Simulate matches against AI opponents of different strengths |
| **Hand analysis** | Review historical hands and identify decision deviations |
| **Game development** | Build intelligent NPC opponents for poker games |
| **Algorithm research** | Evaluate game-theory and opponent-modeling methods |

## Repository Structure

```text
poker-gto-trainer/
├── benchmark/       # Benchmarks
├── cmake/           # CMake modules
├── doc/             # Project documentation
├── docs/            # Documentation and image assets
├── packages/        # Packaging resources
├── CMakeLists.txt   # CMake configuration
├── configure.ac     # Autoconf configuration
└── COPYING          # BSD 3-Clause License
```

## FAQ

### Can this project be used commercially?

The project uses the BSD 3-Clause License. Read the complete terms in [COPYING](COPYING), and ensure compliance with applicable law and third-party dependency licenses.

### How do CFR and deep learning work together?

CFR handles strategy iteration and regret computation. The neural-network components estimate state values and abstract strategies, helping address larger game trees.

### Which match formats are supported?

The project documentation describes 1v1, 1v2, 1v3, 1v6, and 1v9 configurations selected through configuration files.

### How long does training take?

The current performance record reports approximately 15 days and 99 generated models on a 2×128-core, 2 TB RAM system. Actual time depends on hardware and training parameters.

### What is the decision latency?

The current record is 6–10 ms per step. Actual latency depends on hardware, model, and runtime configuration.

### Can I define custom opponents?

Yes. Custom opponent strategies can be defined under `opponent/` and selected in the configuration.

## License

This project is licensed under the **BSD 3-Clause License**. See [COPYING](COPYING) for the complete terms.

Use of the project should also follow [RESPONSIBLE-USE.md](RESPONSIBLE-USE.md).

## Screenshots

![Poker GTO Trainer screenshot 01](docs/assets/Screenshots/0011.png)

![Poker GTO Trainer screenshot 02](docs/assets/Screenshots/0012.png)

![Poker GTO Trainer screenshot 03](docs/assets/Screenshots/0013.png)

## Contact

| Channel | Contact |
| --- | --- |
| Email | <ttpoker40@gmail.com> |
| Telegram | [@alibabama401](https://t.me/alibabama401) |
| Issues | [GitHub Issues](https://github.com/alibabamayun888/poker-gto-trainer/issues) |

<p align="center">
  <strong>If Poker GTO Trainer helps your research, please star the repository and share it with other developers.</strong><br><br>
  <a href="https://github.com/alibabamayun888/poker-gto-trainer/stargazers">
    <img src="https://img.shields.io/github/stars/alibabamayun888/poker-gto-trainer?style=social" alt="Give Poker GTO Trainer a Star">
  </a>
</p>
