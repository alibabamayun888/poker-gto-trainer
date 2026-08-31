[簡體中文](README.md) | [繁體中文](README.zh-TW.md) | [English](README.en.md)

# poker-gto-trainer｜撲克GTO訓練器 | Poker GTO Trainer | 德州撲克AI決策輔助工具 | CFR+深度学习 | 毫秒級決策
<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++17">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.10+">
  <img src="https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch">
  <img src="https://img.shields.io/badge/GTO-Strategy-orange?style=for-the-badge" alt="GTO">
  <img src="https://img.shields.io/badge/CFR-Algorithm-blueviolet?style=for-the-badge" alt="CFR">
</p>

<h1 align="center">🃏 Poker GTO Trainer</h1>
<p align="center">
  <b>撲克GTO訓練器 — 基于CFR演算法与深度神经网络的德州撲克決策輔助工具</b><br>
  <b>Poker GTO Trainer | Texas Hold'em AI Decision Assistant | CFR + Deep Learning</b><br>
  <b>支援1v1到1v9對戰 | 毫秒級決策 | 強化學習自博弈訓練</b>
</p>


<p align="center">
  <a href="#功能特色">🎯 功能特色</a> •
  <a href="#技術架構">⚙️ 技術架構</a> •
  <a href="#快速開始">🚀 快速開始</a> •
  <a href="#API示例">📡 API示例</a> •
  <a href="#性能資料">📊 性能資料</a>
</p>

---

## 閱讀與下載

- 建議先閱讀本 README，瞭解德州撲克 GTO 訓練、AI 決策、CFR 演算法、模型訓練、API 接入和二次開發范围。
- 產品截圖統一讀取 `docs/assets/Screenshots/` 目錄下的真實檔案；上傳时请保持 `assets` 小写、`Screenshots` 首字母大写，檔案名大小写也不要改。
- 如需源碼評估、展示包、部署說明或客製開發，请通过文末 Email 或 Telegram 聯絡。

## 產品截圖

![德州AI GTO訓練器產品截圖 01](docs/assets/Screenshots/0011.png)
![德州AI GTO訓練器產品截圖 02](docs/assets/Screenshots/0012.png)
![德州AI GTO訓練器產品截圖 03](docs/assets/Screenshots/0013.png)

## 目錄

- [專案簡介](#專案簡介)
- [功能特色](#功能特色)
- [技術架構](#技術架構)
- [演算法原理](#演算法原理)
- [快速開始](#快速開始)
- [API示例](#api示例)
- [訓練流程](#訓練流程)
- [視覺化工具](#視覺化工具)
- [性能資料](#性能資料)
- [應用場景](#應用場景)
- [项目结构](#项目结构)
- [常見問題](#常見問題)
- [SEO關鍵字](#seo關鍵字)
- [授權條款](#授權條款)
- [聯絡我们](#聯絡我们)

---

## 專案簡介

**Poker GTO Trainer（撲克GTO訓練器）** 是一款面向開發者和撲克爱好者的**实用型AI決策輔助工具**，基于**反事实遗憾最小化（CFR）演算法**与**深度神经网络**，帮助用户学习、訓練和验证GTO（博弈论最优）策略。

本工具支援**1v1单挑**到**1v9多人對戰**模式，采用自我博弈強化學習訓練，可实现**毫秒級实时決策输出**。适用于策略学习、AI陪练、決策分析等场景。

&gt; **适合搜索關鍵字**：撲克GTO訓練器、德州撲克AI工具、Poker GTO Trainer、Texas Hold'em AI Assistant、CFR演算法实现、Counterfactual Regret Minimization、博弈论最优策略、非完美信息博弈、強化學習撲克、深度神经网络撲克、多智能体決策、撲克AI引擎、撲克策略求解器、GTO策略学习、纳什均衡撲克

| 语言 | 项目名称 |
|------|---------|
| 中文 | 撲克GTO訓練器 / 德州撲克AI工具 / CFR撲克助手 |
| English | Poker GTO Trainer / Texas Hold'em AI Assistant / CFR Poker Tool |
| Tiếng Việt | Công cụ GTO Poker / Trợ lý AI Poker |

---

## 功能特色

### 核心能力

| 特性 | 說明 |
|------|------|
| 🎯 **GTO策略学习** | 通过CFR迭代訓練，学习接近纳什均衡的最优策略 |
| 🎮 **1v1 单挑模式** | Heads-Up No-Limit Texas Hold'em 标准對戰 |
| 🎮 **1vN 多人模式** | 支援1v2、1v3、1v6、1v9 等多种對戰配置 |
| ⚡ **毫秒級決策** | 单步決策延迟 6-10 毫秒 |
| 🧠 **自我博弈訓練** | 通过自我对弈持续优化策略 |
| 📊 **決策視覺化** | 实时展示行动概率、期望值、 regret值 |
| 🔧 **開發者API** | 提供Python/C++ API，方便集成到第三方系统 |

### 訓練与評估

| 模块 | 功能 |
|------|------|
| **自我博弈訓練** | 自动进行大规模自我对弈，生成訓練資料 |
| **策略評估** | 与随机策略、规则基线、其他AI进行對戰評估 |
| **对手建模** | 可选对手行为建模与自适应策略调整 |
| **模型导出** | 支援导出訓練好的策略模型，用于部署 |

---

## 技術架構

| 层级 | 技术 | 說明 |
|------|------|------|
| **核心计算引擎** | C++17 / Boost.Asio | 高性能CFR计算与博弈树搜索 |
| **訓練框架** | Python 3.10+ / PyTorch 2.0+ | 神经网络訓練与策略优化 |
| **決策API** | Python / gRPC | 对外提供实时決策服务接口 |
| **視覺化前端** | Python / Matplotlib / Streamlit | 策略視覺化与交互分析 |
| **資料缓存** | Redis | 状态缓存与实时資料同步 |
| **通信协议** | Protobuf / gRPC | 跨语言服务间通信 |

---

## 演算法原理

### 反事实遗憾最小化（CFR）

CFR 是一种用于求解**非完美信息博弈**的迭代演算法。在每一轮迭代中：

1. **构建博弈树**：遍历当前信息集下的所有可能行动
2. **计算反事实价值**：評估每个行动在假设采取该行动时的期望收益
3. **更新遗憾值**：记录未采取行动的遗憾程度
4. **策略平均**：根据累积遗憾值生成新的行为策略
5. **迭代收敛**：重复上述过程直至策略收敛至纳什均衡

### 深度神经网络组件

- **状态编码器**：将公共牌、手牌、下注历史编码为向量
- **价值网络**：估计当前信息集的反事实价值
- **策略网络**：输出每个合法行动的概率分布

### 決策流程
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

## 快速開始

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

### 运行對戰
# 启动1v1對戰
python main.py --mode=heads-up --model=models/gto-v1.pt

# 启动1v9多人對戰
python main.py --mode=multiplayer --model=models/gto-v1.pt --opponents=9


API示例

Python API

from poker_gto import GTOTrainer

# 初始化訓練器
trainer = GTOTrainer(model_path="models/gto-v1.pt")

# 获取当前状态的決策建議
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

### 訓練流程
# 1. 准备訓練配置
cp conf/train_example.yaml conf/train.yaml
vim conf/train.yaml  # 修改参数

# 2. 启动自我博弈訓練
python main.py --mode=train --config=conf/train.yaml

# 3. 监控訓練进度
python visualize/training_monitor.py --log=logs/training.log

# 4. 評估訓練好的模型
python main.py --mode=eval --model=outputs/model-v1.pt

視覺化工具
# 启动決策視覺化面板
python visualize/decision_board.py --model=models/gto-v1.pt

# 启动策略热力图分析
python visualize/strategy_heatmap.py --model=models/gto-v1.pt --position=BTN

### 性能資料

测试环境：AMD EPYC 2×128 Cores | 2TB RAM | Ubuntu 22.04
| 指标                  | 数值        |
| ------------------- | --------- |
| **決策延迟**            | 6-10 毫秒/步 |
| **1v1 胜率 vs 随机策略**  | 85%       |
| **1v1 胜率 vs 规则基线**  | 72%       |
| **1v1 胜率 vs CFR基线** | 58%       |
| **訓練收敛速度**          | 15天/99模型  |
| **最大支援對戰人数**        | 1v9       |


### 應用場景
| 场景          | 說明                     |
| ----------- | ---------------------- |
| 📚 **策略学习** | 通过AI決策学习GTO策略，提升撲克理论水平 |
| 🤖 **AI陪练** | 与高强度AI對戰，磨练实战技巧        |
| 🧠 **決策分析** | 分析历史牌局，找出決策偏差          |
| 🎮 **游戏開發** | 为撲克游戏提供智能NPC对手         |
| 🔬 **演算法研究** | 验证新的博弈论演算法与对手建模方法       |




### 常見問題

Q1: 这个项目可以用于商业用途吗？
A: 源碼仅供学习研究。如需商业用途，请聯絡获取授权协议。
Q2: CFR演算法与深度学习的关系是什么？
A: CFR负责策略迭代与遗憾值计算，深度学习（神经网络）负责状态价值估计与策略抽象，两者结合可处理大规模博弈树。
Q3: 支援哪些對戰模式？
A: 支援1v1单挑、1v2、1v3、1v6、1v9等多种配置，通过修改配置檔案即可切换。
Q4: 訓練一个模型需要多长时间？
A: 在2×128核、2TB内存的配置下，完整訓練约需15天，生成99个模型。
Q5: 決策延迟是多少？
A: 单步決策延迟为6-10毫秒，满足实时對戰需求。
Q6: 如何評估AI的强度？
A: 项目内置测试模块，可与随机策略、规则基线AI、CFR基线进行對戰評估。
Q7: 是否支援自定义对手策略？
A: 支援。可在opponent/目錄下定义新的对手策略，并在配置檔案中指定。
Q8: 需要多少算力才能运行？
A: 推理阶段仅需普通CPU即可运行；訓練阶段建議配备多核服务器与充足内存。

### SEO關鍵字

以下關鍵字用于搜索引擎索引，覆盖全球多语言搜索场景
中文關鍵字： 撲克GTO訓練器、德州撲克AI工具、撲克AI助手、CFR演算法实现、反事实遗憾最小化、博弈论最优策略、非完美信息博弈、強化學習撲克、深度神经网络撲克、多智能体決策、撲克AI引擎、撲克策略求解器、GTO策略学习、纳什均衡撲克、德州撲克机器人、撲克AI訓練、自我博弈訓練、撲克決策系统、撲克策略分析、撲克游戏AI、AI撲克对手、智能撲克系统、撲克API、撲克開發者工具
English Keywords: Poker GTO Trainer, Texas Hold'em AI Assistant, Poker AI Tool, CFR Poker AI, Counterfactual Regret Minimization, Game Theory Optimal Poker, Imperfect Information Game AI, Reinforcement Learning Poker, Deep Learning Poker, Multi-Agent Decision Making, Poker Bot Engine, GTO Strategy Engine, Nash Equilibrium Poker, Poker AI Source Code, Self-Play Poker Training, Poker Decision System, Poker Strategy Solver, Poker Game AI, AI Poker Opponent, Intelligent Poker System, Heads-Up Poker AI, No-Limit Texas Hold'em AI, Poker AI Research, Poker AI Benchmark, Poker AI GitHub, Open Source Poker AI, Poker AI Tutorial, Poker AI Implementation, Poker AI C++, Poker AI Python, Poker AI PyTorch, Poker Developer API, Poker AI Library


### 授權條款

本项目采用 MIT License 开源协议。
📚 学习用途：允许自由下载、学习、研究
🔬 学术用途：允许在论文和研究中引用
🏢 商业用途：需获取商业授权，请聯絡下方邮箱
This software is provided for learning, research, and demonstration purposes only. Commercial use requires a separate license agreement.


### 聯絡我们
| 渠道          | 聯絡方式                                                                         |
| ----------- | ---------------------------------------------------------------------------- |
| 📧 Email    | <ttpoker40@gmail.com>                                                        |
| 💬 Telegram | [@alibabama401](https://t.me/alibabama401)                                   |
| 🐛 Issues   | [GitHub Issues](https://github.com/alibabamayun888/poker-gto-trainer/issues) |



<p align="center">
  <b>⭐ 如果这个项目对你的研究有帮助，请点个 Star 支援一下！⭐</b><br>
  <i>If this project helps your research, please give it a star and share it with your peers!</i><br><br>
  <a href="https://github.com/alibabamayun888/poker-gto-trainer/stargazers">
    <img src="https://img.shields.io/github/stars/alibabamayun888/poker-gto-trainer?style=social" alt="Give a Star">
  </a>
</p>
```