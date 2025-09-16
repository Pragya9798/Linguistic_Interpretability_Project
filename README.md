# Linguistic_Interpretability_Project
Analyzing attention heads to see how mBERT processes gender morphology in languages with gendered nouns.


Linguistic_Interpretability.ipynb
Core Analysis: Tests attention heads' sensitivity to gender agreement violations by comparing model behavior on correct vs. incorrect article-noun pairs.
Key Components:

Minimal Pairs Generation: Creates pairs like "Der Mann" (correct) vs "Die Mann" (incorrect gender agreement) from German UD corpus
Attention Head Patching: Systematically replaces attention patterns from one head with patterns from corrupted examples to measure causal effects
Head Classification:

Error-sensitive heads (early layers 0-1): Show large effects when patched, suggesting they detect agreement violations
Gender-predictive heads (layers 6, 8, 11): Successfully classify gender from their representations


Synergy Testing:
