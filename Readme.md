# molGPT: Conditional Molecular Generation with Transformers

**molGPT** is an end-to-end pipeline for generating novel drug-like molecules using a transformer-based language model (GPT-style). This project focuses on conditional SMILES generation, where molecular properties such as LogP, QED, TPSA, and scaffold are used to guide the generation process. It's an integration of natural language processing and computational drug discovery.

---

## Project Highlights

- Trains a decoder-only transformer model (GPT) to generate valid SMILES strings
- Conditions the generation on molecular properties:
  - LogP (lipophilicity)
  - QED (quantitative estimate of drug-likeness)
  - TPSA (topological polar surface area)
  - Scaffold (molecular backbone)
- Includes evaluation metrics:
  - SMILES validity
  - Molecular uniqueness
  - Structural novelty (Tanimoto similarity)
  - Alignment with conditional property distributions

---

## Dataset

The project uses the [MOSES](https://github.com/molecularsets/moses) dataset — a curated collection of drug-like molecules designed for benchmarking molecular generative models.

---

## Installation

Install the required dependencies in your environment:

```bash
%pip install pandas rdkit transformers[torch] accelerate>=0.26.0
%pip install scikit-learn matplotlib tqdm pathos
%pip install torch --index-url https://download.pytorch.org/whl/cu118
%pip install git+https://github.com/molecularsets/moses.git
```

---

## Model Overview

The model is a fine-tuned GPT2 from HuggingFace's `transformers` library. It is trained on SMILES strings that are conditionally formatted with molecular properties.

Example input format:

```
<LOGP=2.5> <QED=0.9> <TPSA=45> C1=CC=CC=C1
```

---

## Evaluation Metrics

- Validity: Can the SMILES string be parsed as a valid molecule?
- Uniqueness: Are the generated molecules distinct?
- Novelty: Are the generated molecules different from those in the training set?
- Property Alignment: Do the generated molecules reflect the specified properties?

