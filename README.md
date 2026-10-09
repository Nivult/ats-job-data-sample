# 📊 Sample Dataset: Normalized Job Postings from 60+ ATS Platforms

This repository contains a free, static sample of job postings extracted directly from enterprise Applicant Tracking Systems (Workday, Greenhouse, SAP SuccessFactors, iCIMS, Lever, etc.).

Scraping ATS platforms is notoriously painful. The data is messy, job titles don't reflect the actual tech stack, and aggregators are full of expired listings. We built Nivult to solve this: we index directly from the source and run proprietary classifiers to extract and normalize the actual data.

### 🚀 Scale of the Full Nivult Dataset
While this repository contains a static sample, our live API and database continuously track more than:
*   **3,896,088** active job postings
*   **69,625** companies hiring now
*   **245** countries covered
*   **106,034** new postings / day

### 💡 About this sample
* **Format:** `.jsonl` (100k lines, gzipped)
* **Content:** Job title, company info, full description text, location, seniority, remote policy, employment type, and extracted technologies.
* **Source:** Directly from employer career pages (no generic job boards).

### 💡 Data Schema Example
Every line in the `.jsonl` file is a valid JSON object. Here is the normalized structure:

```json
{
  "id": "103498...",
  "employer": {
    "name": "TechCorp Inc.",
    "industry": "Software Development",
    "team_size": "1000-5000"
  },
  "job": {
    "title": "Senior Backend Engineer",
    "location": "Remote",
    "remote_policy": "Fully Remote",
    "seniority": "Senior",
    "employment_type": "Full-time"
  },
  "extracted_technologies": ["Python", "PostgreSQL", "Kubernetes", "AWS"],
  "url": "[https://techcorp.workday.com/](https://techcorp.workday.com/)...",
  "scraped_at": "2026-10-09T08:00:00Z"
}
```

### 🐍 Quickstart (Python)
Want to test the data quickly? Here is how to parse the `.jsonl` file:

```python
import json

with open('sample_data.jsonl', 'r') as file:
    for line in file:
        job = json.loads(line)
        print(f"{job['job']['title']} at {job['employer']['name']}")
```


### ⚡ Need the Live API?

This repository is just a static snapshot. If you need the live index—updated daily with delta feeds (new, updated, and closed postings)—you can use our API.

👉 Get the Live API on RapidAPI Hub at https://rapidapi.com/nivult-nivult-default/api/nivult-job-postings-company-data
