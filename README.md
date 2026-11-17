# Sample Dataset: Normalized Job Postings from 65+ ATS Platforms

This repository contains a free, static sample of job postings and companies read directly from enterprise Applicant Tracking Systems (Workday, Greenhouse, SAP SuccessFactors, iCIMS, Lever, and many more).

Scraping ATS platforms is notoriously painful. The data is messy, job titles don't reflect the actual tech stack, and aggregators are full of expired listings. We built Nivult to solve this: we index directly from the source — the employer's own career system — and run our own measured classifiers to extract and normalize what matters.

## Scale of the full Nivult index

This repository is a static sample. The live index tracks, every morning:

* **6,000,000 active job postings** (rounded)
* **about 70,000 companies** hiring now
* **more than 240 countries and territories**
* **more than 150,000 new postings on peak days**

## About this sample

Snapshot updated **November 2026**.

* `Jobs Sample.gz`: **500 active job postings**, with full description text where available at the source
* `Company Sample.jsonl.gz`: **500 company profiles**, with domains, locations, technologies and hiring signals where available
* **Format:** `.jsonl.gz` (gzipped JSON Lines — one JSON object per line)
* **Content:** job title, company, full description text, location, seniority, remote policy, skills and technologies extracted from the text
* **Source:** employer career systems only — no job boards, no aggregators

## What a record looks like

A real row from this sample (lightly trimmed for readability):

```json
{
  "id": "0001d655-79a7-483a-ba13-0e6504f77170",
  "title": "Distribution Sales Intern – Summer 2027",
  "ats": "greenhouse",
  "company_slug": "nationallifeinsurancecompany",
  "company": "National Life Insurance Company",
  "url": "https://job-boards.greenhouse.io/nationallifeinsurancecompany/jobs/4394376009",
  "country": "US",
  "location": "Montpelier, VT",
  "language": "en",
  "seniority": "intern",
  "remote": "onsite",
  "skills": ["salesforce", "crm", "customer service", "lead generation", "onboarding"],
  "technologies": ["CRM", "MS Office", "Salesforce"],
  "posted_at": "2026-09-08 15:39:31+00:00",
  "first_seen": "2026-09-08 16:22:00.118614+00:00",
  "last_seen": "2026-11-16 22:48:23.596691+00:00",
  "description": "Come join one of America’s fastest-growing insurance companies..."
}
```

`posted_at` is the employer's own date; `first_seen`/`last_seen` are our reading dates — a posting is marked closed only when it disappears at the source.

## Quickstart (Python)

```python
import gzip, json

with gzip.open("Jobs Sample.gz", "rt") as f:
    for line in f:
        job = json.loads(line)
        print(f"{job['title']} at {job['company']} — {job['country']}")
```

## Need the live index?

This repository is a snapshot. The full index refreshes every morning and ships a delta feed (new, updated, closed postings) so your copy never goes stale.

* **Live API on RapidAPI:** https://rapidapi.com/nivult-nivult-default/api/nivult-job-postings-company-data
* **Actors on Apify Store:** search "Nivult"
* **Site & free portal trial:** https://nivult.com
