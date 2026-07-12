# 🛡️ SovereignAudit Framework Frequently Asked Questions (Q&A)
[English](./Q&A_and_Acknowledgments.md) | [繁體中文](./QA問答與致謝.md)

**Q1: Why is the project open-sourced, yet doesn't provide a "Starter Pack" (e.g., default parameters, initial weights, or test databases)?**

**A**: Because that crosses the red line of a "Sovereign Architecture." SovereignAudit is essentially an "ISO-like framework" that only regulates processes and carries no predefined stances or values. All governance parameters and thresholds must be configured by the deployer themselves via structured files.

If we were to provide a set of initial default values today, we would actually be exporting our own value system, which would interfere with the deployer's "ultimate right to define" their AI decision-making conditions. Therefore, we can provide the tools and logic, but please draw the "passing line" yourselves.

*   **Reference**: Please refer to "1. Architecture Design Purpose and Core Advantages" and "6. Definition of Model and Data Responsibilities" in [01. Architecture Design Purpose and Core Advantages].

---

**Q2: The framework mandates writing to a tamper-proof "Audit Log." If this includes personal data, won't it conflict with the "Right to be Forgotten" under GDPR?**

**A**: The framework leaves the flexibility for this to the deployer. After all, we aren't gods and can't compare every country's regulations one by one, so we must ask each deployer to adjust this on their own.

Therefore, the system itself does not have a built-in automatic PII (Personally Identifiable Information) masking function. The cleansing and compliant transmission of data before entering the model are the deployer's responsibility. Moreover, in practical operation, the framework already states that "full recording is not mandatory. 

To what extent the logs should be retained, deleted, or summarized is left entirely to the discretion of the deployer's professional governance or audit personnel, in accordance with local regulations. During the adjustment process, please just note that the most basic traceability capabilities must be preserved.

*   **Reference**: Please refer to "4. Audit Logs and Recording Strategy" and "6. Definition of Model and Data Responsibilities" in [01. Architecture Design Purpose and Core Advantages].

---

**Q3: This system relies heavily on structured data. What if the black-box model (BB) hallucinates and fails to output the correct format?**

**A**: We have a fallback plan prepared. If the black-box model truly cannot directly produce a structured "Response Intent," the system will capture the raw text it generates and hand it over to the open-source audit model (OS) for "Intent Reverse Engineering and Specification Extraction.

By using the white-box model to reconstruct and record the missing structured data, the process can smoothly continue.

*   **Reference**: Please refer to "0. Basic Sets and Symbol Definitions (💡 Note: Intent Reverse Engineering Mechanism)" in [03. Role Traceability Module].

---

**Q4: Won't having the open-source model (OS) calculate complex logic like the "Four Boundary Questions" cause compute costs to explode?**

**A**: Theoretically no, because the system utilizes a "Funnel-style Routing Mechanism.

The vast majority of normal traffic will pass through and be short-circuited/cleared via the upfront "Database Priority Matching" or the "O(1) Time Complexity 2+4 Rule Matrix Filtering.

Only when encountering inputs that lack precedent, or are judged as gray-area and high-risk, will they be sent into the time-consuming "Four Boundary Questions Module" for deep analysis. Good steel is used on the blade's edge; the overall compute cost has been kept down and controlled as much as possible through this routing design.

Of course, in the early operational stages of the framework, situations requiring analysis by the Four Boundary Questions will likely occur frequently. For cost considerations, you can initially choose a cheaper model and increase manual sampling to balance costs. Once a certain volume of cases has accumulated and the system begins to stabilize, you can naturally reduce manual sampling and upgrade to a better model for more accurate analysis.

*   **Reference**: Please refer to "Core Engineering Mechanisms: Resource Scheduling Optimization and Defense in Depth" in [Overview][span_17](start_span)[span_17](end_span).

---

**Q5: During intent reverse engineering, if the OS model is tricked by the user's "steganography" into extracting a "safe intent," wouldn't that result in a successful jailbreak?**

**A**: This is limited by the inherent constraints of LLM technology, and we frankly admit in our disclaimer that we cannot guarantee absolute safety in decision outcomes.

However, under our architecture, if the system is indeed tricked into extracting a "safe intent" and decides to pass it through, the final step is to "send it to the generative model (small model) to generate the final response based on the original intent.

In other words, the attacker provides a malicious prompt, but the small model will only follow that extracted "safe intent" to generate a completely non-threatening response. 

Theoretically, this effectively neutralizes the jailbreak attack in practice.

*   **Reference**: Please refer to "6. Definition of Model and Data Responsibilities" in [01. Architecture Design Purpose and Core Advantages], and "7.2 Pass Route: Response Generation and Risk Disclosure" in [06. Four Boundary Questions Module].

---

**Q6: "Your documentation is full of 'theoretically' and 'adjust on your own.' So what exactly are you trying to accomplish?"**

**A**: We want to provide a platform—one that complies with regulations, where everyone operates in an open and transparent manner, and can present evidence to mutually exchange differences in values.

Human conflict often stems from gaps in values, but not many people can accurately analyze the components of their own values. Sometimes, people don't even know what they are thinking or why they think that way. Demanding everyone to clearly articulate their thoughts is too difficult.

Therefore, we adopt a relatively objective flow of costs, combined with weightings to simulate various differences in values. Then, by using funnel-style analysis to dissect the hierarchy of these cost flows, we can clearly see where value conflicts are located, providing a foundation for discussion.

Of course, this is just the first version. There will certainly still be many problems in actual operation, but we have done our absolute best; the remaining stage belongs to you.

---

**Q7: "Besides AI auditing, how else can this framework be applied? Where is its commercial value?"**

**A**: That's a great question. As long as it involves "human" or "anthropomorphic decision-making," it can theoretically be applied anywhere. The core mechanism of this framework, which is the flow of costs and weighting, is essentially a simplified model of human interaction.

For example, we can multiply the cost matrix by a customized role multiplier. Suppose we configure a "money-grubber" character who is extremely sensitive to the flow of money. When the system determines that a decision causes the financial cost to flow to others, the multiplied value spikes, making the character react with absolute heartbreak. Conversely, if the financial cost flows to themselves, the higher the value, the more overjoyed they are. If the cost flow is nearly equal, they might become hesitant and indecisive.

By utilizing different cost dimensions and weighting multipliers, we can manifest distinct personalities. This can be applied to dynamic NPC reactions in games, or behavioral predictive analysis of commercial customers.

It can even be reverse-engineered for intimacy analysis, acting as an AI anti-attachment tool. This would allow the AI to lower the risk of dangerous dependency by automatically adjusting its conversational matrix to cool down interactions with high-risk users.

Of course, this is still a simplified application. Real human nature is far more complex and requires many more parameters to set. However, since this open-source showcase is focused on AI response generation and risk auditing, we won't bring out the blueprints for those other fields this time to avoid distracting from the main focus.

As for higher-dimensional commercial value like cross-enterprise trading of decision databases, or predictive analysis of legal cases, these will rely on various companies or institutions collectively establishing a unified, standard data specification, much like the USB standard. This is beyond the scope of our current intervention and is something we leave for the future industry ecosystem to negotiate and develop together.

---

## Acknowledgments and Project Postscript

Throughout this specification, I have repeatedly used "we" to represent the SovereignAudit project.

This is because this development journey was never one I could walk entirely alone.

Along the way, I received countless forms of help: there were AIs assisting me with translation, formatting, and untangling complex document logic; friends cheering me on; colleagues and seniors offering precious guidance; and my family providing substantial financial support and tolerance.

Although the entire project was initiated by me, getting it to where it is today is absolutely not my credit alone. I merely ignited the starting point. For the road ahead, I look forward to the members of the open-source community joining in. It is you who will give this project a real chance to step into the future.
