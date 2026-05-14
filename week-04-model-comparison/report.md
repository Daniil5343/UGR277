#Model Comparison Report — Week 4 
**Name:** [Daniel] 
**Date:** [4/13/26] 
**Project:** [Model Comparison] 
**Component:** [The Entire Thing] 
## Test Setup 
**Input dataset:** 5 [CyberSecurity] text samples covering: - 2 clearly concerning/high-severity records - 1 ambiguous/edge case record - 2 routine/benign records 
**Models tested:**
1. distilbert-base-uncased-finetuned-sst-2-english (sentiment) 
2. facebook/bart-large-mnli (zero-shot classification) 
3. dslim/bert-large-NER (named entity recognition) 
4. Groq Llama 3 8B (LLM classification) 
**Evaluation criteria:** label accuracy, confidence score, speed, ease of 
integration in n8n 
## Results Summary 
| Record | Sentiment | Zero-Shot | NER Entities | Groq |
|--------|-----------|-----------|-------------|------|
| 1 | NEGATIVE (0.9959) | possible anomaly | Moscow (LOC) | HIGH: Unauthorized login attempt from an unfamiliar location suggests potential malicious activity. |
| 2 | NEGATIVE (0.9986) | routine activity | none | INFORMATIONAL: Routine, expected event that does not pose a significant threat. |
| 3 | NEGATIVE (0.9958) | possible anomaly | Amazon (ORG) | HIGH: Phishing email with a spoofed domain is a targeted attack that could compromise information. |
| 4 | NEGATIVE (0.9996) | possible anomaly | SS (MISC) | HIGH: High frequency of failed SSH attempts indicates a brute-force attack. |
| 5 | NEGATIVE (0.9874) | routine activity | none | INFORMATIONAL: Does not indicate abnormal activity or a security issue. |

## Analysis 
**Where models agreed:** [All models correctly flagged the unauthorized login and phishing email as negative or concerning events.] 

**Where models disagreed:** [The Sentiment model (DistilBERT) classified the routine firewall update and normal resource utilization as "NEGATIVE"
with high confidence, while Zero-Shot and Groq correctly identified them as routine/informational.] 

**Most accurate model overall:** [Groq Llama 3 8B provided the most nuanced and accurate 
classifications by distinguishing between technical terminology and actual malicious intent.] 
9 / 15

**Fastest/most practical:** [HF Zero-Shot is highly practical for simple classification tasks, but Groq's speed and reasoning 
make it more reliable for complex security analysis.] 

**Recommended Models and insight **
**Primary model**: Groq Llama 3 8B - It provides high-accuracy severity levels and essential reasoning for security analysts.   


**Secondary model**: HF Zero-Shot - Useful as a fast, secondary filter to categorize alerts before they are sent for detailed LLM analysis.   

**Rejected models and why**: HF Sentiment (DistilBERT): Rejected because it is too biased toward technical keywords, 
incorrectly flagging routine maintenance as negative threats.

**Failure Cases and Limitations**
The Sentiment model failed to understand the context of "routine maintenance," flagging it as 99% negative. 
This demonstrates that models trained on general datasets (like movie reviews) are unsuitable for production 
security environments where "normal" behavior still uses technical, often "scary-sounding" language.
