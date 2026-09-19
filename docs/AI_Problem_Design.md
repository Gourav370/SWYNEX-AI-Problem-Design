# SWYNEX – AI Problem Design

## Project: Support Ticket Priority Classification

### 1. Problem Statement

Customer-support teams receive many text-based tickets every day. Manually identifying which tickets require urgent attention can delay responses.

This project proposes an AI-based text classification system that reads a customer-support ticket and predicts one of three priority levels:

- High
- Medium
- Low

The system is intended to help support teams organize incoming tickets and identify potentially urgent issues more efficiently.

### 2. AI Use Case

**AI Technique:** Text Classification

**Input:** Customer-support ticket text

**Output:** High, Medium, or Low priority

**Primary User:** Customer-support operations team

**Goal:** Provide consistent and efficient ticket prioritization.

### 3. Dataset Description

The demonstration dataset is stored in:

`support_tickets.csv`

Each record contains:

- `ticket_text` – the customer's support request
- `priority_label` – the assigned priority level

The dataset contains example tickets representing High, Medium, and Low priority cases.

For a production system, the dataset should be expanded using appropriately anonymized and consented historical support tickets. Priority labels should follow documented business rules.

### 4. Constraints

1. Personally identifiable information should not be included in the dataset.
2. The system should support short and moderately long support messages.
3. Priority labels should be assigned consistently.
4. The system should return one of the three defined priority classes.
5. Human review should remain available for urgent or uncertain cases.

### 5. Success Criteria

The proposed success criteria are:

- Macro F1 score of at least 0.80 on a held-out test set.
- Accuracy of at least 0.80 as a secondary metric.
- Monitor recall for High-priority tickets separately.
- Fast enough to support near-real-time ticket triage.
- No personally identifiable information should be exposed.

### 6. Evaluation Approach

The labeled dataset should be divided into training, validation, and test sets where the dataset size permits.

The model should be evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Macro F1-score
- Confusion matrix
- High-priority recall

The AI model should also be compared with a simple keyword or rule-based baseline.

Misclassified tickets should be reviewed to identify common sources of errors.

### 7. Recommended Model

The recommended initial machine-learning baseline is:

**TF-IDF + Logistic Regression**

TF-IDF converts text into numerical features, while Logistic Regression performs the classification.

This approach is suitable as an initial baseline because it is relatively simple, fast, and interpretable.

### 8. Risks and Limitations

- The demonstration dataset is small and may not represent all real-world customer language.
- Priority can depend on business context that may not be included in the ticket.
- Ambiguous messages may be incorrectly classified.
- Class imbalance may affect model performance.
- AI predictions should support human decision-making rather than completely replace human review.

### 9. Future Improvements

Future versions could:

- Expand the labeled dataset.
- Use anonymized historical support tickets.
- Improve class balance.
- Add confidence scores.
- Introduce human review for uncertain predictions.
- Monitor model performance over time.
- Test multilingual support.
- Evaluate errors across different ticket categories.

### 10. Repository Structure

```text
SWYNEX-AI-Problem-Design/
├── README.md
├── support_tickets.csv
└── docs/
    └── AI_Problem_Design.md
