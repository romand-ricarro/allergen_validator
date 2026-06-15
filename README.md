# allergen_validator

A Python tool for validating allergen predictions from an ML model against structured food label text, based on the 14 major allergens defined by London Standards.

## What it does

- Detects whether food label text contains explicit allergen declarations (e.g. `Allergens: Milk, Eggs`, shorthand codes like `(N,P)`, may-contain warnings)
- Compares an ML model's predicted allergens against what's actually declared in the text
- Flags invalid predictions with a confidence level and explanation
- Runs batch validation over a CSV dataset and exports a `validation_results.csv`
- Analyses error patterns and generates a `suggested_corrections.csv` for model fine-tuning

## Project structure

```
allergen_validator.py    # Core validator class (EnhancedAllergenValidator)
run_validation.py        # Entry point — runs batch validation on a CSV file
results_analyzer.py      # Analyses validation output and suggests model improvements
data.csv                 # Input dataset (text + ml_prediction columns)
validation_results.csv   # Output — per-row validation results
suggested_corrections.csv # Output — suggested corrections for invalid predictions
```

## Setup

```bash
pip install pandas
```

## Usage

```bash
python run_validation.py
```

Input CSV must have `text` and `ml_prediction` columns. Results are written to `validation_results.csv`.

To analyse results and generate correction suggestions:

```bash
python results_analyzer.py
```

## Supported allergens

Celery & Celeriac, Crustaceans, Dairy, Eggs, Fish, Gluten, Lupin, Molluscs, Mustard, Nuts, Peanuts, Sesame, Shellfish, Soybeans, Sulphites
