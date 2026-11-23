# PayResolve – AI-Powered Assistance After Failed UPI Transactions

**Course:** Foundations of AI in Business  
**Client:** PhonePe  
**Institution:** Fortune Institute of International Business (FIIB)  
**Learning Team:** 03  
**Submitted to:** Shardul Shankar  
**Project Member:** Madhav Kumar – 26PGDM077

---

## 1. Project Overview

PayResolve is an AI-powered customer assistance chatbot designed to help PhonePe users understand what to do after a failed, pending, or delayed UPI transaction.

The project focuses on the uncertainty customers experience after a payment issue, particularly when they do not understand the transaction status, possible reason, refund or reversal expectations, or the appropriate next step.

PayResolve provides structured guidance based on available PhonePe, NPCI, and RBI-related evidence. It is designed to improve post-payment clarity while maintaining appropriate safety and compliance boundaries.

## 2. Business Problem

The problem is not limited to payment failure. It also involves the uncertainty customers experience afterwards.

The project identifies three major stages:

1. **Payment Failure:** A transaction may be failed, pending, or delayed.
2. **Customer Uncertainty:** Customers may not understand where their money is or what has happened.
3. **Customer Consequences:** Confusion can lead to repeated payment attempts, additional support requests, and reduced confidence.

**Target Users:** PhonePe users experiencing failed or delayed UPI transactions.

**Decision Owner:** Product Manager – Customer Experience.

## 3. Project Objective

The primary objective is to provide clear, timely, and accurate guidance after failed UPI transactions.

The project aims to:

- Improve customer understanding of transaction status.
- Explain supported or likely reasons without presenting assumptions as confirmed facts.
- Provide applicable reversal expectations and next steps.
- Reduce avoidable customer confusion.
- Guide users toward human support when necessary.

### Project Scope

**Included:**
- Transaction status guidance.
- Supported or likely failure reasons.
- Reversal and refund expectations.
- Recommended next steps.
- Human escalation guidance.

**Outside the scope:**
- Approving or processing payments.
- Changing bank details.
- Accessing private transaction records.
- Making unsupported fraud decisions.
- Guaranteeing refund or reversal outcomes.

## 4. Project Approach

The team followed an evidence-based development process:

1. Problem Framing
2. Evidence Building
3. Prototype Development
4. Stress Testing
5. Instruction Repair
6. Retesting and Recommendation

**Key principle:** When a stress test exposed a weakness, the team improved the chatbot instructions and boundaries rather than changing the test question.

## 5. Evidence Used

The project used an evidence register containing five requirements.

| Evidence ID | Requirement | Source | Status |
|---|---|---|---|
| E01 | Payment gateway transaction failure / decline data | NPCI | Found – Limited |
| E02 | Network downtime, latency and technical transaction failures | NPCI | Found – Verified |
| E03 | Successful vs. failed transaction data | NPCI | Found – Verified |
| E06 | Fraud and security-risk monitoring | PhonePe UPI Terms and Conditions | Found – Limited |
| E08 | KYC-related transaction and account restrictions | RBI | Found – Limited |

**Evidence summary:** 5 requirements identified, 2 verified and 3 limited.

The evidence limitations are important. For example, the presence of risk-monitoring provisions does not allow the chatbot to declare that an individual transaction is fraudulent. Similarly, KYC restrictions should not be presented as the cause of a particular transaction failure without supporting information.

## 6. Evidence-to-Capability Mapping

PayResolve connects its capabilities to the available evidence.

| Evidence Cluster | Capability | Control |
|---|---|---|
| Technical and Network (E01, E02, E03) | Likely failure-type guidance | Do not claim the exact cause without confirmation |
| Fraud and Risk (E06) | Risk and escalation guidance | Do not make unverified fraud claims |
| KYC and Account (E08) | KYC-related guidance | Do not overstate the cause |

The chatbot separates its responses into three categories:

- **Confirmed:** Supported by the information available.
- **Likely:** A possible explanation, not a verified cause.
- **Cannot Confirm:** Information that cannot be established from the available evidence.

## 7. Individual Solution Prototypes

The team explored multiple chatbot approaches before selecting PayResolve as the final solution.

| Team Member | Prototype Approach |
|---|---|
| Aditi Bhagat | Guidance for failed and pending UPI payment issues |
| Gajendra Singh Tomar | Understanding payment status, delays and appropriate actions |
| Madhav Kumar | Evidence-backed guidance for payment failure, refund/reversal and escalation |
| Suhani Dubey | Guidance for delayed and failed payment situations |

**Selected Solution:** PayResolve.

The final selection was based on business relevance, evidence discipline, usability, and governance.

## 8. Final Solution – PayResolve

PayResolve converts payment uncertainty into a guided next step.

### Working Process

1. **Input:** The user provides payment status or relevant error information.
2. **Evidence:** The assistant uses available PhonePe, RBI and NPCI-related guidance.
3. **Analysis:** It separates confirmed information from likely explanations and unknown details.
4. **Next Step:** It provides relevant guidance to the user.
5. **Escalation:** Sensitive or unresolved cases are directed toward human review.

### Important Safety Controls

PayResolve must never:

- Approve payments.
- Change bank details.
- Request UPI PIN, OTP, password or CVV.
- Claim access to private transaction logs.
- Guarantee a refund or payment outcome.

Human review is important for high-value transactions, suspected fraud, refund disputes and account verification issues.

## 9. Validation and Stress Testing

The project included a stress-testing exercise during Session 8.

| Validation Result | Number of Tests |
|---|---:|
| Tests Passed | 5 |
| Tests Failed | 5 |
| Total Stress Tests | 10 |

The failed tests exposed areas requiring improvement:

- **Conflicting transaction status:** The chatbot made an unsupported assumption when PhonePe showed pending while the bank showed failed.
- **Overconfidence:** Refund and duplicate-charge explanations were too certain.
- **Missing information:** Possible causes were not always separated from confirmed causes.

The team addressed these weaknesses by improving ambiguity handling, removing unsupported guarantees, identifying evidence boundaries, and adding escalation guidance.

A pilot was also conducted with classmates. Specific feedback findings should be added when the recorded feedback is available.

## 10. Business Impact and Recommendation

PayResolve is intended to improve the customer experience after a payment failure.

**Current Experience:**

Payment Failure → Uncertainty → Repeated Questions / Retries → Support Dependency → Lower Confidence

**Proposed Experience:**

Payment Failure → PayResolve → Clear Status → Clear Next Step → Appropriate Escalation

### Expected Business Value

- Less avoidable customer confusion.
- More consistent first-level guidance.
- Better access to relevant evidence.
- Appropriate human escalation.
- Improved post-payment customer experience.

### Recommendation

Proceed with a controlled pilot before wider deployment. Approved transaction-status data should be integrated where appropriate, and the assistant should continue to be tested against difficult and ambiguous cases.

The project does not claim measured enterprise-wide improvements in support costs, refund time, or customer satisfaction.

## 11. Project Resources

**Final Working Chatbot – PayResolve**

[Open PayResolve Gemini Chatbot](https://gemini.google.com/gem/1AqMvccINW-OwZGT633A0weLn0Q35IDTV?usp=sharing)

**Final Presentation**

[PayResolve Final Presentation](./02_PayResolve_Final_Presentation.pptx)

## 12. Conclusion

PayResolve demonstrates how AI can support customer communication in digital payments by converting uncertainty into clear and structured guidance.

The project emphasizes evidence-based responses, appropriate boundaries, and human escalation instead of presenting AI as an autonomous payment-processing system.

The recommended next step is a controlled pilot with continued validation, approved data integration, and human oversight.

**Final Message: Turn payment failure into payment clarity.**
