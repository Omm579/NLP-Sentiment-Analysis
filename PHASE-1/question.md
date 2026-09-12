# Problem Statement and Research Plan

## 1. What problem am I solving?

I am addressing the problem of **automated sentiment analysis of user-generated text (reviews, comments, and posts)**. Existing sentiment analysis approaches can achieve high classification performance under controlled experimental conditions, but their effectiveness is limited by dataset dependency, domain shift, informal and colloquial text, implicit or mixed sentiment, class imbalance, feature selection, and reduced generalization to unseen or independently collected text.

The goal is to develop an **AI-powered NLP-based sentiment analysis system** that systematically extracts meaningful textual characteristics (lexical, dictionary-based, n-gram/TF-IDF, and contextual embedding features), compares a classical Naïve Bayes classifier with a transformer-based classifier (e.g., BERT/DistilBERT), evaluates them using multiple metrics, and investigates whether the resulting model generalizes beyond the dataset on which it was trained — helping users overcome the challenges associated with manual, dictionary-based, and single-domain sentiment classification approaches.

## 2. Why is this problem important?

This problem is important because **sentiment analysis is widely applied in public-opinion monitoring, business intelligence, e-commerce review analysis, and social media analytics**, where organizations need reliable automated understanding of user opinion.

Existing challenges can lead to:

- **Reduced accuracy** on informal text containing slang, emoticons, misspellings, sarcasm, or domain-specific vocabulary not present in standard lexicons
- **Misleading business decisions** caused by false positives and false negatives, which misrepresent user opinion
- **Poor transferability**, since models often learn dataset-specific vocabulary (e.g., movie reviews) rather than general sentiment patterns, and degrade on independent datasets or different domains (e.g., restaurant reviews evaluated on book or hotel reviews)
- **High computational and label cost**, since transformer models require substantially more training data and resources than classical models
- **Limited explainability**, making it hard for users and researchers to understand which words or features influence a prediction

Solving this problem can improve **classification accuracy, cross-domain generalization, interpretability, automation, and decision-making reliability**, and provide practical benefits to **businesses, researchers, e-commerce platforms, and social-media analysts** who need trustworthy sentiment assessments.

## 3. What has already been done?

Several existing approaches and systems have been developed to address this problem. These include:

- **Dictionary/lexicon-based methods** and rule-based polarity scoring, such as the hybrid SD-NB system for danmaku (bullet-screen) sentiment analysis, which combines a sentiment dictionary (DUT emotional vocabulary ontology of 27,476 words, 733 catchwords, 161 weighted emoticons) with a Naïve Bayes classifier using Laplace smoothing
- **Traditional machine-learning models** such as Naïve Bayes and SVM using n-gram/TF-IDF features
- **Deep learning models** including LSTM-based models and TextCNN
- **Transformer-based models** such as BERT, DeBERTa, RoBERTa, and flan-T5 fine-tuned for sentiment and aspect-based sentiment analysis (ABSA)
- **Zero-shot large language models** (GPT-3.5-Turbo, PaLM) driven by structured prompt engineering
- **Topic-model-driven sentiment pipelines** (LDA, NMF, BERTopic) combined with lexicon-based compound sentiment scoring for social media discourse analysis

Previous research has demonstrated that:

- Hybrid dictionary–machine-learning approaches achieve strong results on short, informal text — the danmaku SD-NB system reached **88.2% accuracy**, outperforming N-gram-NB (75.0%), N-gram-SVM (73.5%), and TextCNN (76.8%)
- Fine-tuned transformer models excel in their training domains (e.g., DeBERTa reached **93.1% on DOTSA/Hotels**)
- Zero-shot LLMs can deliver strong results without task-specific training (e.g., PaLM reached **93.5% on SemEval-16/Restaurant and 98.1% on YASO**), but fail sharply on implicit, multi-aspect data (only **48.8% ATSA / 55.8% ACSA on MAMS**, versus DeBERTa's 77.4–83.8%)
- Strong in-domain performance does not necessarily translate to cross-domain performance, motivating explicit cross-dataset validation

## 4. What are the limitations of existing approaches?

Despite their effectiveness, existing approaches have several limitations:

- **Dataset dependency** — models may learn vocabulary specific to one dataset (e.g., movie reviews) rather than general sentiment patterns
- **Poor generalization / domain shift** — performance decreases when models are evaluated on independent datasets or different domains (restaurant → book, clothing, or hotel reviews)
- **Difficulty with informal and colloquial text** — slang, abbreviations, emoticons, and misspellings are not covered by standard vocabularies
- **Implicit and mixed sentiment** — a single sentence may express contrasting opinions toward different aspects (e.g., "great camera but terrible battery"), which remains hard for lexicons, trained transformers, and even zero-shot LLMs
- **Manual lexicon maintenance does not scale** — catchword and emoticon dictionaries require manual upkeep as language evolves
- **Class imbalance** — public review datasets are often dominated by positive examples, which can bias training
- **Label cost versus performance trade-off** — fine-tuned transformers need substantial labeled data and compute, while cheap classical models sacrifice contextual accuracy
- **Limited explainability** — users need understandable reasons behind a positive/negative decision
- **Weak evaluation practice** — many studies report only within-dataset, often binary results; cross-dataset validation and fine-grained evaluation remain uncommon

Therefore, there is a need for an improved approach that can **learn robust, generalizable sentiment patterns from labeled positive/negative text, combine classical (Naïve Bayes with TF-IDF/dictionary features) and contextual (transformer-based) models, generalize to unseen and cross-domain text, and provide interpretable, probability-aware predictions — all within a reproducible experimental framework with a usable web interface**.

## 5. What exactly will my system do?

The proposed system will **accept a submitted text review or comment, validate and preprocess it, extract lexical, dictionary-based, n-gram/TF-IDF, and contextual embedding features, and classify its sentiment as positive or negative (with a configurable neutral/mixed category and five-level category mapping) using both a Naïve Bayes classifier and a fine-tuned transformer model**.

It will take **user-submitted text (reviews, comments, posts)** and process it using **text validation, normalization, tokenization, stop-word removal, TF-IDF/dictionary feature extraction, contextual embeddings, Naïve Bayes (Multinomial/Bernoulli with Laplace smoothing), transformer fine-tuning (BERT/DistilBERT/RoBERTa), and feature selection** to produce **a sentiment classification, a sentiment probability/confidence score, a configurable sentiment category, and feature-level (word-level) explanations, delivered through a web interface and REST API**.

### Main Objectives

- **Study existing sentiment analysis approaches** through selected research papers (hybrid dictionary–ML classification, deep networks vs. LLMs for ABSA, topic-model-driven sentiment analysis)
- **Identify important textual characteristics** (lexical, syntactic, semantic) that support sentiment classification, including sentiment dictionaries and catchwords for informal text
- **Prepare and preprocess** suitable positive and negative labeled text datasets (e.g., product or restaurant reviews, social media comments), handling duplicates, missing values, and class imbalance
- **Implement and compare multiple classification approaches**: a classical Naïve Bayes classifier (TF-IDF/dictionary features) and a transformer-based (e.g., BERT) classifier
- **Evaluate models** using accuracy, precision, recall, F1-score, specificity, false positive/negative rates, ROC-AUC, confusion matrices, and inference time
- **Investigate generalization** through cross-dataset and cross-domain evaluation on at least one independent dataset
- **Provide a usable interface** (web UI + REST API) through which users can submit text for analysis
- **Provide interpretable results** containing classification, probability/risk information, and influential word/feature information

The system will be designed to address the key limitations identified in existing approaches while providing **reliable, explainable, and generalizable sentiment analysis with measurable cross-domain performance**.

## 6. How will I evaluate whether my solution is better or useful?

The proposed system will be evaluated using appropriate **performance, efficiency, and usability metrics**, following the SRS evaluation requirements and motivated by the cross-dataset methodology of the comparative ABSA study.

The evaluation will include:

- **Accuracy / Precision / Recall / F1-score** – to measure prediction and classification performance, reported per class and per dataset
- **Specificity / False Positive Rate / False Negative Rate** – to assess how reliably the model handles both sentiment classes
- **ROC-AUC** – to measure ranking/discrimination performance
- **Confusion Matrices** – to visualize classification behavior for each model
- **Cross-Dataset / Cross-Domain Performance** – comparing within-dataset results against at least one independent dataset to quantify generalization degradation and feature stability across domains
- **Inference Time / Latency** – measuring operational prediction latency separately for the Naïve Bayes and transformer model families (CPU-based inference for classical models; GPU recommended but not mandatory for transformer fine-tuning)
- **Resource Usage** – comparing computational and memory requirements of classical versus transformer pipelines
- **Comparison with Existing Approaches** – benchmarking against the literature results (e.g., SD-NB's 88.2% accuracy; N-gram-NB, SVM, and TextCNN baselines) to determine measurable improvements
- **Error Analysis** – investigating representative false-positive and false-negative cases at the linguistic level (sarcasm, negation, mixed sentiment)
- **Explainability Check** – verifying that feature-importance explanations (per-class log-probability ratios for Naïve Bayes, attention/gradient-based attributions for transformers) are consistent with the model version and feature schema used
- **User Evaluation** – assessing the usability of the web interface and the practical usefulness of prediction, probability, category, and explanation displays where applicable

The solution will be considered successful if it demonstrates **measurable improvement over existing approaches** — particularly in cross-dataset generalization, balanced per-class performance, explainability, and practical latency — while satisfying the defined requirements for performance, efficiency, reliability, security, and usability.
