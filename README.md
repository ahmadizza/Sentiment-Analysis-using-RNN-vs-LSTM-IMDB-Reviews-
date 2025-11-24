# Sentiment Analysis with RNN vs LSTM (IMDB Movie Reviews)

## Project Description

Sentiment analysis is a text classification task used to determine the polarity of a review (positive or negative).
This project compares the performance of a standard **Recurrent Neural Network (RNN)** and a **Long Short-Term Memory (LSTM)** network on the **50,000 IMDB movie reviews dataset**.

RNNs are designed for sequential data such as text, but they often struggle with long-term dependencies due to the vanishing gradient problem.
LSTMs, an improved variant of RNNs, address this limitation using a cell state and gating mechanisms.

---

## Objectives

* Compare the performance of RNN and LSTM in predicting sentiment on the IMDB movie reviews.
* Analyze the vanishing gradient phenomenon during model training.
* Evaluate how well each model handles long-term dependencies in text sequences.

---

## Dataset

* Source: IMDB Movie Reviews Dataset
* Total data: 50,000 labeled movie reviews (positive or negative)
* Data split:

  * 80% training (39,665 samples)
  * 10% validation (4,959 samples)
  * 10% testing (4,958 samples)
* Characteristics: long reviews, informal writing, HTML tags, inconsistent punctuation.

---

## Methodology

1. **Preprocessing**: lowercasing, removing HTML tags, punctuation, numbers, stopwords, followed by tokenization and padding (max length = 256).
2. **Sentiment Encoding**: 1 = positive, 0 = negative.
3. **Model Architecture**:

   * `nn.Embedding` to convert tokens into 64-dimensional vectors
   * `nn.RNN` or `nn.LSTM` as the core sequential layer (bidirectional)
   * `nn.Linear` + `nn.Sigmoid` for binary classification
   * Dropout: 0.2, Hidden Dimension: 32
4. **Evaluation Metrics**: accuracy, precision, recall, loss curves, and gradient analysis.

---

## Results

### Accuracy

* **RNN**: Training accuracy reached 94%, but validation accuracy remained below 82%, indicating overfitting.
* **LSTM**: Training accuracy reached 98%, while validation accuracy stabilized around 87%.

### Loss Behavior

* RNN: training loss decreased but overfitting occurred after epoch 8–9.
* LSTM: training loss decreased consistently, with slower overfitting (around epoch 13).

### Gradient Stability

* RNN: gradients were unstable, with clear signs of vanishing and exploding gradients.
* LSTM: gradients were more stable and consistent throughout training.

### Test Evaluation

* The LSTM model outperformed the RNN model across all evaluation metrics.
* LSTM performed significantly better on long reviews (over 400 words), maintaining contextual understanding more effectively.

---

## Insights and Conclusion

* The RNN model is prone to overfitting and struggles with long text sequences.
* The LSTM model is more robust, stable, and better at balancing precision and recall.
* LSTM successfully mitigates the vanishing gradient issue, making it more suitable for long-term dependency tasks.
* Overall, **LSTM is superior to RNN for sentiment analysis on the IMDB dataset**.


