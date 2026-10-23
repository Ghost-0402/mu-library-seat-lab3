# MU Library Seat System: Lab 3 (Architecture Trade-Offs & Dual-Layer Validation)
ICT461 Advanced Web Technologies, Group O. Author of this submission: Dennis Sampa (202302571).

## What is new in Lab 3
- `/lab3`: the Lab 2 accessible check-in form, now submitting with the Fetch API (loading, success and error states).
- `POST /api/lab3/checkin`: server-side validation, sanitisation and conflict checks; errors follow RFC 7807 (`application/problem+json`) with HTTP 400, 409, 413, 415 or 422.
- `validation.py`: the server-side rules. `static/lab3.js`: client-side rules plus Fetch.

## Requirements
Python 3.9+ and Flask (`pip install -r requirements.txt`).

## Run
```
cd mu_library
python app.py          # http://localhost:5000/lab3
```
To run the evidence tests, start the server on port 5055 (`python -c "import app; app.app.run(port=5055)"`) and run `evidence/run_tests.sh` (needs curl). `tools/browser.js` needs Node and Playwright.

## Layout
mu_library/ (Flask app), evidence/ (curl_log.txt, browser_tests.txt, run_tests.sh, screenshots), tools/browser.js.

## Known limits
No GPS check on this endpoint, no login/CSRF/rate limiting, notes are validated and sanitised but not stored.
