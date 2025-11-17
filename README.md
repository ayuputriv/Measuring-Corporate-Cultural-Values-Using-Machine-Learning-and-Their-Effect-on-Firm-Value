## Measuring Corporate Cultural Values Using Machine Learning and Their Impact on Firm Value

### **An empirical study using NLP, FastText embeddings, and panel regression (522 annual reports, IDX 2017–2019)**

**Author:** *Ayu Putri Vidiantiwi*
**Affiliation:** BINUS University

---

## **Abstract**

This project investigates how corporate cultural values—innovation, integrity, quality, respect, and teamwork—relate to firm value among companies listed on the Indonesia Stock Exchange (IDX). Using **natural language processing (NLP)** and **machine learning**, the study constructs a *culture dictionary* based on FastText word embeddings to extract culture-related signals from **522 annual reports (2017–2019)**. Culture scores derived from text analysis are then tested using **panel data regression** to evaluate their effect on firm value, proxied by the **market-to-book ratio**.

The cultural signals are then evaluated for their relationship with **firm value (market-to-book ratio)** using **panel regression models**. Findings indicate that **quality** is the only cultural dimension significantly associated with higher firm value in Indonesian listed companies, while other cultural attributes show no measurable effect.

This project includes:

* Large-scale **NLP preprocessing** (522 PDF annual reports)
* **FastText embedding similarity** for dictionary expansion
* Machine learning–based **text scoring pipeline**
* **Data engineering** (cleaning, tokenization, stopword removal, n-grams)
* **Econometric modeling** using STATA (fixed/random effects)

The empirical findings show that *quality* is the only cultural value significantly associated with higher firm value, while innovation, integrity, respect, and teamwork show no observable effect.


---

## **Introduction**

Corporate culture influences performance through motivation, coordination, alignment, and trust-building inside organizations. Traditional measures of culture rely on interviews or surveys, which are difficult to scale. This study applies **machine learning-based text analysis** to extract cultural signals directly from companies’ annual reports.

The research replicates and extends Li et al. (2020) by applying their methodology to the Indonesian market and updating the dictionary creation process using **FastText embeddings**.

---

## **Research Objectives**

* Build a **machine learning dictionary** to quantify corporate cultural values from text.
* Analyze how each cultural dimension relates to **firm value**.
* Provide insights into whether cultural signals (non-financial information) are associated with company valuation.

---

## **Methodology**

### **Dataset**

* **522 Annual Reports** from IDX (2017–2019)
* Industries: multiple sectors
* Text language: English (majority) + Indonesian

---

### **NLP Pipeline Overview**

The culture-scoring process consists of six major stages (detail in Working Paper):


#### **Data Cleaning**

* Removing punctuation
* Lowercasing
* PDF → text extraction
* Removing extra whitespace & noise

#### **Pre-Processing**

* Tokenization (NLTK)
* Stopword removal (ID + EN)
* n-grams generation (unigram, bigram, trigram)

#### **Word Representation**

* Using **FastText pretrained embeddings** (300-dim vectors)
* Convert all tokens → vector space
* Capture semantic similarity between words

  * Example: *“enable” ≈ “allow”*
  * *“innovation” ≈ “creativity”*

#### **Cultural Dictionary Construction**

Seed words were chosen for each value:

| Value      | Example Seed Words                  |
| ---------- | ----------------------------------- |
| Innovation | innovate, creativity, develop       |
| Integrity  | ethics, accountability, comply      |
| Quality    | customer, excellence, high-quality  |
| Respect    | communication, collaboration, trust |
| Teamwork   | team, partnership, coordination     |

FastText similarity threshold: **0.75**
→ words with ≥75% cosine similarity included in dictionary.
See Word List samples in working paper. 

#### **Similarity Application**

* Compute similarity between all tokens and seed word embeddings
* Filter tokens by threshold
* Count frequency of matched cultural terms per company

#### **Culture Score Generation**

* Sum of matched word counts = score for each cultural value
* Output: 5 scores per company per year
* Exported to CSV for regression

---

## **Econometric Analysis**

### **Dependent Variable**

**Market-to-Book (MTB)** = market value / book value

### **Independent Variables**

Machine learning–derived culture scores:

* Innovation
* Integrity
* Quality
* Respect
* Teamwork

### **Control Variables**

* Firm Age
* Firm Size
* ROA
* Cash to Assets
* PPE to Assets
* Intangible Assets to Assets
  (all detailed in working paper) 

### **Model**

A fixed-effects / random-effects panel regression:

```
MTB_it = β0 + β1*Innovation_it + β2*Integrity_it + β3*Quality_it
         + β4*Respect_it + β5*Teamwork_it + Controls_it + ε_it
```

Software used: **STATA**.

---

## **Key Findings**

Based on regression output:

* **Quality** → **positive and significant** effect on firm value
* Innovation → not significant
* Integrity → not significant
* Respect → not significant
* Teamwork → not significant

Interpretation:
Only **quality-related language** in corporate reports appears to be valued by investors in the Indonesian market—possibly because it signals operational reliability, customer focus, and strong product/service execution.


---

## **Project Contributions**

This research demonstrates:

### **Technical Contributions**

* Machine learning approach to cultural measurement
* Dictionary creation via FastText embedding similarity
* NLP preprocessing pipeline for large PDF corpora
* Automated extraction of culture signals from annual reports

### **Economic/Research Contributions**

* Evidence on which cultural dimensions matter for firm valuation in emerging markets
* Analysis of non-financial disclosures as market signals
* Replication and expansion of global literature in an Indonesian context

---

## **Tools Used**

* **Python** (Google Colab)

  * pandas, numpy
  * NLTK
  * FastText
  * pdfminer / PyPDF2
* **STATA** for regression
* **Google Drive** integration for large PDFs


---

## 👩🏻‍💻 About Me

**Ayu Putri Vidiantiwi**  
* 📚 M.S. in Applied Analytics, Columbia University  
* 📊 Passionate about finance, business, data storytelling, and analytics
* 🌐 LinkedIn - https://www.linkedin.com/in/ayuputriv/
* 📧 ayu.vidiantiwi@columbia.edu

---
