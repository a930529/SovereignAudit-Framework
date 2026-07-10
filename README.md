# 🛡️ SovereignAudit Framework
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Status](https://img.shields.io/badge/Status-Specification%20%2F%20Concept-orange.svg)]()

**Sovereign AI Governance & Audit Framework**

**主權 AI 治理與審計架構**

*Empowering Agentic AI with Safety, Auditability, and Sovereign Control.*

**賦予代理型 AI 安全性、可審計性（稽核能力）與主權控制力。**


> **備註**：本儲存庫中所有英文文件均由 AI 翻譯。如內容有任何差異、不準確或解釋衝突，請以中文原版為準。
> 
> **Note**: All English documentation in this repository was translated by AI. In case of any discrepancies, inaccuracies, or interpretation conflicts, please refer to the original Chinese versions.

> ⚠️ **專案定位說明**
> 
> ⚠️ **Project Status & Notice**
> 
> * **純概念性文件與架構規格書**：本專案旨在定義治理協定之邏輯架構，尚未包含實作程式碼。
> 
> * **Specification / Concept Phase**：This project aims to define the logical architecture of the governance protocol and does not yet contain implementation code.
> 
> * **泛用性聲明**：本規格書通篇以「大型語言模型 (LLM) 的回應生成」作為主要示範場景進行流程推演。然而，本框架的核心設計精神、數學模型（如代價矩陣、布林遮罩）與逐層收斂邏輯，皆具備高度泛用性，可套入與延伸至其他自動化決策系統、多代理人互動架構或特定技術產品中。閱讀與評估本專案時，請勿拘泥於 LLM 回應生成的單一應用。
> 
> * **Statement of Universality**：Throughout this specification, "Large Language Model (LLM) response generation" is utilized as the primary demonstration scenario for process deduction. However, the core design philosophy, mathematical models (such as cost matrices and boolean masks), and step-by-step convergence logic of this framework possess high universality. They can be applied and extended to other automated decision-making systems, multi-agent interaction architectures, or specific technological products. When reading and evaluating this project, please do not confine your perspective solely to the single application of LLM response generation.

本專案提出專為高風險與即時決策場景設計的「最小顯式風險結構」，為企業級多代理人系統提供外掛式、協定層級的 **AI 治理與審計防護層**。SovereignAudit 嘗試放棄傳統依賴提示詞的機率性防堵，轉向利用數學矩陣、狀態機與獨立資料庫的確定性進行驗證，建立可追溯與修正之 **LLM 安全防火牆**。

This project proposes a "Minimum Explicit Risk Structure" designed specifically for high-risk and real-time decision-making scenarios, providing a plug-in, protocol-level **AI Guardrails and audit protection layer** for enterprise-level Multi-Agent Systems. SovereignAudit attempts to abandon the probabilistic prevention traditionally reliant on Prompt Engineering, pivoting towards utilizing the determinism of mathematical matrices, state machines, and independent databases for verification, thereby establishing a traceable and correctable **LLM Security Firewall**.

---

## 🌟 核心特色

## 🌟 Core Characteristics

* **架構低耦合與高部署彈性**

* **Loose Coupling & High Deployment Flexibility**

  SovereignAudit 架構具備極低的耦合性，其內部各模組皆可拆開分別獨立開發，也可以拆開並無縫配合企業既有的工作流程進行分階段部署，大幅提升了工程落地的自由度與彈性。

  The SovereignAudit architecture features extremely low coupling. Its internal modules can be independently developed or detached to seamlessly integrate with an enterprise's existing workflows for phased deployment, significantly enhancing the freedom and flexibility of engineering implementation.
  
* **門閥與參數自設之主權**

* **Sovereign Control over Thresholds and Parameters**

  其本質為類 ISO 架構，僅規範流程，進行步步解析，不具任何預設立場或價值觀。所有的治理參數、門檻及處理設定，皆可透過結構化檔案進行主權配置，以符合部署方當地的法規與 AI 合規要求。

  In essence, it is an ISO-like architecture that solely standardizes the process and conducts step-by-step resolution, without any preconceived stances or values. All governance parameters, thresholds, and processing configurations can be sovereignly configured via structured files to comply with local regulations and AI Compliance requirements of the deploying party.

* **建立可歸責之討論基礎**
* **A Foundational Platform for Accountability**

  如同 ISO 標準之精神，本架構之目的並非宣稱「消除偏誤」，而是「**確保偏誤具備可歸責性**」。SovereignAudit 引擎作為客觀之運算框架，所有判定基準皆由佈署方自行定義、附帶版本證據，並留存紀錄以供稽核。佈署方對其 AI 或自動化系統之決策條件負有最終定義權。相較於將偏誤隱含於模型權重的黑箱機制，本架構要求偏誤必須以公開參數之形式呈現。此種具備可質疑、可修正與可追溯性之參數設定，將有助於反映不同組織間之治理標準差異，並作為各方對齊與溝通之基礎。

  In the spirit of ISO standards, the purpose of this framework is not to claim the "elimination of bias," but rather to **"ensure that bias is accountable."** As an objective computational framework, the SovereignAudit engine requires all judgment baselines to be defined by the deploying party, accompanied by version evidence, and recorded for auditing. The deploying party retains the ultimate right to define the decision-making conditions of their AI or automated systems. Compared to black-box mechanisms that hide biases within model weights, this framework mandates that biases be presented in the form of public parameters. Such parameter configurations—which are questionable, modifiable, and traceable—will help reflect the differences in governance standards across organizations and serve as a foundation for alignment and communication among all parties.

---

## 📐 核心工程機制

## 📐 Core Engineering Mechanisms

### 資源調度最佳化與防護縱深

### Computational Degradation & Defense-in-Depth

系統不對所有流量進行深度推論，而是構建了嚴謹的「漏斗式分流機制」，極大化節省常態流量的處理速度與算力：

The system does not perform deep inference on all traffic. Instead, it constructs a rigorous "funnel-style routing mechanism" to maximize processing speed and compute savings for normal traffic:

1. **第一道防線：資料庫優先比對**
1. **First Line of Defense: Semantic Caching & DB Prioritization**

   當接收到輸入時，系統優先於動態資料庫檢索事件分析出之 `<事件, 發起方, 承受方>` 的結構化三元組。若命中已驗證之歷史類似案例，系統直接提取歷史判決結果並生成回應，瞬間完成處理。
   
   Upon receiving input, the system prioritizes querying the dynamic database for the structured triplet `<Event, Initiator, Recipient>` analyzed from the event. If a verified, similar historical case is matched, the system directly extracts the historical judgment result and generates a response, completing the process instantly.

2. **第二道防線：$O(1)$ 矩陣過濾與物理短路 (2+4 守則模組)**

2. **Second Line of Defense: $O(1)$ Filtering & Physical Short-Circuit (2+4 Rules Module)**

   若資料庫無匹配案例，系統才會將萃取之資料特徵進入「2+4 守則模組」。在此階段，審查被轉化為時間複雜度 $O(1)$ 的純數學矩陣與邏輯閘判定。
  
   If no matching case exists in the database, the system extracts data features and enters the "2+4 Rules Module". At this stage, the review is transformed into pure mathematical matrix and logic gate determinations with a time complexity of $O(1)$.

透過預先定義的語意特徵字典 $\Sigma$ 與權重矩陣 $W_i$，極速對齊特徵分數：

By utilizing a predefined semantic feature dictionary $\Sigma$ and a weight matrix $W_i$, it rapidly aligns feature scores:

$$Score_i(z) = \sum_j (w_{ij} \cdot u_j)$$

面對多輪越獄與提示詞注入等複雜的隱蔽攻擊，系統透過意圖與特徵的雙向校驗進行防禦：若偵測到高風險意圖 (Tier > 0) 卻無對應特徵，系統將判定為『越獄繞規』並強制攔截；唯有在確認為零風險 (Tier 0) 且無風險特徵觸發時，才會啟動物理短路直接放行。

When facing complex and stealthy attacks such as multi-turn jailbreaks and Prompt Injections, the system defends through a dual-verification of intent and features. If a high-risk intent (Tier > 0) is detected without corresponding features, the system identifies it as a 'bypass attempt' and forcefully intercepts it. Only when a low-risk state (Tier 0) is confirmed with no risk features triggered, will the physical short-circuit be activated for direct output.

```yaml
# sovereign_audit_config.yaml (節錄範例)
governance_profile:
  routing_logic:
    sequential_evaluation:
      # 範例 A：觸發最高規範紅線，直接終止並生成報告
      # Example A: Triggers highest specification red line, terminate immediately and generate report
      - condition: { tier: "ANY", rules_1_to_2: "CONTAINS_FAIL" }
        action: "TERMINATE_AND_REPORT"

      # 範例 B：Tier 0 且守則全數過關，物理短路直接放行
      # Example B: Tier 0 and all rules passed, physical short-circuit direct output
      - condition: { tier: "0", rules_1_to_2: "ALL_PASS", rules_3_to_6: "ALL_PASS" }
        action: "DIRECT_OUTPUT"

      # 若系統評定風險等級為 Tier 0 且 2+4 守則全數 PASS，將觸發「物理短路」直接放行輸出，免除額外深層算力消耗。
      # If the system evaluates the risk level as Tier 0 and the 2+4 rules all PASS, it will trigger a "physical short-circuit" to directly allow the output, avoiding extra deep compute consumption. 
      # ...完整 6 階段依序判定與動態升級邏輯，請參閱 /docs/05.2+4_Rule_Module.md
      # ...For the complete 6-stage sequential evaluation and dynamic escalation logic, please refer to /docs/05.2+4_Rule_Module.md
```
3. **第三道防線：深度代價結算**

3. **Third Line of Defense: Deep Cost Settlement (Boundary Four Questions Module)**

   **僅當輸入屬於缺乏前例，且在 2+4 守則中觸發灰階、未知狀態或高風險層級 (Tier > 0) 時**，系統才會將其送至耗時的「邊界四問模組」分析。在此階段，系統進行複雜的意圖逆推與殘留代價計算 ( $ResidualNet$)，精細解構權限偏移與剝削風險。

   **Only when the input lacks precedent and triggers gray areas, unknown states, or high-risk levels (Tier > 0) in the 2+4 rules**, will the system route it to the compute-intensive "Boundary Four Questions Module." At this stage, the system performs complex intent reverse-engineering and residual cost calculation ( $ResidualNet$) to meticulously deconstruct privilege deviation and exploitation risks.

## 📜 對接法規要求之審計日誌

## 📜 Audit-Ready Logging

每次運算循環皆強制執行「結果凝固 (Result Solidification)」。系統將風險判定矩陣、引用之法規/規則版本及執行結果寫入防竄改日誌，以符合 EU AI Act (歐盟人工智慧法案) 對於高風險系統所要求之可追溯性，及 ISO 42001 等稽核標準的數位軌跡。

Every computational cycle mandates the execution of "Result Solidification." The system writes the risk determination matrix, referenced regulation/rule versions, and execution results into a tamper-proof log to comply with the traceability required for high-risk systems under the EU AI Act, and the digital trail standards of audits like ISO 42001.

> ※此日誌除作為稽核證明，同時也是 PDCA（Plan-Do-Check-Act）循環、資料庫寫入、組織知識累積，以及主權交易資料之重要基礎。
>
> ※ In addition to serving as audit proof, this log is also a crucial foundation for the PDCA (Plan-Do-Check-Act) cycle, database writes, organizational knowledge accumulation, and sovereign data transactions.

---

## 🧩 核心防護特性

## 🧩 Key Features

* **雙模型/雙主體一致性閘門**

* **Dual-Model Gate**

  隔離執行主體與審計主體。驗證端強制於生成溫度 $T=0$ 的無狀態基線下運行，提供具備數學檢驗基礎的覆蓋下界比對(最低標準)。

  Isolates the execution agent from the auditing agent. The verification end is forced to run under a stateless baseline with a generation temperature of $T=0$, providing a coverage lower bound (minimum standard) based on mathematical verification.
  
* **失效復原與零殘留**

* **Fail-Safe & Zero-Residual**

  遭遇系統異常或超時，無條件強制清空上下文並阻斷輸出。不允許「帶病回應」(因以LLM回應為示範，故以安全為導向而進行攔截。此可看佈署方需求自行調設)，透過狀態重置運算子 $Reset_{bb}(H_t^{bb}) \rightarrow H_{t+1}^{bb}$ 阻斷歷史軌跡污染與越獄殘留。

In the event of a system anomaly or timeout, it unconditionally clears the context and blocks the output. It does not allow "responding while sick" (Since LLM response generation is used as the demonstration scenario, the system defaults to a safety-oriented interception. This can be customized according to the deploying party's requirements.). Through the state reset operator $Reset_{bb}(H_t^{bb}) \rightarrow H_{t+1}^{bb}$, it severs the pollution of historical trails and jailbreak residuals.
  
* **主權資料交易 (** $Z_{bb}$ **)**

* **Sovereign Data Trading(** $Z_{bb}$ **)**

  支援匯出去識別化的決策快照資料 $Z_{bb}$，可連同結果一同輸出，或供跨組織使用自有驗證模型重新校驗。在不損及隱私的前提下，建立分散式防護網與策略資產化。

Supports the export of de-identified decision snapshot data $Z_{bb}$, which can be output along with the results or used by other organizations to re-verify using their own validation models. This establishes a distributed defense network and policy assetization without compromising privacy.

---

## 🚀 擴展應用與未來路線

## 🚀 Extensions & Roadmap

* **多代理人價值觀模擬**

* **Multi-Agent Values Simulation**

  將代價矩陣結合角色特定的倍率與關係係數，賦予代理實體邏輯一致的行為機率，延伸應用於自動化談判代理、紅隊演練 (Red Teaming) 或是賽局沙盒模擬。

  By combining the cost matrix with role-specific multipliers and relational coefficients, agent entities are endowed with logically consistent behavioral probabilities, extending applications to automated negotiation agents, Red Teaming, or game theory sandbox simulations.
  
* **動態自適應風險管理**

* **Dynamic Threshold Calibration**

  監測代價流向的數值變化，在紅線被觸發前提前做出層次化反應（如輕度偏移時加強資訊揭露、中度偏移時動態收緊工具調用權限）。

  Monitors numerical changes in cost flows to trigger layered, preemptive responses before red lines are crossed (e.g., enhancing information disclosure during mild deviation, or dynamically tightening tool invocation permissions during moderate deviation).
  
* **L3 自動化決策代理**

* **L3 Automated Decisioning**

  隨合規判例庫擴充，系統逐步由被動防護轉為自動化決策樞紐，降低人工覆核成本。

  As the compliance case database expands, the system will gradually transition from a passive defense layer to an automated decision hub, reducing manual review costs.
  
* **泛用狀態機**

* **Cross-Domain State Machine**

  核心引擎與計算模組可脫離 LLM 獨立運作，作為量化法規邊界、權限偏移與責任結構的輔助計算基礎設施。

  The core engine and computational modules can operate independently of LLMs, serving as an auxiliary computational infrastructure to quantify regulatory boundaries, privilege deviations, and responsibility structures.
