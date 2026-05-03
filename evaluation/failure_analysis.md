# Failure Analysis

## Overall Patterns

The strongest model was `gemini-flash-lite-latest` with the structured JSON prompt. It reached 63.3% exact-match accuracy, 73.3% sentiment accuracy, and 90.0% topic accuracy. The local Hugging Face model, `typeform/distilbert-base-uncased-mnli`, was much weaker overall, with its best exact-match accuracy at 23.3%.

The biggest pattern was that topic classification was easier than sentiment classification for Gemini. Gemini usually identified the correct product or brand, but it sometimes missed the emotional tone of the tweet. The Hugging Face model struggled more with topic labels because it was used as a zero-shot classifier and had to choose among similar brand/product labels.

## Sentiment Errors

The most common sentiment issue was confusing emotionally weak posts with neutral posts. For example, some positive posts about wanting an iPad or enjoying an app were labeled as neutral because the wording was indirect instead of clearly enthusiastic. Some negative posts were also labeled as neutral when the complaint was mild or sarcastic.

Examples of sentiment difficulty included:

- Example 1: A tweet saying someone was using an iPad 2 "like it's a trophy" was labeled neutral by Gemini, even though the ground truth was positive.
- Example 8: A tweet about wanting an iPad 2 because of "gadget lust" was labeled neutral, even though the ground truth was positive.
- Example 26: A tweet saying someone was late for getting an iPad and included `#sadpanda` was labeled negative by Gemini, while the ground truth was neutral.

These errors show that short social media posts can be hard to classify because sentiment is often implied through slang, hashtags, sarcasm, or context.

## Topic Errors

The most common topic errors happened between closely related labels. The models often confused:

- `iPad` with `iPad or iPhone App`
- `Google` with `Other Google product or service`
- `iPhone` with `iPad or iPhone App`

This makes sense because many tweets mention several related products in the same post. For example, a tweet about an iPhone app can include both the device and the app, which makes the main topic ambiguous. The topic label set is also fairly granular, so small differences between labels matter.

Gemini handled topics much better than Hugging Face. Gemini reached 90.0% topic accuracy across all three prompt strategies. The Hugging Face model's best topic accuracy was 43.3%, which suggests that the local zero-shot classifier was less reliable for fine-grained product labels.

## Format Errors

There were no final format errors in the saved results. Both models produced parseable outputs after the notebook was adjusted to batch Gemini calls and normalize Hugging Face classifier outputs into the same result format.

The structured JSON prompt had the strongest format control. It also produced the best overall result for Gemini. This supports the idea that requesting a strict schema is useful when a business process needs clean, machine-readable output.

## Recommended Improvement

If I continued this project, I would improve the test set and label design in two ways.

First, I would simplify some of the topic labels. Labels like `Google` and `Other Google product or service` are too close, and labels like `iPad` and `iPad or iPhone App` can overlap in real tweets. A clearer topic taxonomy would probably improve accuracy.

Second, I would add more examples of sarcasm, hashtags, and mixed sentiment. These were the hardest cases for the models. More examples would make the evaluation more realistic and would help identify when human review is needed.

Based on this evaluation, I would choose `gemini-flash-lite-latest` with the structured JSON prompt as the best model and prompting strategy for this task.
