# **NLP Assignment 1: Distributional Word Vectors**

## **Overview**

This project implements various methods for constructing word vectors from a corpus and evaluates them based on their performance on word similarity datasets. The project focuses on using distributional word vectors to capture word meanings and their contexts, and employs techniques like **raw counts**, **Inverse Document Frequency (IDF)**, and **Pointwise Mutual Information (PMI)** to build word vectors. The assignment is split into multiple parts, and each part focuses on a specific task.

The project uses a sample of the English Wikipedia corpus and evaluates the word vectors against two datasets:
1. **MEN**: A word similarity dataset based on human-annotated word pairs.
2. **SimLex-999**: A word similarity dataset focused on capturing functional similarity between words.

## **Structure**

The project is structured into the following parts:

1. **1. Distributional Counting**:
    - Counts word co-occurrences in a corpus with varying window sizes and generates word vectors.
    - Evaluates the word vectors using cosine similarity and Spearman’s rank correlation.

2. **2. Combining Counts with IDF**:
    - Adjusts the word vectors using **Inverse Document Frequency (IDF)** to reduce the influence of common words.
    - Evaluates the performance of IDF-weighted word vectors.

3. **3. Pointwise Mutual Information (PMI)**:
    - Computes **PMI** for word pairs to create word vectors that emphasize meaningful co-occurrences.
    - Evaluates the performance of PMI-based word vectors.

4. **4. Quantitative Comparisons**:
    - Compares word vectors generated using raw counts, IDF, and PMI, across different window sizes.
    - Analyzes the trends in performance based on window size and method.

5. **5. Qualitative Analysis**:
    - Performs qualitative analysis by examining nearest neighbors for selected words.
    - Focuses on multisense words (words with multiple meanings) and analyzes how their nearest neighbors vary with window size.

## **Requirements**

This project requires Python 3.8+ with the following packages:
- `numpy`
- `pandas`
- `scipy`

Install the required packages using:
```bash
pip install numpy pandas scipy
```

## **Running the Project**

To run the project, follow these steps:

1. **Data Preparation**:
   - Ensure you have the following files in your project directory:
     - `wiki-1percent.txt`: Corpus from Wikipedia (preprocessed).
     - `men.txt`: MEN word similarity dataset.
     - `simlex-999.txt`: SimLex-999 word similarity dataset.
     - `vocab-5k.txt`: A file containing the 5,000 most common words in Wikipedia.
     - `vocab-15kws.txt`: A file containing 15,000 words, including those from the similarity datasets.

2. **Running Parts**:
   - Each part of the assignment can be run separately, depending on which task you want to evaluate.

   **Example**:
   - For Part 1 (Distributional Counting), run:
     ```python
     python part1_distributional_counting.py
     ```

   - For Part 2 (IDF weighting), run:
     ```python
     python part2_idf_weighting.py
     ```

   - For Part 3 (PMI-based word vectors), run:
     ```python
     python part3_pmi.py
     ```

   - For Part 4 (Quantitative Comparisons), run:
     ```python
     python part4_quantitative_comparisons.py
     ```

   - For Part 5 (Qualitative Analysis), run:
     ```python
     python part5_qualitative_analysis.py
     ```

## **Key Functions**

- **`count_word_pairs()`**:
  - Counts word co-occurrences in a corpus with a specified window size.
  - Input: Corpus file, vocabularies, window size.
  - Output: Sparse word pair counts.

- **`calculate_idf_weighted_vectors()`**:
  - Computes IDF-weighted word vectors using raw counts.
  - Input: Word pair counts, total sentences, vocabularies.
  - Output: IDF-weighted word vectors.

- **`calculate_pmi()`**:
  - Computes Pointwise Mutual Information (PMI) for word pairs.
  - Input: Word pair counts, vocabularies.
  - Output: PMI-based word vectors.

- **`evaluate_word_vectors()`**:
  - Evaluates the word vectors against human-labeled similarity datasets (MEN and SimLex-999).
  - Input: Similarity dataset, word vectors.
  - Output: Spearman's rank correlation.

- **`get_nearest_neighbors()`**:
  - Computes the nearest neighbors for a word based on cosine similarity.
  - Input: Word vectors, target word, vocabulary.
  - Output: List of nearest neighbors.

## **Results**

The word vectors are evaluated based on the Spearman’s rank correlation between the word similarities produced by the vectors and the human-annotated similarities in the MEN and SimLex-999 datasets.

**PMI**-based word vectors tend to perform best overall, especially with larger window sizes, as they capture more meaningful word co-occurrences. Smaller window sizes perform well for functional similarity (SimLex-999), while larger windows perform better for associative similarity (MEN).

## **License**
This project is for educational purposes as part of the Natural Language Processing course assignment. No external licensing applies.
