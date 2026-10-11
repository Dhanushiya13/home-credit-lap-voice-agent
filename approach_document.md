# Approach Document: Home Credit LAP Voice Agent

## 1. Project Overview

The objective of this project is to build an AI voice agent using Retell AI that conducts preliminary eligibility checks for Home Credit's Loan Against Property (LAP) offer.

The agent interacts with customers naturally, gathers the required information, evaluates the preliminary eligibility criteria, and communicates the appropriate next steps.

## 2. Tools and Technologies

- **Retell AI:** Voice agent creation, prompt configuration, and test call execution.
- **Prompt Engineering:** Defining the agent's role, conversation flow, qualification rules, and response behaviour.
- **GitHub:** Versioned storage of the system prompt, test transcripts, and project documentation.
- **Google Drive:** Sharing audio recordings of test calls.

## 3. Agent Design Approach

I designed the agent using a single system prompt with clear instructions covering:

- Customer greeting and identity confirmation.
- Availability checks and callback requests.
- Explanation of the LAP offer and its maximum loan amount.
- Collection of eligibility information.
- Evaluation of eligibility rules.
- Handling of disqualifying conditions and special cases.
- Communication of the outcome and next steps.

The prompt also instructs the agent to handle information provided out of order, avoid unnecessarily repeating questions, and use corrected information when a customer changes an earlier answer.

## 4. Preliminary Eligibility Logic

The agent evaluates the following criteria:

| Criterion | Eligibility rule |
|---|---|
| Property type | Residential, commercial, and industrial properties are eligible. Agricultural property is not eligible. |
| Ownership | Sole or joint ownership is acceptable. |
| Original documents | Original property documents must be available for verification. |
| Loan amount | The offer is capped at ₹75 lakh. If the customer requests more, the agent explains the limit and asks whether they wish to proceed with ₹75 lakh. |
| Employment and income | Salaried and self-employed customers are acceptable if their income is received through a bank account. Cash-only income does not meet the requirement. |
| Property market value | The agent collects the customer's estimated market value without inventing a minimum threshold. |
| Loan tenure | The requested tenure must be between 3 and 15 years, inclusive. |

The agent should confirm preliminary eligibility only after all required criteria have been collected and satisfied.

## 5. Special-Case Handling

### Customer is busy
The agent asks for a suitable callback time, acknowledges the preference, and ends the conversation without continuing the qualification questions.

### Existing loan or EMI reduction request
The agent directs the customer to the loan-transfer specialist instead of continuing the standard LAP eligibility flow.

### Incorrect number or identity mismatch
The agent apologises and ends the conversation without disclosing further offer details.

### Missing original property documents
The agent explains that original documents are required and that the offer cannot proceed at this stage.

### Cash-based income
The agent explains the bank-account income requirement and politely ends the eligibility assessment.

### Loan amount above the offer limit
The agent explains the ₹75 lakh cap and asks whether the customer wishes to continue with the maximum offered amount.

### Invalid tenure
The agent explains the permitted tenure of 3–15 years and does not proceed when the customer requests a tenure outside that range.

## 6. Testing and Validation

I tested the agent using simulated customer conversations covering different outcomes and conversational situations.

Test scenarios included:

1. Customer meets all preliminary eligibility criteria.
2. Customer requests a callback because they are busy.
3. Customer provides an incorrect number or denies the requested identity.
4. Customer has only photocopies of property documents.
5. Customer receives income in cash.
6. Customer corrects an earlier income answer.
7. Customer requests a one-year loan tenure.
8. Customer requests ₹90 lakh and is offered the ₹75 lakh limit.
9. Customer already has a loan and wants to reduce the EMI.

The test calls and their corresponding transcripts are organised in the repository. Audio recordings are linked through the README in the `audios/` folder.

## 7. Conclusion

This project demonstrates how prompt engineering and conversational AI can be used to automate preliminary loan qualification through a voice interface.

The focus was on clear qualification rules, natural conversation, consistent handling of disqualifying conditions, and appropriate communication of next steps. The test scenarios helped evaluate the agent's behaviour and identify improvements for a more reliable customer experience.

The eligibility outcome is preliminary and does not represent final loan approval.
