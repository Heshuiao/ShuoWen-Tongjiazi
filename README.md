# ShuoWen-Tongjiazi
Official implementation and dataset for "ShuoWen: A Knowledge-Driven Framework for Classical Chinese Phonetic Loan Extraction".
# ShuoWen Dataset Collection

## 1. Project Overview
This repository contains the dataset for the ShuoWen project, focusing on [请补充你的AI研究方向，例如：Chinese Etymology/NLP]. The collection integrates multiple data sources to support model training and evaluation.

## 2. Dataset Structure
The data is organized into four primary directories:

| Directory | Source/Method | Description |
| :--- | :--- | :--- |
| `data/AAM/` | Method 1 | Data generated or collected via AAM approach. |
| `data/KTG/` | Method 2 | Data generated or collected via KTG approach. |
| `data/HNM/` | HNM Source | Supplementary data from HNM sources. |
| `data/ShuoWen/` | Integrated | The complete, unified dataset (AAM + KTG + HNM). |

## 3. Data Specification
- **Format**: [例如：.json / .csv]
- **Encoding**: UTF-8
- **Status**: Pre-processed and ready for training.
- **Note**: The preprocessing scripts and training pipelines (Python) are currently private and will be released in future updates.

## 4. Usage
To use this dataset in your Python environment:
```python
# Example: Loading ShuoWen integrated data
import pandas as pd
import json

# Replace with actual file path
data_path = "data/ShuoWen/your_file_name.json"
# data = pd.read_csv(data_path)
