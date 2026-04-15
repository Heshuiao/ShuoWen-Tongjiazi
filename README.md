# ShuoWen: A Large-Scale Synthetic Dataset for Tongjiazi Extraction

## 1. Project Overview
This repository hosts **ShuoWen**, a large-scale synthetic dataset specifically designed for **Tongjiazi (phonetic loanword) extraction** in Classical Chinese. 

Tongjiazi is a pervasive linguistic phenomenon in ancient texts that creates significant ambiguity. Due to the extreme scarcity of human-annotated corpora, we propose a **Knowledge-injected Synthesis Framework** to bridge the data gap. ShuoWen contains over **128,000 samples**, covering **8,009 canonical Tongjiazi-original character pairs** derived from authoritative philological knowledge bases.

## 2. Key Contributions & Methodology
The dataset is constructed using a multi-stage synthesis pipeline to ensure both linguistic authenticity and model robustness:

### A. Automatic Anchor Selection & Migration (AAM)
To solve the data sparsity issue, we utilize authoritative dictionaries (e.g., *Standard Dictionary of Tongjiazi*) to identify "Original-Tongjia" pairs. We then migrate these relationships into large-scale unannotated Classical Chinese corpora (such as *Siku Quanshu*) to generate massive candidate samples.

### B. Knowledge-guided Triple Generation (KTG)
To handle homograph ambiguity, we transform dictionary definitions into structured triples (Tongjiazi, Original Character, Context). This process infuses latent philological expertise into the dataset, helping models understand the phonological and semantic logic behind character substitutions.

### C. Hard Negative Mining (HNM) Strategy
A major challenge in Tongjiazi extraction is **over-correction** (mistakenly identifying an original character as a Tongjiazi). We introduce an HNM strategy that specifically generates "hard negatives"—cases where a character *could* be a Tongjiazi but is actually used in its original sense. This refines the model's semantic boundaries and significantly reduces false positives.

## 3. Dataset Structure
The repository is organized to support various NLP tasks, from sequence labeling to generative modeling:

| Directory | Format | Description |
| :--- | :--- | :--- |
| `data/01_raw/` | `.jsonl` | The complete synthetic dataset with metadata. |
| `data/02_processed/` | `JSON/BIO` | Task-specific formats: **JSON** for instruction tuning (LLMs) and **BIO** for sequence labeling (BERT-based models). |
| `data/03_integrated/` | Mixed | The final unified dataset including HNM samples for robust training. |

## 4. Technical Specifications
- **Total Samples**: 128,000+
- **Coverage**: 8,009 unique Tongjia-Original pairs.
- **Languages**: Classical Chinese (Source), Modern Chinese (Explanations/Annotations).
- **Core Features**:
    - Mitigation of **Metaphorical Semantic Shifts**: Distinguishing between loan usage and extended meanings.
    - Robustness against **Proper Noun Interference**: Ensuring names and titles are not misidentified as phonetic loans.

## 5. Usage & Implementation
The dataset is ready-to-use for fine-tuning models like **BERT**, **RoBERTa**, or **LLMs** (e.g., GPT-4, Llama) for ancient Chinese tasks. 
- **For NER-style extraction**: Use the `BIO` formatted data.
- **For semantic interpretation**: Use the `JSON` instruction-tuning data.

## 6. Maintenance & Affiliation
- **Author**: Yichen Yu (于宜辰)
- **Affiliation**: College of Computer Science, Sichuan University (SCU)
- **Contact**: [yichenyu@stu.scu.edu.cn]
