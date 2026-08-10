# 📊 Confusion Matrix & Classification Report

This README explains the **Confusion Matrix** and **Classification Report**, two important tools used to evaluate the performance of a **classification machine learning model**.

---

## 📌 Table of Contents

* [1. Confusion Matrix](#1-confusion-matrix)
* [2. Confusion Matrix Components](#2-confusion-matrix-components)
* [3. Accuracy](#3-accuracy)
* [4. Precision](#4-precision)
* [5. Recall](#5-recall)
* [6. Specificity](#6-specificity)
* [7. F1-Score](#7-f1-score)
* [8. Error Rate](#8-error-rate)
* [9. Classification Report](#9-classification-report)
* [10. Example](#10-example)
* [11. When to Use Which Metric](#11-when-to-use-which-metric)
* [12. Python Implementation](#12-python-implementation)

---

# 1. Confusion Matrix

A **Confusion Matrix** is a table used to evaluate the performance of a classification model.

For a binary classification problem, the matrix contains four important values:

| Actual / Predicted |            Positive |            Negative |
| ------------------ | ------------------: | ------------------: |
| **Positive**       |  True Positive (TP) | False Negative (FN) |
| **Negative**       | False Positive (FP) |  True Negative (TN) |

The four components are:

### True Positive (TP)

The model predicts **Positive**, and the actual value is also **Positive**.

Example:

> Actual: Spam
> Predicted: Spam

---

### True Negative (TN)

The model predicts **Negative**, and the actual value is also **Negative**.

Example:

> Actual: Not Spam
> Predicted: Not Spam

---

### False Positive (FP)

The model predicts **Positive**, but the actual value is **Negative**.

Example:

> Actual: Not Spam
> Predicted: Spam

This is also called a **Type I Error**.

---

### False Negative (FN)

The model predicts **Negative**, but the actual value is **Positive**.

Example:

> Actual: Spam
> Predicted: Not Spam

This is also called a **Type II Error**.

---

# 2. Confusion Matrix Components

The four values can be summarized as:

```text
                 Predicted
                Positive  Negative
Actual Positive    TP        FN
       Negative    FP        TN
```

These four values are used to calculate most classification metrics.

---

# 3. Accuracy

**Accuracy** tells us how many predictions the model classified correctly out of all predictions.

### Formula

```text
Accuracy = (TP + TN) / (TP + TN + FP + FN)
```

Or as a percentage:

```text
Accuracy (%) = [(TP + TN) / Total Samples] × 100
```

### Example

Suppose:

```text
TP = 80
TN = 90
FP = 10
FN = 20
```

Then:

```text
Accuracy = (80 + 90) / (80 + 90 + 10 + 20)

         = 170 / 200

         = 0.85

         = 85%
```

### Interpretation

The model correctly classified **85% of all samples**.

### ⚠️ Important

Accuracy can be misleading when the dataset is **imbalanced**.

For example, if 95% of the data belongs to one class, a model that always predicts that class can achieve 95% accuracy while performing poorly on the minority class.

---

# 4. Precision

**Precision** answers:

> "Out of all samples predicted as Positive, how many were actually Positive?"

### Formula

```text
Precision = TP / (TP + FP)
```

### Example

```text
TP = 80
FP = 10

Precision = 80 / (80 + 10)

          = 80 / 90

          = 0.8889

          ≈ 88.89%
```

### Interpretation

When the model predicts Positive, it is correct approximately **88.89% of the time**.

### Precision is important when:

**False Positives are costly.**

Examples:

* Spam detection
* Fraud detection
* Email classification

---

# 5. Recall

Recall is also called:

* **Sensitivity**
* **True Positive Rate (TPR)**

Recall answers:

> "Out of all actual Positive samples, how many did the model correctly identify?"

### Formula

```text
Recall = TP / (TP + FN)
```

### Example

```text
TP = 80
FN = 20

Recall = 80 / (80 + 20)

       = 80 / 100

       = 0.80

       = 80%
```

### Interpretation

The model successfully identified **80% of all actual Positive samples**.

### Recall is important when:

**False Negatives are costly.**

Examples:

* Disease detection
* Fraud detection
* Security threat detection

---

# 6. Specificity

Specificity measures how well the model identifies actual Negative samples.

It is also called the:

**True Negative Rate (TNR)**

### Formula

```text
Specificity = TN / (TN + FP)
```

### Example

```text
TN = 90
FP = 10

Specificity = 90 / (90 + 10)

            = 90 / 100

            = 90%
```

### Interpretation

The model correctly identifies **90% of all actual Negative samples**.

---

# 7. F1-Score

The **F1-Score** is the harmonic mean of Precision and Recall.

It is useful when we want a balance between:

* Precision
* Recall

### Formula

```text
F1 = 2 × (Precision × Recall) / (Precision + Recall)
```

Using the example:

```text
Precision = 88.89%
Recall = 80%
```

Then:

```text
F1 ≈ 84.21%
```

### Alternative Formula

F1 can also be calculated directly from the confusion matrix:

```text
F1 = 2TP / (2TP + FP + FN)
```

### Interpretation

A higher F1-Score means the model has a better balance between Precision and Recall.

---

# 8. Error Rate

The **Error Rate** tells us the percentage of predictions that the model classified incorrectly.

### Formula

```text
Error Rate = (FP + FN) / (TP + TN + FP + FN)
```

It can also be calculated as:

```text
Error Rate = 1 - Accuracy
```

or:

```text
Error Rate (%) = 100 - Accuracy (%)
```

### Example

If:

```text
Accuracy = 85%
```

Then:

```text
Error Rate = 100% - 85%

           = 15%
```

### Interpretation

The model makes incorrect predictions for approximately **15% of the samples**.

---

# 9. Classification Report

A **Classification Report** provides several evaluation metrics for each class.

A typical classification report looks like:

```text
              precision    recall  f1-score   support

Class 0          0.90       0.85      0.87       100
Class 1          0.80       0.88      0.84        90

accuracy                              0.86       190
macro avg         0.85       0.87      0.86       190
weighted avg      0.85       0.86      0.85       190
```

---

## Precision

Measures how many predicted samples for a class were actually correct.

```text
Precision = TP / (TP + FP)
```

---

## Recall

Measures how many actual samples of a class were correctly identified.

```text
Recall = TP / (TP + FN)
```

---

## F1-Score

Measures the balance between Precision and Recall.

```text
F1 = 2 × (Precision × Recall) / (Precision + Recall)
```

---

## Support

**Support** represents the number of actual samples belonging to each class.

For example:

```text
Class 0 → support = 100
Class 1 → support = 90
```

This means there are:

* 100 actual samples of Class 0
* 90 actual samples of Class 1

---

# 10. Macro Average

The **Macro Average** calculates the metric independently for every class and then takes the simple average.

For example:

```text
Macro Precision =
(Precision Class 0 + Precision Class 1) / 2
```

For `N` classes:

```text
Macro Average = Sum of metric for each class / N
```

### Important

Every class receives **equal importance**, regardless of how many samples it contains.

This makes macro average particularly useful when evaluating **imbalanced datasets**.

---

# 11. Weighted Average

The **Weighted Average** calculates the metric for each class and weights it according to the number of samples in that class.

### Formula

```text
Weighted Average =
Σ(metric × class support) / Total Support
```

### Important

Classes with more samples have more influence on the final score.

---

# 12. Quick Formula Reference

| Metric                   | Formula                                         |
| ------------------------ | ----------------------------------------------- |
| **Accuracy**             | `(TP + TN) / (TP + TN + FP + FN)`               |
| **Error Rate**           | `(FP + FN) / Total`                             |
| **Precision**            | `TP / (TP + FP)`                                |
| **Recall / Sensitivity** | `TP / (TP + FN)`                                |
| **Specificity**          | `TN / (TN + FP)`                                |
| **F1-Score**             | `2 × Precision × Recall / (Precision + Recall)` |
| **F1-Score (direct)**    | `2TP / (2TP + FP + FN)`                         |
| **False Positive Rate**  | `FP / (FP + TN)`                                |
| **False Negative Rate**  | `FN / (FN + TP)`                                |

---

# 13. Relationship Between Metrics

A useful way to remember the metrics:

```text
                    Predicted Positive
                           |
                    +------+------+
                    |             |
                  TP             FP
                    |             |
Actual Positive ----+             +---- Actual Negative
                    |
                  FN
                    |
                    +---- Predicted Negative
```

### Precision focuses on:

```text
Predicted Positive
       ↓
TP / (TP + FP)
```

**Question:**

> "When I predict Positive, how often am I right?"

### Recall focuses on:

```text
Actual Positive
       ↓
TP / (TP + FN)
```

**Question:**

> "How many actual Positives did I find?"

### Specificity focuses on:

```text
Actual Negative
       ↓
TN / (TN + FP)
```

**Question:**

> "How many actual Negatives did I correctly identify?"

---

# 14. Python Implementation

Using `scikit-learn`:

```python
from sklearn.metrics import (
    confusion_matrix,
    classification_report,
    accuracy_score
)

# Confusion Matrix
cm = confusion_matrix(y_test, y_pred)

print("Confusion Matrix:")
print(cm)

# Classification Report
print("\nClassification Report:")
print(classification_report(y_test, y_pred))

# Accuracy
accuracy = accuracy_score(y_test, y_pred)

print("\nAccuracy:", accuracy)
```

---

# 15. Visualizing the Confusion Matrix

Using `seaborn`:

```python
import seaborn as sns
import matplotlib.pyplot as plt
from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test, y_pred)

sns.heatmap(
    cm,
    annot=True,
    fmt="d",
    cmap="Blues"
)

plt.xlabel("Predicted")
plt.ylabel("Actual")
plt.title("Confusion Matrix")
plt.show()
```

---

# 16. Which Metric Should You Use?

| Situation                                    | Important Metric                        |
| -------------------------------------------- | --------------------------------------- |
| Overall correctness                          | **Accuracy**                            |
| False Positives are expensive                | **Precision**                           |
| False Negatives are expensive                | **Recall**                              |
| Need balance between Precision & Recall      | **F1-Score**                            |
| Need to measure correct Negative predictions | **Specificity**                         |
| Dataset is imbalanced                        | **F1 / Precision / Recall / Macro Avg** |
| Simple balanced classification               | **Accuracy**                            |

---

# 17. Key Takeaways

### Accuracy

> How many predictions were correct overall?

### Precision

> When the model says Positive, how often is it correct?

### Recall

> Out of all actual Positives, how many did the model find?

### Specificity

> Out of all actual Negatives, how many did the model correctly identify?

### F1-Score

> How well does the model balance Precision and Recall?

### Error Rate

> How many predictions were incorrect?

### Confusion Matrix

> Shows exactly where the model's predictions are correct or incorrect.

### Classification Report

> Provides Precision, Recall, F1-Score, and Support for each class.

---

## 📚 Summary

For a classification model, don't rely only on **Accuracy**. Always inspect the **Confusion Matrix** and **Classification Report** to understand how the model performs for individual classes.

A good evaluation generally considers:

```text
Confusion Matrix
       ↓
TP, TN, FP, FN
       ↓
Precision
Recall
Specificity
F1-Score
Accuracy
Error Rate
       ↓
Overall Model Performance
```
