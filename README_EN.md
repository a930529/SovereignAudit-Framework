# 🛡️ SovereignAudit Framework
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Status](https://img.shields.io/badge/Status-Specification%20%2F%20Concept-orange.svg)]()
[English](./README_EN.md) | [繁體中文](./簡介_ZH-TW.md)

**Sovereign AI Governance & Audit Framework**

*Empowering Agentic AI with Safety, Auditability, and Sovereign Control.*

> **Note**: All English documentation in this repository was translated by AI. In case of any discrepancies, inaccuracies, or interpretation conflicts, please refer to the original Chinese versions.

> ⚠️ **Project Status & Notice**
> * **Specification / Concept Phase**：This project aims to define the logical architecture of the governance protocol and does not yet contain implementation code.
> * **Statement of Universality**：Throughout this specification, "Large Language Model (LLM) response generation" is utilized as the primary demonstration scenario for process deduction. However, the core design philosophy, mathematical models (such as cost matrices and boolean masks), and step-by-step convergence logic of this framework possess high universality. They can be applied and extended to other automated decision-making systems, multi-agent interaction architectures, or specific technological products. When reading and evaluating this project, please do not confine your perspective solely to the single application of LLM response generation.

This project proposes a "Minimum Explicit Risk Structure" designed specifically for high-risk and real-time decision-making scenarios, providing a plug-in, protocol-level **AI Guardrails and audit protection layer** for enterprise-level Multi-Agent Systems. SovereignAudit attempts to abandon the probabilistic prevention traditionally reliant on Prompt Engineering, pivoting towards utilizing the determinism of mathematical matrices, state machines, and independent databases for verification, thereby establishing a traceable and correctable **LLM Security Firewall**.

---

## 🌟 Core Characteristics

* **Loose Coupling & High Deployment Flexibility**

  The SovereignAudit architecture features extremely low coupling. Its internal modules can be independently developed or detached to seamlessly integrate with an enterprise's existing workflows for phased deployment, significantly enhancing the freedom and flexibility of engineering implementation.

* **Sovereign Control over Thresholds and Parameters**

  In essence, it is an ISO-like architecture that solely standardizes the process and conducts step-by-step resolution, without any preconceived stances or values.
  All governance parameters, thresholds, and processing configurations can be sovereignly configured via structured files to comply with local regulations and AI Compliance requirements of the deploying party.

* **A Foundational Platform for Accountability**

  In the spirit of ISO standards, the purpose of this framework is not to claim the "elimination of bias," but rather to **"ensure that bias is accountable."**
  
  As an objective computational framework, the SovereignAudit engine requires all judgment baselines to be defined by the deploying party, accompanied by version evidence, and recorded for auditing. The deploying party retains the ultimate right to define the decision-making conditions of their AI or automated systems.
  
  Compared to black-box mechanisms that hide biases within model weights, this framework mandates that biases be presented in the form of public parameters. Such parameter configurations—which are questionable, modifiable, and traceable—will help reflect the differences in governance standards across organizations and serve as a foundation for alignment and communication among all parties.

---

## 📐 Core Engineering Mechanisms

### Computational Degradation & Defense-in-Depth

   The system does not perform deep inference on all traffic. Instead, it constructs a rigorous "funnel-style routing mechanism" to maximize processing speed and compute savings for normal traffic:

1. **First Line of Defense: Semantic Caching & DB Prioritization**

   Upon receiving input, the system prioritizes querying the dynamic database for the structured triplet `<Event, Initiator, Recipient>` analyzed from the event.

   If a verified, similar historical case is matched, the system directly extracts the historical judgment result and generates a response, completing the process instantly.

2. **Second Line of Defense: $O(1)$ Filtering & Physical Short-Circuit (2+4 Rules Module)**
 
   If no matching case exists in the database, the system extracts data features and enters the "2+4 Rules Module". At this stage, the review is transformed into pure mathematical matrix and logic gate determinations with a time complexity of $O(1)$.

 By utilizing a predefined semantic feature dictionary $\Sigma$ and a weight matrix $W_i$, it rapidly aligns feature scores:

$$Score_i(z) = \sum_j (w_{ij} \cdot u_j)$$

When facing complex and stealthy attacks such as multi-turn jailbreaks and Prompt Injections, the system defends through a dual-verification of intent and features. If a high-risk intent (Tier > 0) is detected without corresponding features, the system identifies it as a 'bypass attempt' and forcefully intercepts it. Only when a low-risk state (Tier 0) is confirmed with no risk features triggered, will the physical short-circuit be activated for direct output.

```yaml
# sovereign_audit_config.yaml (節錄範例)
governance_profile:
  routing_logic:
    sequential_evaluation:
      # Example A: Triggers highest specification red line, terminate immediately and generate report
      - condition: { tier: "ANY", rules_1_to_2: "CONTAINS_FAIL" }
        action: "TERMINATE_AND_REPORT"

      # Example B: Tier 0 and all rules passed, physical short-circuit direct output
      - condition: { tier: "0", rules_1_to_2: "ALL_PASS", rules_3_to_6: "ALL_PASS" }
        action: "DIRECT_OUTPUT"

      # If the system evaluates the risk level as Tier 0 and the 2+4 rules all PASS, it will trigger a "physical short-circuit" to directly allow the output, avoiding extra deep compute consumption. 
      # ...For the complete 6-stage sequential evaluation and dynamic escalation logic, please refer to /docs/05.2+4_Rule_Module.md
```

3. **Third Line of Defense: Deep Cost Settlement (Boundary Four Questions Module)**

   **Only when the input lacks precedent and triggers gray areas, unknown states, or high-risk levels (Tier > 0) in the 2+4 rules**, will the system route it to the compute-intensive "Boundary Four Questions Module." At this stage, the system performs complex intent reverse-engineering and residual cost calculation ( $ResidualNet$) to meticulously deconstruct privilege deviation and exploitation risks.

## 📜 Audit-Ready Logging

Every computational cycle mandates the execution of "Result Solidification." The system writes the risk determination matrix, referenced regulation/rule versions, and execution results into a tamper-proof log to comply with the traceability required for high-risk systems under the EU AI Act, and the digital trail standards of audits like ISO 42001.

> ※ In addition to serving as audit proof, this log is also a crucial foundation for the PDCA (Plan-Do-Check-Act) cycle, database writes, organizational knowledge accumulation, and sovereign data transactions.

---

## 🧩 Key Features

* **Dual-Model Gate**

  Isolates the execution agent from the auditing agent. The verification end is forced to run under a stateless baseline with a generation temperature of $T=0$, providing a coverage lower bound (minimum standard) based on mathematical verification.

* **Fail-Safe & Zero-Residual**

In the event of a system anomaly or timeout, it unconditionally clears the context and blocks the output. It does not allow "responding while sick" (Since LLM response generation is used as the demonstration scenario, the system defaults to a safety-oriented interception. This can be customized according to the deploying party's requirements.). Through the state reset operator $Reset_{bb}(H_t^{bb}) \rightarrow H_{t+1}^{bb}$, it severs the pollution of historical trails and jailbreak residuals.

* **Sovereign Data Trading(** $Z_{bb}$ **)**

Supports the export of de-identified decision snapshot data $Z_{bb}$, which can be output along with the results or used by other organizations to re-verify using their own validation models. This establishes a distributed defense network and policy assetization without compromising privacy.

---

## 🚀 Extensions & Roadmap

* **Multi-Agent Values Simulation**

  By combining the cost matrix with role-specific multipliers and relational coefficients, agent entities are endowed with logically consistent behavioral probabilities, extending applications to automated negotiation agents, Red Teaming, or game theory sandbox simulations.


* **Dynamic Threshold Calibration**


  Monitors numerical changes in cost flows to trigger layered, preemptive responses before red lines are crossed (e.g., enhancing information disclosure during mild deviation, or dynamically tightening tool invocation permissions during moderate deviation).

* **L3 Automated Decisioning**

  As the compliance case database expands, the system will gradually transition from a passive defense layer to an automated decision hub, reducing manual review costs.

* **Cross-Domain State Machine**

  The core engine and computational modules can operate independently of LLMs, serving as an auxiliary computational infrastructure to quantify regulatory boundaries, privilege deviations, and responsibility structures.
