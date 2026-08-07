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

## Abbreviation normalization

Normalization is fully local and deterministic; it does not call AI or any external service. Exact inputs such as `MM`, `NSCLC`, `BC`, and `AML` show possible full terms for the user to select before searching. Edit `data/medical_abbreviations.json` to extend the catalog.
