CV Evaluator 1.0 — Compare your CV against any role or job posting and get how well you match against its requirements, as well as suggestions for courses to take to close the skill gaps.

Copyright 2025 **Rene Chiquete Elizalde.**

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0
LinkedIn: https://www.linkedin.com/in/renechiquete/ 

This is a web app made in Python to be executed in Flask, you will likely need to modify it to run in on other framework.
Follow these steps to run the app locally from the unzipped folder.

## Prerequisites
- Python 3.11+ installed and on PATH.
- (Optional, for OCR fallback) Tesseract OCR and Poppler binaries:
  - **Windows:** Install Tesseract (e.g., UB Mannheim build) and Poppler binaries. Set paths in `config.py` if they’re not on PATH.
  - **macOS:** `brew install tesseract poppler`
  - **Linux (Debian/Ubuntu):** `sudo apt-get install tesseract-ocr poppler-utils`
  - Without these, embedded PDF text still works; OCR fallback just won’t run.

## Setup
1) Open a terminal in the unzipped folder.
2) Create and activate a virtual environment:
   - **Windows (PowerShell):**
     ```powershell
     python -m venv .venv
     .\.venv\Scripts\Activate.ps1
     ```
   - **macOS/Linux:**
     ```bash
     python3 -m venv .venv
     source .venv/bin/activate
     ```
3) Install dependencies:
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

## Configure OpenAI
- Recommended: set your key via environment variable before running:
  - **Windows (PowerShell):**
    ```powershell
    $env:OPENAI_API_KEY="sk-..."
    ```
  - **macOS/Linux:**
    ```bash
    export OPENAI_API_KEY="sk-..."
    ```
- Alternate (less secure): place the key in `config.py` as `OPENAI_API_KEY`.

## Windows OCR paths (if needed)
- Set these in `config.py` if Tesseract/Poppler aren’t on PATH:
  ```python
  TESSERACT_CMD = r"C:\Program Files\Tesseract-OCR\tesseract.exe"
  POPPLER_PATH = r"C:\path\to\poppler\Library\bin"
  ```

## Run the app
```bash
python app.py
```
- Browse to http://localhost:5000
- Upload a PDF CV and enter a target role/description or job URL.

## Notes
- Keep `.venv/` out of any ZIP you share; users recreate it per-platform.
- `MAX_CONTENT_LENGTH` limits uploads to 5 MB by default (see `config.py`).
- OCR is a fallback: if embedded text is available, it’s used first; otherwise OCR is attempted (needs Tesseract/Poppler).
