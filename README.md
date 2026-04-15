# ShuoWen: A Large-Scale Synthetic Dataset for Tongjiazi Extraction

## 1. Project Overview
This repository hosts **ShuoWen**, a large-scale synthetic dataset specifically designed for **Tongjiazi (phonetic loanword) extraction** in Classical Chinese. 

Tongjiazi is a pervasive linguistic phenomenon in ancient texts that creates significant ambiguity. Due to the extreme scarcity of human-annotated corpora, we propose a **Knowledge-injected Synthesis Framework** to bridge the data gap. ShuoWen contains over **128,000 samples**, covering **8,009 canonical Tongjiazi-original character pairs** derived from authoritative philological knowledge bases.

## 2. Key Contributions & Methodology
The dataset is constructed using a multi-stage synthesis pipeline, featuring a complementary mechanism between context-driven and knowledge-driven generation:

### A. Automatic Anchor Selection & Migration (AAM)
To ensure **linguistic authenticity**, AAM migrates authoritative "Original-Tongjia" pairs into massive unannotated corpora. By leveraging authentic syntactic structures as "anchors," AAM provides high-quality samples where loanwords appear in natural historical contexts.

### B. Knowledge-guided Triple Generation (KTG)
To achieve **full coverage of rare/long-tail data**, KTG bypasses the limitations of existing corpora. It provides LLMs with explicit philological knowledge and constraints, forcing the synthesis of samples for rare Tongjiazi pairs that seldom appear in common texts. This ensures the dataset covers all 8,009 canonical pairs.

### C. Hard Negative Mining (HNM) Strategy
To solve the **over-correction** problem, HNM purposefully generates "hard negatives"—cases where a character *could* be a Tongjiazi but is actually used in its original sense. This refines the model's semantic boundaries and reduces false positives.

## 3. Innovations in Data Synthesis: Case Studies
The synergy between AAM and KTG ensures that ShuoWen is both linguistically natural and comprehensive.

| Module | Synthesis Logic | Case Example | Innovation |
| :--- | :--- | :--- | :--- |
| **AAM** | **Context-driven**: Migrating pairs into real ancient sentences. | *Source*: "阳虎**归**孔子豚。" <br> *Synthetic*: "阳虎**馈**孔子豚。" | Preserves authentic syntax and grammatical patterns. |
| **KTG** | **Knowledge-driven**: Synthesizing rare pairs via LLM constraints. | *Knowledge*: {Target: "蚤", Original: "早", Reason: "Phonetic similarity"} <br> *Synthetic*: "四之日其**蚤**，献羔祭韭。" | Achieves 100% coverage of rare, long-tail Tongjiazi pairs. |
| **HNM** | **Adversarial Mining**: Creating samples for original usage. | *Input*: "成子**说**，宰门闭。" <br> *Label*: **Original Usage** (Negative) | Prevents the model from blindly replacing characters. |

## 4. Dataset Structure
Based on the current repository, the data is organized as follows:

| Directory | Format | Description |
| :--- | :--- | :--- |
| `data/01_raw/` | `.jsonl` | The complete synthetic dataset with metadata. |
| `data/02_ShuoWen/` | `JSON/BIO` | Task-specific formats: **JSON** for instruction tuning and **BIO** for sequence labeling. |

## 5. Technical Specifications
- **Total Samples**: 128,000+
- **Coverage**: 8,009 unique Tongjia-Original pairs (Full Coverage).
- **Languages**: Classical Chinese (Source), Modern Chinese (Annotations).
- **Core Features**:
    - Mitigation of **Metaphorical Semantic Shifts**.
    - Robustness against **Proper Noun Interference**.

## 6. Usage & Implementation
The dataset is ready-to-use for fine-tuning models like **BERT**, **RoBERTa**, or **LLMs** (e.g., Qwen, Llama).
- **For NER-style extraction**: Use the `BIO` formatted data in `02_ShuoWen`.
- **For semantic interpretation**: Use the `JSON` instruction-tuning data in `02_ShuoWen`.

## 7. Maintenance & Affiliation
- **Author**: Yichen Yu (于宜辰)
- **Affiliation**: College of Computer Science, Sichuan University (SCU)
- **Contact**: [yichenyu@stu.scu.edu.cn]
