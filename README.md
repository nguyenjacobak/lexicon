# Construction of Sentiment Lexicon and Lexicon-Based Sentiment Scoring

This project focuses on the construction of a comprehensive Vietnamese sentiment lexicon and its application in scoring sentiment for the **VSA - Food Reviews** dataset. The approach involves leveraging an existing baseline lexicon and significantly expanding it using Large Language Models (LLMs).

## 1. Baseline: The Original Lexicon (VietSentiWordNet)
Initially, the system utilized the **VietSentiWordNet** dataset (`VietSentiWordnet_Ver1.3.5.txt`).

* **Scale:** Approximately 1,000 words.
* **Structure:** Each word contains a `PosScore` (Positive Score) and a `NegScore` (Negative Score).
* **Polarity Calculation:**
    $$Polarity = PosScore - NegScore$$
* **Limitation:** Due to the limited vocabulary size, the coverage was insufficient for diverse user reviews.

---

## 2. Building the Extended Lexicon (New Approach)
To overcome the limitations of the baseline, we constructed a new, extended sentiment lexicon containing **20,500 words**.

### Methodology
The expansion process combines web scraping with the semantic understanding capabilities of Large Language Models (specifically Gemini).

### Construction Pipeline
1.  **Word Collection:** Gathered a corpus of 20,500 Vietnamese words (Nouns, Verbs, Adjectives).
2.  **Definition Extraction:** Scraped definitions for each word from online dictionaries to provide context.
3.  **LLM Scoring (Gemini):**
    * Input: `Word` + `Definition`.
    * Model: Gemini.
    * Task: Analyze the sentiment and assign a score in the range $[-1, 1]$.
4.  **Storage:** The result is saved as a structured dictionary containing `{word, definition, score}`.

### Construction Flowchart
```mermaid
graph TD;
    A[Collect 20,500 Words] --> B[Scrape Definitions from Dictionary Web];
    B --> C[Input Word + Definition to LLM Gemini];
    C --> D[Receive Sentiment Score -1 to 1];
    D --> E[Save to New Lexicon Dataset];
    E --> F[Ready for Sentiment Pipeline];
