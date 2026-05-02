# Assignment 5 Submission Checklist

## Repository Structure

- [x] `README.md`
- [x] `memo.md`
- [x] `requirements.txt`
- [x] `ai_log.md`
- [x] `.gitignore`
- [x] `data/test_set.csv`
- [x] `data/raw/`
- [x] `notebooks/lm_evaluation.ipynb`
- [x] `prompts/prompt_templates.md`
- [x] `results/`
- [x] `evaluation/failure_analysis.md`

## Option C Requirements

- [x] Business-relevant NLP task defined in notebook
- [x] Real social media dataset downloaded
- [x] 30-example test set created
- [x] Ground truth columns included: sentiment and topic
- [x] Three prompt strategies documented
- [x] Notebook cells have saved outputs for setup, dataset loading, test set creation, and prompt generation
- [x] Notebook configured for at least two models: Google Gemini and Hugging Face local zero-shot classifier
- [x] Add `GOOGLE_API_KEY` to `.env`
- [x] Add `HF_TOKEN` to `.env`
- [x] Set `RUN_API_CALLS = True`
- [x] Run full model experiments
- [x] Save `results/raw_model_outputs.csv`
- [x] Save `results/results_matrix.csv`
- [ ] Complete `evaluation/failure_analysis.md`
- [ ] Complete `memo.md`
- [ ] Add at least 8 AI log entries

## Important

Do not commit `.env` or API keys.
