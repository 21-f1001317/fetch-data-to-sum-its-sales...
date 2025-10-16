# Sales Summary SPA

## Overview
A single-page web app that:
- Loads `data.csv` from the same directory, sums its `sales` column, and displays the total.
- Sets the document title to “Sales Summary ${seed}” where `seed` is read from the `?seed=` query parameter.
- Loads Bootstrap 5 from jsDelivr.
- Displays a captcha image passed via `?url=...` and attempts to solve it (displaying the extracted text) within 15 seconds using Tesseract.js. If the URL returns plain text or JSON with a `text`/`solution` field, that value is shown directly.

## Setup
- Place `index.html` and `data.csv` in the same directory on any static web server.
- Ensure `data.csv` has a header row that includes a `sales` column. The parser is case-insensitive for `sales` and tolerates currency symbols and thousand separators.
- The app uses CDNs:
  - Bootstrap 5 via jsDelivr
  - PapaParse for CSV parsing
  - Tesseract.js for OCR

No build step is required.

## Usage
- Open the page in a browser: `index.html`
- Title seed:
  - Append `?seed=12345` to set the page title to “Sales Summary 12345”.
- Sales total:
  - The app automatically fetches and parses `data.csv` and displays the sum of the `sales` column in the “Total Sales” card.
- Captcha solver:
  - Append a captcha image URL: `?url=https%3A%2F%2Fexample.com%2Fcaptcha.png`
  - The page will display:
    - The provided URL (and link).
    - The captcha image.
    - The solved text (via OCR) within ~15 seconds if possible.
  - If the URL returns plain text or JSON (with `text` or `solution`), that content is immediately shown as the solved text.
  - Note: The captcha URL should allow CORS for the browser to fetch its bytes for OCR. If CORS is blocked, image display may still work but OCR may fail.

Examples:
- `index.html?seed=42`
- `index.html?seed=42&url=https%3A%2F%2Fyour-cors-enabled-host%2Fcaptcha.jpg`

## License
MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the “Software”), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.