# Slinglish Translator Automation

This project runs Playwright-based UI automation against the PixelsSuite chat translator and writes results back to an Excel file.

## Requirements

- Python 3.9+ (3.10+ recommended)
- Playwright browsers installed

## Setup

From the project folder:

python -m venv .venv
.\.venv\Scripts\activate
python -m pip install --upgrade pip
pip install playwright openpyxl
python -m playwright install
## Test Data (Excel)

The script expects an Excel file containing test cases with input and expected Sinhala output columns.

Important details:

- The default Excel path in the script points to ../test_automation/Assignment 1 - Test cases.xlsx.
- In this repository, the Excel file is located next to the script: Assignment 1 - Test cases.xlsx.
- To avoid path issues, pass the file explicitly with --excel.
- The default sheet name is  Test cases (note the leading space).

## Run

Basic run (headed browser):

python test_automation.py --excel "Assignment 1 - Test cases.xlsx"
Headless run:

python test_automation.py --excel "Assignment 1 - Test cases.xlsx" --headless
Specify sheet name if yours differs:

python test_automation.py --excel "Assignment 1 - Test cases.xlsx" --sheet "Test cases"
Override target URL:

set FRONTEND_URL=https://www.pixelssuite.com/chat-translator
python test_automation.py --excel "Assignment 1 - Test cases.xlsx"
## Outputs

The script updates the Excel file with:

- Actual output text
- Status (PASS, FAIL, or COLLECTED)

You can change output destination:

python test_automation.py --excel "Assignment 1 - Test cases.xlsx" --output "results.xlsx"
## Notes

- The script auto-detects columns based on common header names (Singlish/Input/Expected/Actual/Status).
- If headers are unusual or merged, you can set --header-row and --input-col, --expected-col, --actual-col, --status-col.
