# MedCode Finder

A local web version of the medical code search notebook. It uses HTML, CSS and JavaScript for the interface and Python/Flask with pandas for loading and searching CSV data. No external API is used.

## Run

```powershell
python -m pip install -r requirements.txt
python app.py
```

Open `http://127.0.0.1:5000` and upload the three CSV datasets from **Manage datasets**.

Expected files and required columns:

- Diagnosis: `Description`
- Procedure: `Description`
- NDC: `PHARM_CLASSES`, `PROPRIETARYNAME`, `NONPROPRIETARYNAME`

Uploaded files are stored in the local `data` directory. Searches use case-insensitive literal substring matching, matching the notebook workflow while safely handling special characters.

## Medical terminology expansion

The app first checks for an exact, case-insensitive match in `Short_Term` and `Long_Term` in `data/medical_terms.csv`. A match searches every semicolon-separated synonym in `Search_Terms`; otherwise the original input is searched directly.
