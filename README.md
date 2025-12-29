# CVE Dashboard README

## Overview

This project is a single-page HTML **dashboard** that displays the 10 most recent CVEs from the NVD (National Vulnerability Database) via the NVD CVE API 2.0.  It includes a real-time update button, severity statistics, and a responsive, modern UI suitable for security monitoring use cases.[2]

***

## Features

- Top 10 most recent CVEs (last 30 days window).[2]
- Real-time update button that pulls fresh data from the NVD CVE 2.0 API.[2]
- Severity classification (CRITICAL, HIGH, MEDIUM, LOW) calculated from CVSS v3.x base score.[2]
- Summary statistics cards: total CVEs, count of critical and high severity items.[2]
- Responsive layout using Tailwind CSS for a modern, glassmorphism-style interface.[2]
- Graceful error handling with fallback/demo CVE data if the NVD API call fails.[2]

***

## Prerequisites

- A modern web browser (Chrome, Edge, Firefox, or Safari).  
- Internet connectivity to:
  - Access the NVD CVE 2.0 API endpoint at `https://services.nvd.nist.gov/rest/json/cves/2.0`.[2]
  - Load Tailwind CSS and Chart.js from their public CDNs.[2]

No backend server or local Python runtime is required; all logic runs in the browser via JavaScript.

***

## Installation

1. Copy the dashboard HTML code into a new file, for example:

   - `cve-dashboard.html`

2. Save the file to any directory on your machine.

3. Open the file in your browser by either:
   - Double-clicking `cve-dashboard.html`, or  
   - Right-click → “Open with” → your preferred browser.

---

## Usage

1. Open the dashboard in your browser.  
2. On initial load, the dashboard automatically:
   - Queries the NVD CVE 2.0 API for the most recent 10 CVEs within the last 30 days.[2]
   - Populates the CVE table with ID, description, publish date, and severity.[2]
   - Updates the statistic cards for total, critical, and high CVEs.[2]
3. To refresh the data at any time, click the:

   - `🔄 Update CVEs (Real-time)` button.

4. If the NVD API is unavailable or rate-limited, the dashboard displays an error message and falls back to built-in sample CVE data so the UI remains functional.[2]

***

## File Structure

Since this is a single-page HTML app, everything resides in one file:

- `cve-dashboard.html`  
  - HTML layout and structure  
  - Tailwind-based styling via CDN  
  - JavaScript logic for:
    - Fetching data from NVD  
    - Parsing and normalizing CVE objects  
    - Severity scoring and color tagging  
    - Rendering the table and stats cards  

If you later split this into multiple files (e.g., `index.html`, `app.js`, `styles.css`), keep the API call and CVE processing logic together in a dedicated JS module.

***

## Configuration

You can customize the following aspects in the script section:

- **Date window**:  
  - Change the “last 30 days” window by adjusting the `startDate` calculation.[2]
- **Results per page**:  
  - Modify the `resultsPerPage` URL parameter to pull more or fewer CVEs.[2]
- **Severity thresholds**:  
  - Adjust the CVSS v3.x base score thresholds for CRITICAL/HIGH/MEDIUM/LOW as desired.[2]

If you obtain an NVD API key, you can also add it as a request header or query parameter to improve rate limits, following the NVD API documentation.[2]

***

## Limitations

- Subject to NVD API rate limits and availability.[2]
- Severity classification depends on CVSS v3.0/v3.1 metrics; CVEs without those metrics default to LOW.[2]
- Runs entirely client-side; for internal networks or air-gapped environments, you would need a local proxy or backend to mirror NVD data.[2]

***

## Future Enhancements

Potential enhancements you can implement:

- Add filtering by product, vendor, or keyword.[2]
- Add auto-refresh on a configurable interval (e.g., every 5 minutes).[2]
- Persist last fetched CVEs in localStorage to show cached data on reload.[2]
- Integrate with SIEM/SOAR tooling via webhook or API gateway on the backend.[2]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/135872903/a8478726-1411-403f-8ed4-9a1cc381d8e8/Current-CVEs.docx)
[2](https://nvd.nist.gov/developers/vulnerabilities)
