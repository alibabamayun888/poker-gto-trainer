# poker-gto-trainer｜扑克GTO训练器 | Poker GTO Trainer | 德州扑克AI决策辅助工具 | CFR+深度学习 | 毫秒级决策


[简体中文](README.md) | [繁體中文](README.zh-TW.md) | [English](README.en.md)



<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++17">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.10+">
  <img src="https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch">
  <img src="https://img.shields.io/badge/GTO-Strategy-orange?style=for-the-badge" alt="GTO">
  <img src="https://img.shields.io/badge/CFR-Algorithm-blueviolet?style=for-the-badge" alt="CFR">
</p>

<h1 align="center">🃏 Poker GTO Trainer</h1>
<p align="center">
  <b>扑克GTO训练器 — 基于CFR算法与深度神经网络的德州扑克决策辅助工具</b><br>
  <b>Poker GTO Trainer | Texas Hold'em AI Decision Assistant | CFR + Deep Learning</b><br>
  <b>支持1v1到1v9对战 | 毫秒级决策 | 强化学习自博弈训练</b>
</p>


<p align="center">
  <a href="#功能特性">🎯 功能特性</a> •
  <a href="#技术架构">⚙️ 技术架构</a> •
  <a href="#快速开始">🚀 快速开始</a> •
  <a href="#API示例">📡 API示例</a> •
  <a href="#性能数据">📊 性能数据</a>
</p>

---

## 目录

- [项目简介](#项目简介)
- [功能特性](#功能特性)
- [技术架构](#技术架构)
- [算法原理](#算法原理)
- [快速开始](#快速开始)
- [API示例](#api示例)
- [训练流程](#训练流程)
- [可视化工具](#可视化工具)
- [性能数据](#性能数据)
- [应用场景](#应用场景)
- [项目结构](#项目结构)
- [常见问题](#常见问题)
- [SEO关键词](#seo关键词)
- [许可证](#许可证)
- [联系我们](#联系我们)

---

## 项目简介

**Poker GTO Trainer（扑克GTO训练器）** 是一款面向开发者和扑克爱好者的**实用型AI决策辅助工具**，基于**反事实遗憾最小化（CFR）算法**与**深度神经网络**，帮助用户学习、训练和验证GTO（博弈论最优）策略。

本工具支持**1v1单挑**到**1v9多人对战**模式，采用自我博弈强化学习训练，可实现**毫秒级实时决策输出**。适用于策略学习、AI陪练、决策分析等场景。

&gt; **适合搜索关键词**：扑克GTO训练器、德州扑克AI工具、Poker GTO Trainer、Texas Hold'em AI Assistant、CFR算法实现、Counterfactual Regret Minimization、博弈论最优策略、非完美信息博弈、强化学习扑克、深度神经网络扑克、多智能体决策、扑克AI引擎、扑克策略求解器、GTO策略学习、纳什均衡扑克

| 语言 | 项目名称 |
|------|---------|
| 中文 | 扑克GTO训练器 / 德州扑克AI工具 / CFR扑克助手 |
| English | Poker GTO Trainer / Texas Hold'em AI Assistant / CFR Poker Tool |
| Tiếng Việt | Công cụ GTO Poker / Trợ lý AI Poker |

---

## 功能特性

### 核心能力

| 特性 | 说明 |
|------|------|
| 🎯 **GTO策略学习** | 通过CFR迭代训练，学习接近纳什均衡的最优策略 |
| 🎮 **1v1 单挑模式** | Heads-Up No-Limit Texas Hold'em 标准对战 |
| 🎮 **1vN 多人模式** | 支持1v2、1v3、1v6、1v9 等多种对战配置 |
| ⚡ **毫秒级决策** | 单步决策延迟 6-10 毫秒 |
| 🧠 **自我博弈训练** | 通过自我对弈持续优化策略 |
| 📊 **决策可视化** | 实时展示行动概率、期望值、 regret值 |
| 🔧 **开发者API** | 提供Python/C++ API，方便集成到第三方系统 |

### 训练与评估

| 模块 | 功能 |
|------|------|
| **自我博弈训练** | 自动进行大规模自我对弈，生成训练数据 |
| **策略评估** | 与随机策略、规则基线、其他AI进行对战评估 |
| **对手建模** | 可选对手行为建模与自适应策略调整 |
| **模型导出** | 支持导出训练好的策略模型，用于部署 |

---

## 技术架构

| 层级 | 技术 | 说明 |
|------|------|------|
| **核心计算引擎** | C++17 / Boost.Asio | 高性能CFR计算与博弈树搜索 |
| **训练框架** | Python 3.10+ / PyTorch 2.0+ | 神经网络训练与策略优化 |
| **决策API** | Python / gRPC | 对外提供实时决策服务接口 |
| **可视化前端** | Python / Matplotlib / Streamlit | 策略可视化与交互分析 |
| **数据缓存** | Redis | 状态缓存与实时数据同步 |
| **通信协议** | Protobuf / gRPC | 跨语言服务间通信 |

---

## 算法原理

### 反事实遗憾最小化（CFR）

CFR 是一种用于求解**非完美信息博弈**的迭代算法。在每一轮迭代中：

1. **构建博弈树**：遍历当前信息集下的所有可能行动
2. **计算反事实价值**：评估每个行动在假设采取该行动时的期望收益
3. **更新遗憾值**：记录未采取行动的遗憾程度
4. **策略平均**：根据累积遗憾值生成新的行为策略
5. **迭代收敛**：重复上述过程直至策略收敛至纳什均衡

### 深度神经网络组件

- **状态编码器**：将公共牌、手牌、下注历史编码为向量
- **价值网络**：估计当前信息集的反事实价值
- **策略网络**：输出每个合法行动的概率分布

### 决策流程
输入: 当前游戏状态 (手牌 + 公共牌 + 下注历史)
↓
状态编码器 → 向量表示
↓
策略网络 → 各行动概率 (Fold / Call / Raise)
↓
价值网络 → 各行动期望收益
↓
输出: 最优行动 + 置信度 + 期望值


---

## 快速开始

### 环境要求

- **OS**: Ubuntu 20.04+ / CentOS 8+ / macOS 12+
- **Compiler**: GCC 9.4+ / Clang 12+
- **Build**: CMake 3.20+
- **Python**: 3.10+
- **PyTorch**: 2.0+
- **Redis**: 6.0+

### 安装步骤

```bash
# 1. 克隆仓库
git clone https://github.com/alibabamayun888/poker-gto-trainer.git
cd poker-gto-trainer

# 2. 安装Python依赖
pip install -r requirements.txt

# 3. 编译C++核心
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)

# 4. 运行测试
cd ..
python -m pytest tests/ -v
```

### 运行对战
# 启动1v1对战
python main.py --mode=heads-up --model=models/gto-v1.pt

# 启动1v9多人对战
python main.py --mode=multiplayer --model=models/gto-v1.pt --opponents=9


API示例

Python API

from poker_gto import GTOTrainer

# 初始化训练器
trainer = GTOTrainer(model_path="models/gto-v1.pt")

# 获取当前状态的决策建议
state = {
    "hand": ["As", "Kd"],
    "community": ["Qh", "Jc", "Td"],
    "pot": 100,
    "to_call": 20
}

decision = trainer.decide(state)
print(decision)
# 输出: {'action': 'raise', 'amount': 60, 'confidence': 0.85, 'ev': 45.2}

C++ API
#include "gto/trainer.hpp"

int main() {
    GTODecision decision = GTOTrainer::decide(hand, community, pot, toCall);
    std::cout << "Action: " << decision.action << std::endl;
    std::cout << "Confidence: " << decision.confidence << std::endl;
    return 0;
}

### 训练流程
# 1. 准备训练配置
cp conf/train_example.yaml conf/train.yaml
vim conf/train.yaml  # 修改参数

# 2. 启动自我博弈训练
python main.py --mode=train --config=conf/train.yaml

# 3. 监控训练进度
python visualize/training_monitor.py --log=logs/training.log

# 4. 评估训练好的模型
python main.py --mode=eval --model=outputs/model-v1.pt

可视化工具
# 启动决策可视化面板
python visualize/decision_board.py --model=models/gto-v1.pt

# 启动策略热力图分析
python visualize/strategy_heatmap.py --model=models/gto-v1.pt --position=BTN

### 性能数据

测试环境：AMD EPYC 2×128 Cores | 2TB RAM | Ubuntu 22.04
| 指标                  | 数值        |
| ------------------- | --------- |
| **决策延迟**            | 6-10 毫秒/步 |
| **1v1 胜率 vs 随机策略**  | 85%       |
| **1v1 胜率 vs 规则基线**  | 72%       |
| **1v1 胜率 vs CFR基线** | 58%       |
| **训练收敛速度**          | 15天/99模型  |
| **最大支持对战人数**        | 1v9       |


### 应用场景
| 场景          | 说明                     |
| ----------- | ---------------------- |
| 📚 **策略学习** | 通过AI决策学习GTO策略，提升扑克理论水平 |
| 🤖 **AI陪练** | 与高强度AI对战，磨练实战技巧        |
| 🧠 **决策分析** | 分析历史牌局，找出决策偏差          |
| 🎮 **游戏开发** | 为扑克游戏提供智能NPC对手         |
| 🔬 **算法研究** | 验证新的博弈论算法与对手建模方法       |




### 常见问题

Q1: 这个项目可以用于商业用途吗？
A: 源码仅供学习研究。如需商业用途，请联系获取授权协议。
Q2: CFR算法与深度学习的关系是什么？
A: CFR负责策略迭代与遗憾值计算，深度学习（神经网络）负责状态价值估计与策略抽象，两者结合可处理大规模博弈树。
Q3: 支持哪些对战模式？
A: 支持1v1单挑、1v2、1v3、1v6、1v9等多种配置，通过修改配置文件即可切换。
Q4: 训练一个模型需要多长时间？
A: 在2×128核、2TB内存的配置下，完整训练约需15天，生成99个模型。
Q5: 决策延迟是多少？
A: 单步决策延迟为6-10毫秒，满足实时对战需求。
Q6: 如何评估AI的强度？
A: 项目内置测试模块，可与随机策略、规则基线AI、CFR基线进行对战评估。
Q7: 是否支持自定义对手策略？
A: 支持。可在opponent/目录下定义新的对手策略，并在配置文件中指定。
Q8: 需要多少算力才能运行？
A: 推理阶段仅需普通CPU即可运行；训练阶段建议配备多核服务器与充足内存。

### SEO关键词

以下关键词用于搜索引擎索引，覆盖全球多语言搜索场景
中文关键词： 扑克GTO训练器、德州扑克AI工具、扑克AI助手、CFR算法实现、反事实遗憾最小化、博弈论最优策略、非完美信息博弈、强化学习扑克、深度神经网络扑克、多智能体决策、扑克AI引擎、扑克策略求解器、GTO策略学习、纳什均衡扑克、德州扑克机器人、扑克AI训练、自我博弈训练、扑克决策系统、扑克策略分析、扑克游戏AI、AI扑克对手、智能扑克系统、扑克API、扑克开发者工具
English Keywords: Poker GTO Trainer, Texas Hold'em AI Assistant, Poker AI Tool, CFR Poker AI, Counterfactual Regret Minimization, Game Theory Optimal Poker, Imperfect Information Game AI, Reinforcement Learning Poker, Deep Learning Poker, Multi-Agent Decision Making, Poker Bot Engine, GTO Strategy Engine, Nash Equilibrium Poker, Poker AI Source Code, Self-Play Poker Training, Poker Decision System, Poker Strategy Solver, Poker Game AI, AI Poker Opponent, Intelligent Poker System, Heads-Up Poker AI, No-Limit Texas Hold'em AI, Poker AI Research, Poker AI Benchmark, Poker AI GitHub, Open Source Poker AI, Poker AI Tutorial, Poker AI Implementation, Poker AI C++, Poker AI Python, Poker AI PyTorch, Poker Developer API, Poker AI Library


### 许可证

本项目采用 MIT License 开源协议。
📚 学习用途：允许自由下载、学习、研究
🔬 学术用途：允许在论文和研究中引用
🏢 商业用途：需获取商业授权，请联系下方邮箱
This software is provided for learning, research, and demonstration purposes only. Commercial use requires a separate license agreement.

## 产品截图

![德州AI GTO训练器产品截图 01](docs/assets/Screenshots/0011.png)
![德州AI GTO训练器产品截图 02](docs/assets/Screenshots/0012.png)
![德州AI GTO训练器产品截图 03](docs/assets/Screenshots/0013.png)

### 联系我们
| 渠道          | 联系方式                                                                         |
| ----------- | ---------------------------------------------------------------------------- |
| 📧 Email    | <ttpoker40@gmail.com>                                                        |
| 💬 Telegram | [@alibabama401](https://t.me/alibabama401)                                   |
| 🐛 Issues   | [GitHub Issues](https://github.com/alibabamayun888/poker-gto-trainer/issues) |



<p align="center">
  <b>⭐ 如果这个项目对你的研究有帮助，请点个 Star 支持一下！⭐</b><br>
  <i>If this project helps your research, please give it a star and share it with your peers!</i><br><br>
  <a href="https://github.com/alibabamayun888/poker-gto-trainer/stargazers">
    <img src="https://img.shields.io/github/stars/alibabamayun888/poker-gto-trainer?style=social" alt="Give a Star">
  </a>
</p>
```
