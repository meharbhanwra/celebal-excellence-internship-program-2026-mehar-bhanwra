# 📘 Text Generation using RNN, LSTM, and GRU

### Understanding Sequence Modeling and Language Generation with Recurrent Neural Networks

This project features a hands-on Jupyter Notebook (`week5_Mehar_Bhanwra.ipynb`) focused on building and comparing recurrent neural network architectures for Natural Language Processing (NLP). The notebook serves as a practical introduction to sequence modeling, text generation, and the mathematical foundations behind modern language models.

Students and beginners will learn how different recurrent architectures process sequential data and how architectural improvements such as LSTM and GRU overcome the limitations of traditional RNNs.

---

# 🎯 Learning Goals

* Understand the complete NLP workflow from text preprocessing to language generation.
* Learn how text is converted into numerical sequences using tokenization and vocabulary mapping.
* Understand the limitations of Vanilla RNNs in learning long-term dependencies.
* Explore how LSTM and GRU architectures address the vanishing gradient problem.
* Compare different recurrent architectures using loss and accuracy metrics.
* Generate coherent text by predicting words sequentially from a learned language model.
* Analyze the mathematical foundations behind recurrent neural networks and gating mechanisms.

---

# 📦 Dataset & Text Preprocessing

The notebook uses a text corpus that is transformed into training sequences for next-word prediction.

### Preprocessing Pipeline

* Text cleaning and normalization
* Tokenization using Keras Tokenizer
* Vocabulary construction
* N-gram sequence generation
* Sequence padding for uniform input lengths
* Input-output sequence creation
* One-hot encoding of target words

Example:

Input Sequence:

I love deep learning

Generated Training Samples:

* I → love
* I love → deep
* I love deep → learning

This process converts raw text into supervised learning examples suitable for sequence prediction.

---

# 🚀 Project Workflow & Notebook Highlights

## 1. Tokenization & Sequence Generation

Transforms raw textual data into integer representations.

* Builds vocabulary dictionaries
* Creates word-to-index mappings
* Generates n-gram training sequences
* Pads sequences to a fixed length

This step prepares the corpus for neural network training.

---

## 2. Vanilla RNN Language Model

Implements a basic Recurrent Neural Network architecture.

### Characteristics

* Maintains a hidden state across timesteps
* Learns short-term sequential patterns
* Lightweight and computationally efficient

### Limitation

The model struggles to retain information over long sequences due to the vanishing gradient problem.

---

## 3. LSTM Language Model

Implements Long Short-Term Memory networks.

### Key Components

* Forget Gate
* Input Gate
* Output Gate
* Cell State

### Advantages

* Retains information across long sequences
* Handles long-term dependencies effectively
* Reduces information loss during backpropagation

LSTMs significantly improve language modeling performance compared to traditional RNNs.

---

## 4. GRU Language Model

Implements Gated Recurrent Units.

### Key Components

* Update Gate
* Reset Gate

### Advantages

* Fewer parameters than LSTM
* Faster training
* Competitive predictive performance

GRUs provide a balance between computational efficiency and learning capability.

---

## 5. Hyperparameter Tuning Experiments

Additional model variants were created to study the impact of architectural changes.

### Parameters Explored

* Embedding dimensions
* Hidden layer units
* Training epochs

The tuned models were compared against their baseline counterparts to observe performance improvements and convergence behavior.

---

## 6. Text Generation

Each trained model is used to generate text from a user-provided seed phrase.

Generation process:

1. Input seed text
2. Convert text into token sequences
3. Predict the most probable next word
4. Append prediction to sequence
5. Repeat iteratively

This demonstrates how language models learn contextual word relationships from training data.

---

# 📊 Summary of Results

| Architecture  | Final Loss | Final Accuracy | Training Time (s) | Parameters |
| ------------- | ---------- | -------------- | ----------------- | ---------- |
| RNN           | 0.2564     | 100.0%         | 11.57             | 16,878     |
| Modified RNN  | 0.0080     | 100.0%         | 23.93             | 45,934     |
| LSTM          | 1.6960     | 65.79%         | 17.20             | 35,502     |
| Modified LSTM | 0.1741     | 100.0%         | 57.78             | 120,046    |
| GRU           | 0.4106     | 99.34%         | 20.51             | 29,486     |
| Modified GRU  | 0.0111     | 100.0%         | 54.94             | 95,726     |

## Key Observations

### Vanilla Models

* The baseline RNN achieved perfect training accuracy while maintaining the lowest parameter count and fastest training time among all architectures.
* The baseline LSTM showed the weakest performance, achieving only 65.79% accuracy and the highest loss among the three base models.
* The baseline GRU significantly outperformed the baseline LSTM, achieving 99.34% accuracy while requiring fewer parameters and less computational overhead.

### Hyperparameter-Tuned Models

* All modified architectures achieved 100% training accuracy, indicating substantially improved learning capacity.
* Modified RNN achieved the lowest loss value (0.0080), demonstrating excellent fit to the training data while remaining computationally efficient.
* Modified GRU achieved comparable performance with a loss of 0.0111 and fewer parameters than the modified LSTM.
* Modified LSTM required the largest model size (120,046 parameters) and the longest training time (57.78 seconds) to achieve perfect accuracy.

### Computational Efficiency

* The RNN architecture remained the fastest model to train across both baseline and modified versions.
* GRU provided an effective balance between accuracy, parameter efficiency, and training speed.
* LSTM delivered strong performance after tuning but at the cost of substantially increased computational complexity.

### Overall Conclusion

The experimental results demonstrate that increasing model capacity through hyperparameter tuning significantly improves text-generation performance across all recurrent architectures. While all modified models achieved perfect training accuracy, the GRU architecture offered the best trade-off between performance and computational efficiency, whereas the LSTM achieved similar results with a considerably larger parameter count and longer training time.


---

# 🧠 Mathematical Concepts Covered

### Vanilla RNN

Hidden State Update:

hₜ = tanh(Wₓh xₜ + Wₕh hₜ₋₁ + b)

---

### LSTM

Uses gated memory mechanisms:

* Forget Gate
* Input Gate
* Cell State Update
* Output Gate

These gates regulate information flow and preserve long-term context.

---

### GRU

Uses:

* Update Gate
* Reset Gate

The architecture simplifies memory management while maintaining strong sequence-learning performance.

---

# 🛠️ Technologies Used

* Python
* NumPy
* Pandas
* TensorFlow / Keras
* Matplotlib
* Jupyter Notebook

---

# 🛠️ Prerequisites & Installation

To run this notebook locally, ensure you have Python 3 installed along with the required machine learning libraries.

Clone the repository:

```bash
git clone https://github.com/meharbhanwra/celebal-excellence-internship-program-2026-mehar-bhanwra.git
cd celebal-excellence-internship-program-2026-mehar-bhanwra/week-5
```

Install dependencies:

```bash
pip install tensorflow keras numpy pandas matplotlib jupyter
```

Launch Jupyter Notebook:

```bash
jupyter notebook week5_Mehar_Bhanwra.ipynb
```

---

# ✅ Conclusion

This project demonstrates the evolution of recurrent neural network architectures for sequence modeling and text generation. Through the implementation and comparison of Vanilla RNNs, LSTMs, and GRUs, the notebook highlights how gating mechanisms improve memory retention, learning stability, and language generation quality. The results illustrate why modern NLP systems rely heavily on advanced recurrent architectures for handling sequential data effectively.
