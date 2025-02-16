# 🌲 Gradient Boosting: Predicting Customer Satisfaction

This page explains how gradient boosting works using a real-world example: predicting customer satisfaction at a restaurant.

---

## 🍽 Scenario: Predicting Customer Satisfaction with a Restaurant

Imagine you own a restaurant, and you want to predict how satisfied a customer will be (on a 1-10 scale) based on their dining experience.

At first, you use a very simple rule:  
**"If they order a burger, they will rate the restaurant an 8."**

---

## 🌳 Step 1: First Tree (Initial Prediction)

You collect data on 5 customers and their actual satisfaction ratings.  
Your first tree makes a simple prediction, assuming every customer gives a rating of 8:

| Customer | Ordered | Actual Satisfaction | Prediction (Tree 1) | Residual (Error) |
|----------|---------|---------------------|---------------------|------------------|
| Alice    | Burger  | 9                   | 8                   | +1               |
| Bob      | Salad   | 6                   | 8                   | -2               |
| Charlie  | Pizza   | 7                   | 8                   | -1               |
| David    | Burger  | 8                   | 8                   | 0                |
| Eve      | Salad   | 5                   | 8                   | -3               |

The **residual** is how much our prediction is off:
- **Positive residual (+1)** means we underpredicted (the customer was happier than expected).
- **Negative residual (-3)** means we overpredicted (the customer was less happy than expected).

---

## 🌱 Step 2: Second Tree (Correcting the First One)

Now, we train a second tree that learns from the errors (residuals) of the first tree.

- If the first tree underestimated (positive residual), the new tree **adds** to the prediction.
- If the first tree overestimated (negative residual), the new tree **subtracts** from the prediction.

| Customer | Ordered | Residual from Tree 1 | Tree 2 Adjustment |
|----------|---------|----------------------|-------------------|
| Alice    | Burger  | +1                   | +0.5              |
| Bob      | Salad   | -2                   | -1.0              |
| Charlie  | Pizza   | -1                   | -0.5              |
| David    | Burger  | 0                    | 0                 |
| Eve      | Salad   | -3                   | -1.5              |

---

## 🔄 Final Predictions

We update our predictions by combining the results from both trees:

**Final Prediction = Tree 1 Prediction + Tree 2 Adjustment**

| Customer | Ordered | Tree 1 Prediction | Tree 2 Adjustment | Final Prediction |
|----------|---------|-------------------|-------------------|------------------|
| Alice    | Burger  | 8                 | +0.5              | 8.5              |
| Bob      | Salad   | 8                 | -1.0              | 7.0              |
| Charlie  | Pizza   | 8                 | -0.5              | 7.5              |
| David    | Burger  | 8                 | 0                 | 8.0              |
| Eve      | Salad   | 8                 | -1.5              | 6.5              |

---

## 🌟 Key Takeaways

- **Tree 1** makes an initial guess (e.g., assuming every customer rates 8).
- **Tree 2** focuses solely on correcting the mistakes (residuals) of Tree 1.
- By **adding** the predictions of both trees, we achieve a more accurate overall prediction.
- In gradient boosting, additional trees can be trained to further correct errors, continuously improving the model.

Happy Boosting! 🚀
