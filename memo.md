# Business Memo

To: Course Instructor  
From: Me  
Subject: LM Evaluation for Social Media Sentiment and Topic Classification  
Date: May 2, 2026

## Recommendation

I recommend using `gemini-flash-lite-latest` with the structured JSON prompting strategy for this social media classification task. This combination had the strongest overall performance, with 63.3% exact-match accuracy, 73.3% sentiment accuracy, and 90.0% topic accuracy across the 30-post test set.

## Summary of Evaluation

I evaluated two models on a social media sentiment and topic classification task using real tweets from the Brands and Product Emotions dataset. The task required each model to assign both a sentiment label (`positive`, `negative`, or `neutral`) and a topic label, such as `Apple`, `iPad`, `Google`, or `iPad or iPhone App`.

The two models were:

- `gemini-flash-lite-latest` through the Google Gemini API
- `typeform/distilbert-base-uncased-mnli` as a local Hugging Face Transformers model

I tested three prompt strategies for each model:

- zero-shot
- few-shot
- structured JSON

The best-performing model was Gemini. Its structured JSON prompt produced the highest exact-match accuracy. The Hugging Face model was useful as a free local fallback, but it was less accurate because it is a zero-shot classifier rather than a chat-style language model.

## Best Model and Prompt Strategy

The best combination was:

```text
Model: gemini-flash-lite-latest
Prompt strategy: structured_json
Sentiment accuracy: 73.3%
Topic accuracy: 90.0%
Exact-match accuracy: 63.3%
Format compliance: 100.0%
```

The structured JSON strategy worked best because it gave the model a clear output schema and a constrained set of labels. This reduced formatting problems and helped the model stay focused on the two required fields.

## Business Implications

For a business monitoring social media feedback, this evaluation suggests that a lightweight Gemini model can be a practical tool for classifying customer posts by sentiment and topic. The model was especially strong at identifying the business topic, which would help teams quickly see whether posts are about products, apps, services, or brand-level reactions.

However, the model still made sentiment mistakes on subtle or mixed tweets. Some posts that included sarcasm, indirect criticism, or mild excitement were classified incorrectly. Because of that, I would not use this system as a fully automated decision-maker. I would use it as a first-pass labeling tool, with human review for ambiguous or high-impact posts.

Overall, the best workflow is to use structured prompting with a strong API model for production-style analysis, while keeping a local Hugging Face model as a free backup or baseline comparison.

## Cost and Performance Tradeoff

This project used the free path, so there was no paid API cost in the experiment. Gemini used the Google AI Studio free tier, and the Hugging Face model was run locally through Transformers.

| Model | Best Strategy | Exact-Match Accuracy | Cost Used |
|---|---:|---:|---:|
| `gemini-flash-lite-latest` | structured JSON | 63.3% | $0.00 |
| `typeform/distilbert-base-uncased-mnli` | zero-shot | 23.3% | $0.00 |

Because both options were free in this setup, the higher-performing Gemini model was worth using. The Hugging Face model still had value as a no-cost local baseline, but it was not accurate enough to be my recommended production choice.
