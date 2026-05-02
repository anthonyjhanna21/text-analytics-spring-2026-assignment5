# Assignment 5: LM Evaluation Report

## Project Title and Option

Social Media Sentiment and Topic Classification  
Option C: LM Evaluation Report

## Name

Anthony Hanna

## Project Description

This project evaluates how well language models classify real social media posts by sentiment and brand/product topic. The source data is the Kaggle Brands and Product Emotions dataset, which contains tweets about brands and products with emotion labels.

## Setup Instructions

1. Install dependencies:

```bash
pip install -r requirements.txt
```

2. Add a `.env` file with a Google AI Studio key:

```text
GOOGLE_API_KEY=your_key_here
```

3. Open and run:

```text
notebooks/lm_evaluation.ipynb
```

4. In the notebook, set `RUN_API_CALLS = True` when ready to run the model experiments.

## Models and Tools Used

- Google Gemini free tier
- Kaggle Brands and Product Emotions dataset
- Python
- pandas
- kagglehub
- google-generativeai

## Paid vs. Free Path

This project is designed for the free path using Google AI Studio's free tier and Kaggle's free dataset access.

## Key Findings

To be completed after running the experiments.

## File Descriptions

- `data/raw/`: original downloaded Kaggle CSV
- `data/test_set.csv`: selected 30-example evaluation set
- `notebooks/lm_evaluation.ipynb`: main experiment notebook
- `prompts/prompt_templates.md`: prompt strategies
- `results/results_matrix.csv`: model and prompt comparison metrics
- `evaluation/failure_analysis.md`: qualitative error analysis
- `ai_log.md`: AI usage log
