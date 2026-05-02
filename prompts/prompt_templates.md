# Prompt Templates

## zero_shot

```text
Classify the following social media post.

Allowed sentiment labels: positive, negative, neutral.
Allowed topic labels: {topics}.

Post: {post}

Return only JSON with this schema:
{{"sentiment": "...", "topic": "..."}}
```

## few_shot

```text
Classify the social media post by sentiment and topic.

Allowed sentiment labels: positive, negative, neutral.
Allowed topic labels: {topics}.

Examples:
Post: RT @mention I hope everyone has an awesome weekend at #SXSW! I know @mention is giving away some great Apple prizes.
Output: {{"sentiment": "positive", "topic": "Apple"}}

Post: @mention really disappointed with the iPad app - lots of error messages have to switch to tweet deck for the rest of #sxsw
Output: {{"sentiment": "negative", "topic": "iPad or iPhone App"}}

Post: Check out iPad Design Headaches (2 Tablets, Call in the Morning) at SXSW. {{link}} #SXSW #tapworthy
Output: {{"sentiment": "neutral", "topic": "iPad"}}

Now classify this post:
Post: {post}
Output:
```

## structured_json

```text
You are a business analyst classifying brand-related social media posts.

Choose exactly one sentiment from: positive, negative, neutral.
Choose exactly one topic from: {topics}.

Rules:
- Use positive when the post expresses approval, excitement, appreciation, or praise.
- Use negative when the post expresses frustration, criticism, disappointment, or dislike.
- Use neutral when the post mostly reports information, asks a question, or mentions a brand/product without clear emotion.
- Do not invent a topic. Pick the closest topic from the allowed list.
- Return valid JSON only. No markdown. No explanation.

Post: {post}

JSON schema:
{{"sentiment": "positive|negative|neutral", "topic": "one allowed topic"}}
```
