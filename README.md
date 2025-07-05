# 🛒 Multilingual E-Commerce Intent Classification

This project is part of our internship task to build a machine learning model that classifies user queries into specific e-commerce intents. The system supports multiple languages (English, Hindi, and Spanish) and handles queries like order cancellation, address changes, and product requests.

## 📌 Objective

Automatically classify customer support sentences into one of the following e-commerce intents:

- `cancel_order`
- `confirm_order`
- `order_status`
- `change_address`
- `contact_advisor`
- `get_list_of_products`
- `general_query`
- `not_ecommerce`

## 🌍 Multilingual Support

Our dataset and model support:
- English 🇬🇧
- Hindi 🇮🇳
- Spanish 🇪🇸

We used **multilingual sentence embeddings** to ensure effective understanding across languages.

---

## 📁 Dataset

- Total samples: **30,000**
- Balanced across all 8 intent classes
- Balanced across 3 languages (10,000 English, 10,000 Hindi, 10,000 Spanish)
- Format:
  | text | intent | lang |
  |------|--------|------|
  | "Where is my order?" | order_status | en |
  | "मेरा ऑर्डर कहाँ है?" | order_status | hi |
  | "¿Dónde está mi pedido?" | order_status | es |

---

## 🧠 Models Trained

We trained and evaluated multiple models using **Stratified K-Fold Cross-Validation (5 folds)**:

| Model               | Avg Accuracy |
|---------------------|--------------|
| Logistic Regression | 0.81         |
| Linear SVM          | 0.84         |
| Random Forest       | 0.88         |
| MLP Classifier      | **0.89** ✅ |

✅ The **MLP (Neural Network)** achieved the best accuracy and was chosen as the final model.

---

## 🛠️ Tools & Libraries

- Python (Colab)
- Scikit-learn
- SentenceTransformers (`paraphrase-multilingual-MiniLM-L12-v2`)
- NLTK + stopwordsiso
- Matplotlib & Seaborn for visualizations

---

## 📊 Visualizations

We generated:
- **Accuracy comparison bar chart**
- **Confusion matrix** for best model
- **Heatmap of precision/recall/F1** for all classes


## 🔮 Inference

The model can take a user query in any supported language and return the predicted intent.

Example:

```python
predict_intent("मैं अपना ऑर्डर रद्द करना चाहता हूँ", lang='hi')
# Output: cancel_order
