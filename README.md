# Linguistic_Interpretability_Project
Analyzing attention heads to see how mBERT processes gender morphology in languages with gendered nouns.


### Linguistic_Interpretability.ipynb
#### Core Analysis: Tests attention heads' sensitivity to gender agreement violations by comparing model behavior on correct vs. incorrect article-noun pairs.
Key Components:

Minimal Pairs Generation: Creates pairs like "Der Mann" (correct) vs "Die Mann" (incorrect gender agreement) from the German UD corpus
Attention Head Patching: Systematically replaces attention patterns from one head with patterns from corrupted examples to measure causal effects
Head Classification:

Error-sensitive heads (early layers 0-1): Show large effects when patched, suggesting they detect agreement violations
Gender-predictive heads (layers 6, 8, 11): Successfully classify gender from their representations


Synergy Testing: Checking for causal chains between error-sensitive and gender-predictive heads
Ablation Studies: Zero out attention heads and measure the impact on the  created masked language model predictions task using KL-divergence


### Gender_Encoding.ipynb
#### Core Analysis: Uses controlled stimuli with noun substitutions to test whether article representations encode the article's own gender vs. the gender of associated nouns.
Key Components:

Stimulus Creation: Generates templates from UD sentences, substituting nouns with different genders (e.g., "Der [NOUN]" with masculine/feminine/neuter nouns)
Representation Extraction: Extracts attention head representations at article positions
Hypothesis Testing:

H1: Article representations encode the article's morphological gender (low accuracy ~33%)
H2: Article representations are influenced by noun context (high accuracy >70%)


Cross-validation: Uses logistic regression to predict noun gender from article representations

Main Finding: Strong evidence for H2 - article representations consistently encode information about the gender of their associated nouns rather than just their own morphological properties.


Conclusion: mBERT's processing of grammatical gender involves a distributed system where different attention heads serve complementary roles: some detect agreement violations while others encode contextual gender information. Finding that articles encode noun gender information suggests the model learns sophisticated contextual dependencies rather than surface morphological patterns.
