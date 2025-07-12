# Extractive-Summarization-via-KL-Divergence-Minimization
This project implements extractive summarization using the KL-Sum method, specifically by building summaries based on word frequency distributions (words_PD) from the source document, and evaluates the generated summaries against human gold summaries on the DUC dataset using ROUGE metrics.

# Problem Statement
<img width="1903" height="171" alt="image" src="https://github.com/user-attachments/assets/35ae1046-e868-4d97-97ff-25ad42208487" />


# Solution Summary
- Implemented **extractive summarization** using the **KL-Sum method** on the **DUC dataset**.

- **Data Preparation**:
  - Loaded `dataset.pkl`:
    - Extracted **introductions** as source documents.
    - Extracted **abstracts** as human-authored gold summaries.
  - Analyzed abstracts:
    - Mean length ≈ 100 words.
    - Removed zero-length abstracts to ensure data integrity.

- **Preprocessing Pipeline**:
  - Cleaned text (removed non-alphanumeric characters, newlines).
  - Lowercased, tokenized.
  - Removed English stopwords.
  - Lemmatized using **WordNetLemmatizer**.
  - Retained words with valid **nltk.corpus.wordnet.synsets**.

- **KL-Sum Algorithm**:
  - Computed document word probability distribution (**words_PD**) with `collections.Counter`.
  - Iteratively built summary:
    - For each candidate sentence:
      - Calculated sentence+summary probability distribution (**PS**).
      - Selected sentence minimizing **KL-divergence** between PD and PS.
    - Continued until summary ≈ 100 words.

- **Evaluation**:
  - Assessed generated summaries vs. gold summaries using **ROUGE Perl package**.
  - Reported F-scores:
    - ROUGE-1 → **0.287**
    - ROUGE-2 → **0.113**
    - ROUGE-L → **0.250**

- **Key Insights**:
  - KL-Sum with words_PD offers a **quantitative benchmark** on DUC for alignment with human summaries.
  - Project structure hints at future comparison with **LDA-based topic distributions (topics_PD)** to explore alternative distributional models.

- **Conclusion**:
  - Demonstrated effectiveness of KL-Sum in extractive summarization.
  - Set foundation for comparative studies on different distributional approaches.
