# Hierarchical vs. Flat Truncation Summarization for Long-Form Fiction

This repository contains the code and report for a project comparing two
strategies for summarizing text chapters that exceed a summarization model's
input limit: **flat truncation** (summarize only the first 1024 tokens) versus
**hierarchical** chunk-then-combine summarization (split into chunks, summarize
each, then summarize the combined summaries). Both are evaluated on chapters
from the BookSum corpus using `facebook/bart-large-cnn` without fine-tuning.

**Full report:** `reportfinal.pdf` (in the repo root).

## Repository structure

```
.
├── README.md                  
├── requirements.txt
├── reportfinal.pdf
├── references.bib
├── nlp_summarizer_projectfinal2.ipynb    ← the experiment notebook
├── summarization_results.csv   
└── summarization_results40chap.csv      
```

## Setup

Requires Python 3.10+ and a CUDA-capable GPU (the experiment was run on an
RTX 3050, 8GB VRAM). CPU will work but you have to wait a night.

```bash
pip install -r requirements.txt
# Install a CUDA build of PyTorch matching your driver, e.g.:
pip install torch --index-url https://download.pytorch.org/whl/cu121
```

## Running

Open `nlp_summarizer_project.ipynb` and run all cells top to bottom.
The first run downloads the BART model (~1.6GB) and the dataset, so an internet
connection is needed on first execution.

> **Note.** `N_CHAPTERS` in the data cell controls the sample size (set to 40 but you can change to 8 to get result of the mini version).
Requires `acl.sty` and `acl_natbib.bst` (ACL style files) in the same folder.
