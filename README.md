# Explainable-AI-based-Classification-System

Implementation of the ECII (Exception-based Class-Individual Induction) algorithm for generating human-readable explanations from black-box classification models using knowledge graphs and ontology reasoning.

## Overview
This project implements and extends the research-based ECII algorithm to build interpretable machine learning systems. Instead of just predicting a class label, the system explains *why* an instance belongs to a class by generating logical rules grounded in domain ontologies.

**Key Contribution:** Extended base ECII algorithm with NLP-based similarity matching and enhanced relationship detection for improved explanation quality.

## What is ECII?

ECII (Exception-based Class-Individual Induction) is an explainable AI technique that:
- Takes a trained classification model's predictions
- Analyzes knowledge graphs and ontologies related to the domain
- Generates human-readable decision rules explaining each prediction
- Links predictions to domain concepts using logical reasoning

## Algorithm Details

### ECII Core Process

**Step 1: Individual Analysis**
For each classified instance:
  1. Extract feature values
  2. Map to ontology properties
  3. Identify applicable concepts


**Step 2: Concept Matching**

For each prediction:
  1. Vectorize using TF-IDF
  2. Compute cosine similarity with ontology concepts
  3. Rank matches above threshold (default: 0.85)
  4. Select most relevant concept


**Step 3: Rule Generation**

Generate rule in form:
  Class(x) ← Property1(x, value1) ∧ Property2(x, value2) ∧ ¬Property3(x)
  
Where:
  - Positive properties support classification
  - Negative properties (¬) are exceptions
  - All grounded in ontology semantics

**Step 4: Validation**

For each generated rule:
  1. Apply to training set
  2. Measure consistency (% correct classifications)
  3. Prune rules below consistency threshold
  4. Return top-K most reliable rules


## Evaluation Metrics

**Rule Quality:**
- **Consistency:** 85%+ (rules correctly explain training instances)
- **Coverage:** Percentage of instances with valid explanations
- **Conciseness:** Average rule length (fewer conditions = better)

**NLP Matching Performance:**
- **Similarity Threshold:** 0.85
- **Precision:** How often matched concepts are semantically correct
- **Recall:** Percentage of relevant concepts successfully matched
