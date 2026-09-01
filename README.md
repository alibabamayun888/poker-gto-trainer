# Poker GTO Trainer｜扑克 GTO 训练器与德州扑克 AI 策略工具

[简体中文](README.md) | [繁體中文](README.zh-TW.md) | [English](README.en.md)

<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++17">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.10+">
  <img src="https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch 2.0+">
  <img src="https://img.shields.io/badge/GTO-Strategy-orange?style=for-the-badge" alt="GTO Strategy">
  <img src="https://img.shields.io/badge/CFR-Algorithm-blueviolet?style=for-the-badge" alt="CFR Algorithm">
</p>

<p align="center">
  <strong>基于 CFR 算法与深度神经网络的德州扑克 GTO 策略训练和决策分析工具</strong><br>
  <strong>Poker GTO Trainer | Texas Hold'em AI Strategy Tool | CFR + Deep Learning</strong><br>
  支持 1v1 至 1v9 对战、自我博弈训练、策略评估、API 接入与可视化分析
</p>

<p align="center">
  <a href="#功能特性">功能特性</a> ·
  <a href="#技术架构">技术架构</a> ·
  <a href="#快速开始">快速开始</a> ·
  <a href="#api-示例">API 示例</a> ·
  <a href="#性能数据">性能数据</a>
</p>

## 目录

- [项目简介](#项目简介)
- [功能特性](#功能特性)
- [技术架构](#技术架构)
- [算法原理](#算法原理)
- [快速开始](#快速开始)
- [API 示例](#api-示例)
- [训练流程](#训练流程)
- [可视化工具](#可视化工具)
- [性能数据](#性能数据)
- [应用场景](#应用场景)
- [项目结构](#项目结构)
- [常见问题](#常见问题)
- [许可证](#许可证)
- [产品截图](#产品截图)
- [联系我们](#联系我们)

## 项目简介

**Poker GTO Trainer（扑克 GTO 训练器）**是一款面向开发者、研究人员和扑克策略学习者的德州扑克 AI 工具。项目结合**反事实遗憾最小化（Counterfactual Regret Minimization，CFR）算法**与**深度神经网络**，用于学习、训练和验证 GTO（Game Theory Optimal，博弈论最优）策略。

项目支持 **1v1 单挑至 1v9 多人对战**配置，通过自我博弈强化学习持续优化策略，并提供决策分析、策略评估、模型导出、开发者 API 和可视化工具。它适用于德州扑克 GTO 学习、扑克 AI 研究、算法验证、AI 陪练和游戏开发。

| 语言 | 项目名称 |
| --- | --- |
| 中文 | 扑克 GTO 训练器 / 德州扑克 AI 工具 / CFR 扑克助手 |
| English | Poker GTO Trainer / Texas Hold'em AI Assistant / CFR Poker Tool |
| Tiếng Việt | Công cụ GTO Poker / Trợ lý AI Poker |

## 功能特性

### 核心能力

| 特性 | 说明 |
| --- | --- |
| **GTO 策略学习** | 通过 CFR 迭代训练，学习接近纳什均衡的策略 |
| **1v1 单挑模式** | Heads-Up No-Limit Texas Hold'em 标准对战 |
| **1vN 多人模式** | 支持 1v2、1v3、1v6、1v9 等对战配置 |
| **毫秒级决策** | 单步决策延迟为 6–10 毫秒 |
| **自我博弈训练** | 通过自我对弈持续优化策略 |
| **决策可视化** | 展示行动概率、期望值和 regret 值 |
| **开发者 API** | 提供 Python/C++ API，便于集成第三方系统 |

### 训练与评估

| 模块 | 功能 |
| --- | --- |
| **自我博弈训练** | 自动进行大规模自我对弈并生成训练数据 |
| **策略评估** | 与随机策略、规则基线及其他 AI 进行对战评估 |
| **对手建模** | 支持可选的对手行为建模与自适应策略调整 |
| **模型导出** | 导出训练后的策略模型用于部署 |

## 技术架构

| 层级 | 技术 | 说明 |
| --- | --- | --- |
| **核心计算引擎** | C++17 / Boost.Asio | CFR 计算与博弈树搜索 |
| **训练框架** | Python 3.10+ / PyTorch 2.0+ | 神经网络训练与策略优化 |
| **决策 API** | Python / gRPC | 提供实时决策服务接口 |
| **可视化前端** | Python / Matplotlib / Streamlit | 策略可视化与交互分析 |
| **数据缓存** | Redis | 状态缓存与实时数据同步 |
| **通信协议** | Protobuf / gRPC | 跨语言服务通信 |

## 算法原理

### 反事实遗憾最小化（CFR）

CFR 是一种用于求解**不完全信息博弈**的迭代算法，也是扑克 AI 与德州扑克 GTO 策略研究中的常用方法。每轮迭代主要包括：

1. **构建博弈树**：遍历当前信息集下的可能行动。
2. **计算反事实价值**：评估假设采取各行动时的期望收益。
3. **更新遗憾值**：记录未采取行动所对应的遗憾程度。
4. **策略平均**：根据累积遗憾值生成新的行为策略。
5. **迭代收敛**：重复以上过程，使策略逐渐接近纳什均衡。

### 深度神经网络组件

- **状态编码器**：将公共牌、手牌和下注历史编码为向量。
- **价值网络**：估计当前信息集的反事实价值。
- **策略网络**：输出每个合法行动的概率分布。

### 决策流程

```text
当前游戏状态（手牌 + 公共牌 + 下注历史）
                    ↓
             状态编码器 → 向量表示
                    ↓
             策略网络 → 行动概率
                    ↓
             价值网络 → 期望收益
                    ↓
        输出行动、置信度与期望值
```

## 快速开始

### 环境要求

- **OS**：Ubuntu 20.04+ / CentOS 8+ / macOS 12+
- **Compiler**：GCC 9.4+ / Clang 12+
- **Build**：CMake 3.20+
- **Python**：3.10+
- **PyTorch**：2.0+
- **Redis**：6.0+

### 安装步骤

```bash
# 1. 克隆仓库
git clone https://github.com/alibabamayun888/poker-gto-trainer.git
cd poker-gto-trainer

# 2. 安装 Python 依赖
pip install -r requirements.txt

# 3. 编译 C++ 核心
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)

# 4. 运行测试
cd ..
python -m pytest tests/ -v
```

### 运行对战

```bash
# 启动 1v1 对战
python main.py --mode=heads-up --model=models/gto-v1.pt

# 启动 1v9 多人对战
python main.py --mode=multiplayer --model=models/gto-v1.pt --opponents=9
```

## API 示例

### Python API

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

### C++ API

```cpp
#include "gto/trainer.hpp"

int main() {
    GTODecision decision = GTOTrainer::decide(hand, community, pot, toCall);
    std::cout << "Action: " << decision.action << std::endl;
    std::cout << "Confidence: " << decision.confidence << std::endl;
    return 0;
}
```

## 训练流程

```bash
# 1. 准备训练配置
cp conf/train_example.yaml conf/train.yaml
vim conf/train.yaml

# 2. 启动自我博弈训练
python main.py --mode=train --config=conf/train.yaml

# 3. 监控训练进度
python visualize/training_monitor.py --log=logs/training.log

# 4. 评估训练后的模型
python main.py --mode=eval --model=outputs/model-v1.pt
```

## 可视化工具

```bash
# 启动决策可视化面板
python visualize/decision_board.py --model=models/gto-v1.pt

# 启动策略热力图分析
python visualize/strategy_heatmap.py --model=models/gto-v1.pt --position=BTN
```

## 性能数据

测试环境：AMD EPYC 2×128 Cores、2 TB RAM、Ubuntu 22.04。

| 指标 | 数值 |
| --- | --- |
| **决策延迟** | 6–10 毫秒/步 |
| **1v1 胜率 vs 随机策略** | 85% |
| **1v1 胜率 vs 规则基线** | 72% |
| **1v1 胜率 vs CFR 基线** | 58% |
| **训练收敛速度** | 15 天 / 99 个模型 |
| **最大支持对战人数** | 1v9 |

> 性能结果与硬件、编译选项、模型版本和测试配置有关。复现或引用数据时，请同时记录完整测试环境。

## 应用场景

| 场景 | 说明 |
| --- | --- |
| **策略学习** | 通过 AI 决策分析学习德州扑克 GTO 策略 |
| **AI 陪练** | 与不同强度的 AI 进行模拟对战 |
| **决策分析** | 分析历史牌局并识别决策偏差 |
| **游戏开发** | 为扑克游戏提供智能 NPC 对手 |
| **算法研究** | 验证博弈论算法与对手建模方法 |

## 项目结构

```text
poker-gto-trainer/
├── benchmark/       # 基准测试
├── cmake/           # CMake 模块
├── doc/             # 项目文档
├── docs/            # 文档与图片资源
├── packages/        # 软件包相关内容
├── CMakeLists.txt   # CMake 构建配置
├── configure.ac     # Autoconf 配置
└── COPYING          # BSD 3-Clause 许可证
```

## 常见问题

### 这个项目可以用于商业用途吗？

项目采用 BSD 3-Clause License。商业使用前请阅读 [COPYING](COPYING) 中的完整许可证条款，并确认同时遵守适用法律和第三方依赖许可证。

### CFR 算法与深度学习是什么关系？

CFR 负责策略迭代与遗憾值计算；深度学习组件用于状态价值估计与策略抽象，两者结合可用于处理更大规模的博弈树。

### 支持哪些对战模式？

项目说明支持 1v1、1v2、1v3、1v6 和 1v9 等配置，可通过配置文件切换。

### 训练一个模型需要多长时间？

当前性能记录显示，在 2×128 核、2 TB 内存的测试环境中，完整训练约需 15 天并生成 99 个模型。实际时间取决于硬件和训练参数。

### 决策延迟是多少？

当前性能记录为单步 6–10 毫秒；实际延迟取决于硬件、模型和运行配置。

### 是否支持自定义对手策略？

支持，可在 `opponent/` 目录中定义对手策略，并在配置文件中指定。

## 许可证

本项目采用 **BSD 3-Clause License**。完整条款请参阅 [COPYING](COPYING)。

使用本项目时还应遵守 [RESPONSIBLE-USE.md](RESPONSIBLE-USE.md) 中的负责任使用说明。

## 产品截图

![德州扑克 AI GTO 训练器产品截图 01](docs/assets/Screenshots/0011.png)

![德州扑克 AI GTO 训练器产品截图 02](docs/assets/Screenshots/0012.png)

![德州扑克 AI GTO 训练器产品截图 03](docs/assets/Screenshots/0013.png)

## 联系我们

| 渠道 | 联系方式 |
| --- | --- |
| Email | <ttpoker40@gmail.com> |
| Telegram | [@alibabama401](https://t.me/alibabama401) |
| Issues | [GitHub Issues](https://github.com/alibabamayun888/poker-gto-trainer/issues) |

<p align="center">
  <strong>如果 Poker GTO Trainer 对你的研究有帮助，欢迎 Star 并分享给其他开发者。</strong><br><br>
  <a href="https://github.com/alibabamayun888/poker-gto-trainer/stargazers">
    <img src="https://img.shields.io/github/stars/alibabamayun888/poker-gto-trainer?style=social" alt="Give Poker GTO Trainer a Star">
  </a>
</p>
