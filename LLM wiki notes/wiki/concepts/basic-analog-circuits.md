---
title: "基礎類比電路 (Basic Analog Circuits)"
aliases:
  - 類比電路
  - Basic Analog Circuits
  - 歐姆定律與類比電路
tags:
  - concept
  - electronics
  - analog-circuits
  - measurement
  - daq
related_concepts:
  - basic-electricity.md
key_papers: []
source: "https://www.ni.com/zh-tw/shop/data-acquisition/measurement-fundamentals/analog-fundamentals/basic-analog-circuits.html"
date_added: 2026-11-24
---

# 基礎類比電路（Basic Analog Circuits）

## 定義

基礎類比電路（Basic Analog Circuits）探討連續電壓與電流訊號在電子元件與量測系統中的定量行為，涵蓋**歐姆定律（Ohm's Law）**、**功率耗散（Power Dissipation）**、**被動元件（電阻 R、電容 C、電感 L）**、**阻抗與導納**、**運算放大器（Op-Amp）**，以及**RC 濾波器（RC Filters）**。本頁為 [基礎電學觀念](basic-electricity.md) 之定量與量測實務延伸。

## 核心原理

### 1. 歐姆定律（Ohm's Law）、功率與分壓／分流

- **電阻（Resistance, $R$）**：介質阻絕電流通過的特性，單位為**歐姆（$\Omega$）**；電阻器額定功率代表其不過熱下可耗散的最大功率。
- **歐姆定律**：
  $$I = \frac{V}{R}, \qquad V = I \cdot R, \qquad R = \frac{V}{I}$$
  - 範例：對 $1\text{ M}\Omega$ 電阻施加 $10\text{ V}$，產生電流為 $10\ \mu\text{A}$。
- **功率耗散（Power, $P$）**：
  $$P = I \cdot V = \frac{V^2}{R} = I^2 \cdot R$$
  - 範例：對 $10\ \Omega$ 電阻施加 $10\text{ V}$，耗散功率為 $10\text{ W}$。
  - **量測實務警示（平方律效應）**：對數位化儀（Digitizer）的 $50\ \Omega$ 輸入端施加 $10\text{ V}$ 需耗散 $2\text{ W}$（雙通道為 $4\text{ W}$）；若電壓加倍，耗散功率將增為 **4 倍**，構成儀器輸入電壓上限。
- **串聯分壓（Voltage Divider）**：串聯電阻流經相同電流、共同分配總電壓 $E$：
  $$R_{eq} = R_1 + R_2, \qquad E_2 = E \cdot \frac{R_2}{R_1 + R_2}$$
- **並聯分流（Current Divider）**：並聯電阻承受相同電壓 $E$、依電阻分配電流：
  $$I = I_1 + I_2, \qquad R_{eq} = \frac{1}{\frac{1}{R_1} + \frac{1}{R_2}} = \frac{R_1 \cdot R_2}{R_1 + R_2}$$
- **常見量測儀器**：**多功能數位電錶（DMM）**廣泛用於自動化測試，具備高解析度（位數）、多重量測（電壓／電流／電阻）與隔離高壓量測能力。

---

### 2. 電容（Capacitance, $C$）

- 電容器以電荷形式儲存能量，電容值隨兩極板面積增加而變大、隨極板間距縮小而變大；單位為**法拉（F）**。
- **頻率特性**：電容器會隨訊號**頻率升高而降低阻抗**。
- **基本公式**：
  $$C = \frac{Q}{V}$$
  （$Q$ 為累積電荷，單位庫侖；$V$ 為兩極板電壓差）
- **串並聯等效電容**：
  - **串聯**：$\frac{1}{C_{\text{Total}}} = \frac{1}{C_1} + \frac{1}{C_2} + \cdots$（兩顆串聯：$C_{eq} = \frac{C_1 \cdot C_2}{C_1 + C_2}$）
  - **並聯**：各電容承受相同電壓，總電容直接相加：$C_{eq} = C_1 + C_2$

---

### 3. 電感（Inductance, $L$）、阻抗與導納

- 電感器透過磁場抵抗電流變化，單位為**亨利（H）**。
- **頻率特性**：電感器會隨訊號**頻率升高而提高阻抗**。
- **基本感應電壓關係**：
  $$E = L \cdot \frac{dI}{dt}$$
  > **勘誤備註**：NI 原網頁公式圖將上式誤植為 $L = E \cdot \frac{dI}{dt}$，此處已修正為標準電磁學定義 $E = L \cdot \frac{dI}{dt}$（即 $L = \frac{E}{dI/dt}$）。
- **串並聯等效電感（含互感 $M$）**：
  - **串聯（無互感）**：$L_T = L_1 + L_2$
  - **串聯（計入互感 $M$）**：$L_T = L_1 + L_2 \pm 2M$
  - **並聯（計入互感 $M$）**：$L_T = \frac{L_1 \cdot L_2 - M^2}{L_1 + L_2 - 2M}$
- **阻抗（Impedance, $Z$）與導納（Admittance, $Y$）**：
  - **阻抗**（單位 $\Omega$）：交流電（AC）在特定頻率下遭遇的總阻力，複數表示為 $Z = R + jX$（實部為電阻 $R$，虛部為電抗 $X$），亦可用極座標（幅值與相位角）表示。
  - **導納**（單位西門子 S）：阻抗的倒數，$Y = G + jB$（實部為電導 $G$，虛部為電納 $B$）。
    > **勘誤備註**：NI 原文敘述將電導括號誤寫為「電導（C）」，但公式正確寫為 $Y = G + jB$，此處統一修正為 $G$。

#### R / C / L 串並聯與頻率特性對照表

| 元件 | 單位 | 串聯等效 | 並聯等效（無互感） | 頻率升高時阻抗變化 |
|------|------|------|------|------|
| **電阻（$R$）** | 歐姆（$\Omega$） | $R_1 + R_2$ | $\frac{R_1 R_2}{R_1 + R_2}$ | 理論上不變 |
| **電容（$C$）** | 法拉（F） | $\frac{C_1 C_2}{C_1 + C_2}$ | $C_1 + C_2$ | **降低** |
| **電感（$L$）** | 亨利（H） | $L_1 + L_2$（含互感 $\pm 2M$） | $\frac{L_1 L_2}{L_1 + L_2}$（含互感見上式） | **提高** |

---

### 4. 類比放大器電路（Op-Amp）

- **基本運算放大器（Op-Amp）三級模型**：
  1. **差動放大器（Diff Amp）**：放大兩輸入端訊號之差值。
  2. **增益與頻率響應（Gain and 1st Pole）**：以傳輸函式 $H(s) = \frac{V_{out}(s)}{V_{in}(s)}$ 描述頻域振幅與相位響應。
  3. **輸出緩衝區（Output Buffer）**：提供輸出驅動能力（NI 的 DAQ 產品皆內建放大器）。
- **兩種基礎放大器組態**（*註：NI 原文直譯為「逆變／非逆變放大器」，以下採用台灣電子學慣用譯名「反相／非反相放大器」*）：

| 組態類型 | 原文譯名 | 訊號極性 | 閉迴路增益公式（$\text{Gain} = \frac{V_o}{V_s}$） | 關鍵原理 |
|------|------|------|------|------|
| **反相放大器（Inverting Amplifier）** | 逆變放大器 | 反轉極性（正入負出） | $\text{Gain} = -\frac{R_2}{R_1}$ | 運用反相輸入端**虛擬接地（Virtual Ground）**推導 |
| **非反相放大器（Non-Inverting Amplifier）** | 非逆變放大器 | 保持同極性 | $\text{Gain} = 1 + \frac{R_2}{R_1}$ | 增益恆 $\ge 1$，取決於 $R_1$、$R_2$ 比值 |

---

### 5. 類比 RC 濾波器（RC Filters）

- **RC 低通濾波器（Low-Pass Filter）**：
  - 接法：串聯電阻 $R_1$、並聯電容 $C_1$，從電容兩端取輸出 $V_{out}$。
  - 功能：通過低頻與 DC 訊號、衰減高頻訊號。
  - **時間常數與 $-3\text{ dB}$ 截止頻率（半功率點，$V_{out} = 0.707\,V_{in}$）**：
    $$t = R \cdot C, \qquad F_{3\text{dB}} = \frac{1}{2 \cdot \pi \cdot t} = \frac{1}{2 \cdot \pi \cdot R \cdot C}$$
  - **寄生濾波實務**：即使未刻意設計，受測裝置（DUT）的源電阻 $R$ 與 DMM／數位化儀的輸入電容 $C$ 也會自然構成低通濾波器，在高頻時導致訊號衰減。
- **RC 高通濾波器（High-Pass Filter）**：
  - 接法：串聯電容 $C_1$、並聯電阻 $R_1$，從電阻兩端取輸出 $V_{out}$。
  - 功能：衰減低頻與阻隔 DC、通過高頻訊號。
  - **量測儀器耦合應用**：用於 DMM、數位化儀或動態訊號擷取（DSA）裝置的輸入耦合——**串入電容為 AC 耦合（AC Coupling）**，**將電容短路則為 DC 耦合（DC Coupling）**。

## 參考來源

- [類比電路：歐姆定律與基本概念（Analog Circuits: Ohm's Law, Basic Concepts & Examples）](https://www.ni.com/zh-tw/shop/data-acquisition/measurement-fundamentals/analog-fundamentals/basic-analog-circuits.html) — NI（National Instruments Corp.）白皮書（`DocumentID: dztut-3037`，更新日期 2026-09-10）

## 相關論文

_目前尚無相關論文頁。_

## 相關概念

- [基礎電學觀念 (Basic Electricity)](basic-electricity.md) — 電壓、接地（GND）、電流、短路／斷路與數位／類比訊號之入門定性觀念
