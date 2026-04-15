# ShuoWen: A Large-Scale Synthetic Dataset for Tongjiazi Extraction

## 1. Project Overview
[cite_start]This repository hosts **ShuoWen**, a large-scale synthetic dataset specifically designed for **Tongjiazi (phonetic loanword) extraction** in Classical Chinese[cite: 2, 4]. 

[cite_start]Tongjiazi is a pervasive linguistic phenomenon in ancient texts that creates significant ambiguity[cite: 29, 30]. [cite_start]Due to the extreme scarcity of human-annotated corpora, we propose a **Knowledge-injected Synthesis Framework** to bridge the data gap[cite: 4, 6]. [cite_start]ShuoWen contains over **128,000 samples**, covering **8,009 canonical Tongjiazi-original character pairs** derived from authoritative philological knowledge bases[cite: 4, 5].

## 2. Key Contributions & Methodology
[cite_start]The dataset is constructed using a multi-stage synthesis pipeline, featuring a complementary mechanism between context-driven and knowledge-driven generation[cite: 60, 166]:

### A. Automatic Anchor Selection & Migration (AAM)
[cite_start]To ensure **linguistic authenticity**, AAM migrates authoritative "Original-Tongjia" pairs into massive unannotated corpora[cite: 37, 38]. [cite_start]By leveraging authentic syntactic structures as "anchors," AAM provides high-quality samples where loanwords appear in natural historical contexts[cite: 133, 134].

### B. Knowledge-guided Triple Generation (KTG)
[cite_start]To achieve **full coverage of rare/long-tail data**, KTG bypasses the limitations of existing corpora[cite: 39, 78]. [cite_start]It provides LLMs with explicit philological knowledge and constraints, forcing the synthesis of samples for rare Tongjiazi pairs that seldom appear in common texts[cite: 65, 180]. [cite_start]This ensures the dataset covers all 8,009 canonical pairs[cite: 41].

### C. Hard Negative Mining (HNM) Strategy
[cite_start]To solve the **over-correction** problem, HNM purposefully generates "hard negatives"—cases where a character *could* be a Tongjiazi but is actually used in its original sense[cite: 6, 7]. [cite_start]This refines the model's semantic boundaries and reduces false positives[cite: 42, 66].

## 3. Innovations in Data Synthesis: Case Studies
[cite_start]The synergy between AAM and KTG ensures that ShuoWen is both linguistically natural and comprehensive[cite: 166].

| Module | Synthesis Logic | Case Example | Innovation |
| :--- | :--- | :--- | :--- |
| **AAM** | [cite_start]**Context-driven**: Migrating pairs into real ancient sentences[cite: 37]. | *Source*: "阳虎**归**孔子豚。" <br> *Synthetic*: "阳虎**馈**孔子豚。" | [cite_start]Preserves authentic syntax and grammatical patterns[cite: 38]. |
| **KTG** | [cite_start]**Knowledge-driven**: Synthesizing rare pairs via LLM constraints[cite: 65]. | *Knowledge*: {Target: "蚤", Original: "早", Reason: "Phonetic similarity"} <br> *Synthetic*: "四之日其**蚤**，献羔祭韭。" | [cite_start]Achieves 100% coverage of rare, long-tail Tongjiazi pairs[cite: 41, 164]. |
| **HNM** | [cite_start]**Adversarial Mining**: Creating samples for original usage[cite: 167]. | *Input*: "成子**说**，宰门闭。" <br> *Label*: **Original Usage** (Negative) | [cite_start]Prevents the model from blindly replacing characters[cite: 42, 92]. |

## 4. Dataset Structure
Based on the current repository, the data is organized as follows:

| Directory | Format | Description |
| :--- | :--- | :--- |
| `data/01_raw/` | `.jsonl` | [cite_start]The complete synthetic dataset with metadata[cite: 274]. |
| `data/02_ShuoWen/` | `JSON/BIO` | [cite_start]Task-specific formats: **JSON** for instruction tuning and **BIO** for sequence labeling[cite: 121, 122]. |

## 5. Technical Specifications
- [cite_start]**Total Samples**: 128,000+ [cite: 4, 59]
- [cite_start]**Coverage**: 8,009 unique Tongjia-Original pairs (Full Coverage)[cite: 5, 41].
- [cite_start]**Languages**: Classical Chinese (Source), Modern Chinese (Annotations)[cite: 105].
- **Core Features**:
    - [cite_start]Mitigation of **Metaphorical Semantic Shifts**[cite: 11].
    - [cite_start]Robustness against **Proper Noun Interference**[cite: 11].

## 6. Usage & Implementation
[cite_start]The dataset is ready-to-use for fine-tuning models like **BERT**, **RoBERTa**, or **LLMs** (e.g., Qwen, Llama)[cite: 67, 123].
- [cite_start]**For NER-style extraction**: Use the `BIO` formatted data in `02_ShuoWen`[cite: 121].
- [cite_start]**For semantic interpretation**: Use the `JSON` instruction-tuning data in `02_ShuoWen`[cite: 122].

## 7. Maintenance & Affiliation
- [cite_start]**Author**: Yichen Yu (于宜辰) [cite: 3, 532]
- [cite_start]**Affiliation**: College of Computer Science, Sichuan University (SCU) [cite: 17, 532]
- [cite_start]**Contact**: [yichenyu@stu.scu.edu.cn] [cite: 17]
