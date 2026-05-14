# Week 4: Model Comparison

[cite_start]Tested 4 AI models on 5 Cybersecurity text samples to evaluate their suitability for the Alert Classification component of our Capstone project[cite: 6, 281, 326].

## Models Tested
- [cite_start]**HF Sentiment:** distilbert-base-uncased-finetuned-sst-2-english [cite: 101, 278, 327]
- [cite_start]**HF Zero-Shot:** facebook/bart-large-mnli [cite: 131, 279, 327]
- [cite_start]**HF NER:** dslim/bert-large-NER [cite: 163, 280, 327]
- [cite_start]**Groq:** Llama 3 8B [cite: 194, 281, 327]

## Findings
[cite_start]I recommend **Groq Llama 3 8B** for the alert classification component because it provided the most accurate severity levels and reasoning, whereas the Sentiment model incorrectly flagged routine system maintenance as a threat[cite: 295, 302, 327].

[cite_start]See `report.md` for the full technical analysis and results table[cite: 260, 328].

## Reflection
[cite_start]What surprised me most was how poorly the Sentiment model performed on technical logs[cite: 328]. [cite_start]Because it was trained on movie reviews, it interpreted words like "failed" or "unauthorized" as extreme negatives even when the context described routine or successful system security measures[cite: 101, 307]. This highlighted that specialized security tasks require models with reasoning capabilities or domain-specific training rather than general sentiment analysis.
