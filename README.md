# Resume Skill NER (spaCy)

A spaCy-based Named Entity Recognition (NER) pipeline to extract SKILL entities from curriculum vitae / resumes. This project contains the end-to-end notebook used for dataset inspection, annotation cleaning, training, evaluation, and model export.

- Notebook: notebooks/spacy-model-train.ipynb — trains a single-label NER model (SKILL) from annotated CV JSONs.
- Recommended repo name: `resume-skill-ner` (or `spacy-skill-extractor`).
- Quick result (from the notebook): cleaned-model evaluation — Precision ≈ 58.9%, Recall ≈ 62.3%, F1 ≈ 60.5% (see notebook for full training logs and token-level metrics).

Why this project
- Automatically identifying skills from CVs is useful for resume screening, candidate matching, and HR automation.
- This notebook demonstrates preprocessing, overlap-cleaning of annotations, spaCy training flows, evaluation, and model export — a full reproducible example.

What’s included
- notebooks/spacy-model-train.ipynb — main runnable notebook (training, evaluation, saving).
- data_sample/ — small anonymized example JSONs (add a tiny subset; do not include private data).
- requirements.txt — exact Python packages to reproduce.
- .gitignore — recommended ignores.
- README.md — this file.

High-level workflow in the notebook
1. Load annotated CV JSONs from a dataset folder.
2. Detect and remove overlapping annotations (keep longest span).
3. Normalize labels to a single `SKILL` label.
4. Validate char-span alignment and drop misaligned spans.
5. Train a spaCy NER model (blank English model, NER pipe) and evaluate on a holdout set.
6. Save trained model under `/kaggle/working/skill_ner_model_clean` (not committed to git; large files should be handled separately).

How to run (quick)
- Option A — Run notebook on Kaggle (recommended for reproducibility)
  1. Open notebooks/spacy-model-train.ipynb on Kaggle and run "Save Version" → (optionally) "Save & GitHub".
  2. Confirm the commit and click "View on GitHub".

- Option B — Run locally
  1. Clone the repo:
     git clone https://github.com/<your-username>/resume-skill-ner.git
  2. Create and activate a virtual env:
     python -m venv .venv
     source .venv/bin/activate   # macOS / Linux
     .venv\Scripts\activate      # Windows (PowerShell: .venv\Scripts\Activate.ps1)
  3. Install dependencies:
     pip install -r requirements.txt
  4. Place a small sample of your dataset in `data_sample/` (or update the DATA_PATH in the notebook).
  5. Start Jupyter and run the notebook:
     jupyter notebook
     # open notebooks/spacy-model-train.ipynb and Run → Run All

Reproducibility and environment
- Python: 3.10–3.12 compatible (notebook used Python 3.12).
- See requirements.txt for core packages; pin versions in a real production repo or include environment.yml for Binder.

Key results (from notebook)
- After annotation cleaning and training a spaCy NER:
  - Clean-model token metrics (notebook final): Precision ≈ 58.91%, Recall ≈ 62.27%, F1 ≈ 60.54%.
  - Full per-run losses and example predictions are in the notebook outputs.
- Notes: metrics vary with preprocessing choices, label normalization, and model hyperparameters — the notebook shows both raw and cleaned workflows for comparison.

Data & privacy
- The notebook in this project used a Kaggle dataset at `/kaggle/input/datasets/sarmadmirza12/zipcvv/ZIP`.
- Do NOT commit private or personally identifiable data to GitHub. Provide a sanitized `data_sample/` or instructions to reproduce from original sources.

Model artifacts and size
- Trained models are saved to `/kaggle/working/skill_ner_model_clean` in the notebook.
- Do not commit large model artifacts (>50 MB) directly to the repo. Use:
  - GitHub Releases to host model files, or
  - Git LFS for versioned large files, or
  - provide a download link in README.
    
Contact / author
- Your Name — GitHub: @sarmadmirza8888
- Email: sarmadmirza8888@gmail.com

