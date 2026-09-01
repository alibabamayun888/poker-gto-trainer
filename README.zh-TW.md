# Poker GTO Trainer｜撲克 GTO 訓練器與德州撲克 AI 策略工具

[简体中文](README.md) | [繁體中文](README.zh-TW.md) | [English](README.en.md)

<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++17">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.10+">
  <img src="https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch 2.0+">
  <img src="https://img.shields.io/badge/GTO-Strategy-orange?style=for-the-badge" alt="GTO Strategy">
  <img src="https://img.shields.io/badge/CFR-Algorithm-blueviolet?style=for-the-badge" alt="CFR Algorithm">
</p>

<p align="center">
  <strong>基於 CFR 演算法與深度神經網路的德州撲克 GTO 策略訓練和決策分析工具</strong><br>
  <strong>Poker GTO Trainer | Texas Hold'em AI Strategy Tool | CFR + Deep Learning</strong><br>
  支援 1v1 至 1v9 對戰、自我博弈訓練、策略評估、API 整合與視覺化分析
</p>

## 目錄

- [專案簡介](#專案簡介)
- [功能特色](#功能特色)
- [技術架構](#技術架構)
- [演算法原理](#演算法原理)
- [快速開始](#快速開始)
- [API 範例](#api-範例)
- [訓練流程](#訓練流程)
- [視覺化工具](#視覺化工具)
- [效能資料](#效能資料)
- [應用情境](#應用情境)
- [專案結構](#專案結構)
- [常見問題](#常見問題)
- [授權條款](#授權條款)
- [產品截圖](#產品截圖)
- [聯絡我們](#聯絡我們)

## 專案簡介

**Poker GTO Trainer（撲克 GTO 訓練器）**是一款面向開發者、研究人員和撲克策略學習者的德州撲克 AI 工具。專案結合**反事實遺憾最小化（Counterfactual Regret Minimization，CFR）演算法**與**深度神經網路**，用於學習、訓練和驗證 GTO（Game Theory Optimal，賽局理論最佳化）策略。

專案支援 **1v1 單挑至 1v9 多人對戰**設定，透過自我博弈強化學習持續改善策略，並提供決策分析、策略評估、模型匯出、開發者 API 和視覺化工具。它適用於德州撲克 GTO 學習、撲克 AI 研究、演算法驗證、AI 陪練和遊戲開發。

## 功能特色

### 核心能力

| 特色 | 說明 |
| --- | --- |
| **GTO 策略學習** | 透過 CFR 迭代訓練，學習接近納許均衡的策略 |
| **1v1 單挑模式** | Heads-Up No-Limit Texas Hold'em 標準對戰 |
| **1vN 多人模式** | 支援 1v2、1v3、1v6、1v9 等對戰設定 |
| **毫秒級決策** | 單步決策延遲為 6–10 毫秒 |
| **自我博弈訓練** | 透過自我對弈持續改善策略 |
| **決策視覺化** | 顯示行動機率、期望值和 regret 值 |
| **開發者 API** | 提供 Python/C++ API，方便整合第三方系統 |

### 訓練與評估

| 模組 | 功能 |
| --- | --- |
| **自我博弈訓練** | 自動進行大規模自我對弈並產生訓練資料 |
| **策略評估** | 與隨機策略、規則基準及其他 AI 進行對戰評估 |
| **對手建模** | 支援選用的對手行為建模與自適應策略調整 |
| **模型匯出** | 匯出訓練後的策略模型用於部署 |

## 技術架構

| 層級 | 技術 | 說明 |
| --- | --- | --- |
| **核心計算引擎** | C++17 / Boost.Asio | CFR 計算與賽局樹搜尋 |
| **訓練框架** | Python 3.10+ / PyTorch 2.0+ | 神經網路訓練與策略最佳化 |
| **決策 API** | Python / gRPC | 提供即時決策服務介面 |
| **視覺化前端** | Python / Matplotlib / Streamlit | 策略視覺化與互動分析 |
| **資料快取** | Redis | 狀態快取與即時資料同步 |
| **通訊協定** | Protobuf / gRPC | 跨語言服務通訊 |

## 演算法原理

### 反事實遺憾最小化（CFR）

CFR 是一種用於求解**不完全資訊賽局**的迭代演算法，也是撲克 AI 與德州撲克 GTO 策略研究中的常用方法：

1. **建構賽局樹**：遍歷目前資訊集下的可能行動。
2. **計算反事實價值**：評估假設採取各行動時的期望收益。
3. **更新遺憾值**：記錄未採取行動所對應的遺憾程度。
4. **策略平均**：根據累積遺憾值產生新的行為策略。
5. **迭代收斂**：重複以上流程，使策略逐漸接近納許均衡。

### 深度神經網路元件

- **狀態編碼器**：將公共牌、手牌和下注歷史編碼為向量。
- **價值網路**：估計目前資訊集的反事實價值。
- **策略網路**：輸出每個合法行動的機率分布。

```text
目前遊戲狀態（手牌 + 公共牌 + 下注歷史）
                      ↓
               狀態編碼器 → 向量表示
                      ↓
               策略網路 → 行動機率
                      ↓
               價值網路 → 期望收益
                      ↓
          輸出行動、信心度與期望值
```

## 快速開始

### 環境需求

- **OS**：Ubuntu 20.04+ / CentOS 8+ / macOS 12+
- **Compiler**：GCC 9.4+ / Clang 12+
- **Build**：CMake 3.20+
- **Python**：3.10+
- **PyTorch**：2.0+
- **Redis**：6.0+

### 安裝步驟

```bash
# 1. 複製儲存庫
git clone https://github.com/alibabamayun888/poker-gto-trainer.git
cd poker-gto-trainer

# 2. 安裝 Python 相依套件
pip install -r requirements.txt

# 3. 編譯 C++ 核心
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)

# 4. 執行測試
cd ..
python -m pytest tests/ -v
```

### 執行對戰

```bash
# 啟動 1v1 對戰
python main.py --mode=heads-up --model=models/gto-v1.pt

# 啟動 1v9 多人對戰
python main.py --mode=multiplayer --model=models/gto-v1.pt --opponents=9
```

## API 範例

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

## 訓練流程

```bash
cp conf/train_example.yaml conf/train.yaml
vim conf/train.yaml
python main.py --mode=train --config=conf/train.yaml
python visualize/training_monitor.py --log=logs/training.log
python main.py --mode=eval --model=outputs/model-v1.pt
```

## 視覺化工具

```bash
python visualize/decision_board.py --model=models/gto-v1.pt
python visualize/strategy_heatmap.py --model=models/gto-v1.pt --position=BTN
```

## 效能資料

測試環境：AMD EPYC 2×128 Cores、2 TB RAM、Ubuntu 22.04。

| 指標 | 數值 |
| --- | --- |
| **決策延遲** | 6–10 毫秒/步 |
| **1v1 勝率 vs 隨機策略** | 85% |
| **1v1 勝率 vs 規則基準** | 72% |
| **1v1 勝率 vs CFR 基準** | 58% |
| **訓練收斂速度** | 15 天 / 99 個模型 |
| **最大支援對戰人數** | 1v9 |

> 效能結果與硬體、編譯選項、模型版本和測試設定有關。重現或引用資料時，請同時記錄完整測試環境。

## 應用情境

| 情境 | 說明 |
| --- | --- |
| **策略學習** | 透過 AI 決策分析學習德州撲克 GTO 策略 |
| **AI 陪練** | 與不同強度的 AI 進行模擬對戰 |
| **決策分析** | 分析歷史牌局並識別決策偏差 |
| **遊戲開發** | 為撲克遊戲提供智慧 NPC 對手 |
| **演算法研究** | 驗證賽局理論演算法與對手建模方法 |

## 專案結構

```text
poker-gto-trainer/
├── benchmark/       # 基準測試
├── cmake/           # CMake 模組
├── doc/             # 專案文件
├── docs/            # 文件與圖片資源
├── packages/        # 套件相關內容
├── CMakeLists.txt   # CMake 建置設定
├── configure.ac     # Autoconf 設定
└── COPYING          # BSD 3-Clause 授權條款
```

## 常見問題

### 這個專案可以用於商業用途嗎？

專案採用 BSD 3-Clause License。商業使用前請閱讀 [COPYING](COPYING) 中的完整授權條款，並確認同時遵守適用法律和第三方相依套件授權。

### CFR 演算法與深度學習有什麼關係？

CFR 負責策略迭代與遺憾值計算；深度學習元件用於狀態價值估計與策略抽象，兩者結合可用於處理更大規模的賽局樹。

### 支援哪些對戰模式？

專案說明支援 1v1、1v2、1v3、1v6 和 1v9 等設定，可透過設定檔切換。

### 訓練一個模型需要多長時間？

目前效能記錄顯示，在 2×128 核、2 TB 記憶體的測試環境中，完整訓練約需 15 天並產生 99 個模型。實際時間取決於硬體和訓練參數。

### 決策延遲是多少？

目前效能記錄為單步 6–10 毫秒；實際延遲取決於硬體、模型和執行設定。

### 是否支援自訂對手策略？

支援，可在 `opponent/` 目錄中定義對手策略，並在設定檔中指定。

## 授權條款

本專案採用 **BSD 3-Clause License**。完整條款請參閱 [COPYING](COPYING)。

使用本專案時亦應遵守 [RESPONSIBLE-USE.md](RESPONSIBLE-USE.md) 中的負責任使用說明。

## 產品截圖

![德州撲克 AI GTO 訓練器產品截圖 01](docs/assets/Screenshots/0011.png)

![德州撲克 AI GTO 訓練器產品截圖 02](docs/assets/Screenshots/0012.png)

![德州撲克 AI GTO 訓練器產品截圖 03](docs/assets/Screenshots/0013.png)

## 聯絡我們

| 管道 | 聯絡方式 |
| --- | --- |
| Email | <ttpoker40@gmail.com> |
| Telegram | [@alibabama401](https://t.me/alibabama401) |
| Issues | [GitHub Issues](https://github.com/alibabamayun888/poker-gto-trainer/issues) |

<p align="center">
  <strong>如果 Poker GTO Trainer 對你的研究有幫助，歡迎 Star 並分享給其他開發者。</strong><br><br>
  <a href="https://github.com/alibabamayun888/poker-gto-trainer/stargazers">
    <img src="https://img.shields.io/github/stars/alibabamayun888/poker-gto-trainer?style=social" alt="Give Poker GTO Trainer a Star">
  </a>
</p>
