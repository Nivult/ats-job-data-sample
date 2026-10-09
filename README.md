# 📊 Sample Dataset: Normalized Job Postings from 60+ ATS Platforms

This repository contains a free, static sample of job postings extracted directly from enterprise Applicant Tracking Systems (Workday, Greenhouse, SAP SuccessFactors, iCIMS, Lever, etc.).

Scraping ATS platforms is notoriously painful. The data is messy, job titles don't reflect the actual tech stack, and aggregators are full of expired listings. We built **Nivult** to solve this: we index directly from the source and run proprietary classifiers to extract and normalize the actual data.

### 📦 About this sample
- **Format:** `.jsonl.gz` (JSON Lines, gzipped)
- **Content:** Job title, company info, full description text, location, seniority, remote policy, employment type, and extracted technologies.
- **Source:** Directly from employer career pages (no generic job boards).

### 💡 Data Schema Example
Every line in the `.jsonl` file is a valid JSON object. Here is the normalized structure:

```json
{
  "id": "e8a9f0...",
  "employer": {
    "name": "TechCorp Inc.",
    "industry": "Software Development",
    "size_band": "1000-5000"
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
  "scraped_at": "2026-10-08T00:00:00Z"
}

⚡ Need the Live API?
This repository is just a static snapshot. If you need the live index—updated daily with delta feeds (new, updated, and closed postings)—you can use our API.

👉 Get the Live API on RapidAPI Hub at https://rapidapi.com/nivult-nivult-default/api/nivult-job-postings-company-data
