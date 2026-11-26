# DSCC240_Final_Project
## Data Preprocessing (Lynne) — `01_Data_Preprocessing.ipynb`
Needs `arxiv-metadata-oai-snapshot.json` (Kaggle) in this folder.

**Abstracts**
1. Read all 3.2M papers; field = primary category (8 fields, all physics archives → `physics`); date = v1.
2. Keep two windows: pre = Jan 2020–Nov 2022, post = Jul 2023–Sep 2025.
3. Drop pre papers revised after ChatGPT (the stored abstract is the latest version).
4. Clean text: LaTeX math → `[MATH]` (kept in `math`), citations removed, URLs → `[URL]`, LaTeX commands/accents fixed, line breaks joined.
5. Drop withdrawn, < 30 words, non-English, and duplicate abstracts.
6. Save `abstracts_clean.csv.gz` (on Drive, too big for GitHub). Use `abstract` for features; numbers written in LaTeX are in `math`.

**Introductions (H2)**
1. Sample 60 papers per field × period (same version as the abstract).
2. Download the LaTeX source from arXiv (PDF if no source); take the text from `\section{Introduction}` to the next section.
3. Clean with the same function as the abstracts; keep intros with ≥ 100 words → `introductions.csv`.
Needs internet + `pip install requests pypdf`; ~50 min for all papers (set `N_TEST = None`).
