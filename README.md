[![Oportunitati si Cariere](https://github.com/peviitor-scrapers/rhenus-midi-data-romania-python-scraper/actions/workflows/job-seeker-ro-spider.yml/badge.svg)](https://github.com/peviitor-scrapers/rhenus-midi-data-romania-python-scraper/actions/workflows/job-seeker-ro-spider.yml)
[![Automation Tests](https://github.com/peviitor-scrapers/rhenus-midi-data-romania-python-scraper/actions/workflows/automation-testing.yml/badge.svg)](https://github.com/peviitor-scrapers/rhenus-midi-data-romania-python-scraper/actions/workflows/automation-testing.yml)
[![Version](https://img.shields.io/badge/version-1.0.0-blue)](CHANGELOG.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.12-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Website](https://img.shields.io/website?url=https%3A%2F%2Fpeviitor.ro&label=peviitor.ro)](https://peviitor.ro)
[![API](https://img.shields.io/website?url=https%3A%2F%2Fapi.peviitor.ro%2F&label=api.peviitor.ro)](https://api.peviitor.ro/)
[![GitHub Pages](https://img.shields.io/github/deployments/peviitor-scrapers/rhenus-midi-data-romania-python-scraper/github-pages?label=GitHub%20Pages)](https://peviitor-scrapers.github.io/rhenus-midi-data-romania-python-scraper/)

# job_seeker_ro_spider — RHENUS MIDI DATA ROMANIA SRL Scraper

**job_seeker_ro_spider** — a scraper for RHENUS MIDI DATA ROMANIA SRL jobs in Romania. It collects announcements published by the company on [ANOFM](https://mediere.anofm.ro/app/module/mediere/jobs), [jobRapid](https://www.jobrapid.ro/), [BeBee](https://bebee.com/) and [Jobica](https://jobica.ro/), then publishes them to [peviitor.ro](https://peviitor.ro) through the Peviitor API.

ANOFM is the authoritative source (`employer_tax_code=33231931`). The other portals republish the same ANOFM offer on their own detail pages; because peviitor.ro identifies jobs by unique URL, each distinct URL is published as a distinct job. Horeo and Emprego had no matching postings; Ziarul Muncii, Careerjet, Jooble and BestJobs have no own job-detail URLs. The company has no reachable careers website.

> **🌱 Derived scraper.** This repository is derived from [minon-investment-srl-python-scraper](https://github.com/peviitor-scrapers/minon-investment-srl-python-scraper).

## Overview

The project automates the daily collection of RHENUS MIDI DATA ROMANIA SRL jobs in Romania, keeping the peviitor.ro board up to date with the latest career opportunities.

## Features

- Extracts jobs from ANOFM (`mediere.anofm.ro`) by employer CUI
- Extracts jobRapid postings by company-name search and JSON-LD `JobPosting` blocks
- Derives BeBee and Jobica detail URLs from ANOFM ids, reads Emprego links from its search page, maps Cauta.ro's company profile and includes the official Rhenus job board; each page's hiring organization is verified
- Deduplicates by URL across all seven sources; distinct URLs remain distinct jobs
- Publishes non-personal fields stated by the source: location, salary, tags, work mode and expiry date
- Never stores job descriptions, contact names, emails or phone numbers (GDPR data minimization)
- Validates the company via CUIScan (legal name and address, by CIF) and CUIFirma (brand search)
- **Company cache** — does not hit the APIs on every scrape
- **Stale cache / config fallback** when CUIScan is unavailable
- Cross-validates against the Peviitor API
- Deletes stale jobs from peviitor when they are no longer live (scoped to this scraper's seven URL prefixes)
- Stores to the Peviitor API (job core + company core)
- Generates `docs/jobs.md` automatically — accessible on GitHub Pages
- **Company identity in a single file** (`scraper/config/company.json`)
- GitHub Actions: daily scrape + automated testing (unit, integration, e2e, consistency)
- Identifies itself through the User-Agent: `job_seeker_ro_spider`

## Local setup

```bash
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python -m pytest tests/unit tests/consistency   # offline checks
.venv/bin/python -m scraper.index                         # full scrape + publish
```

## License

Copyright (c) 2026 Alexandra Ifrim

Licensed under the [MIT License](LICENSE).

## Managed By

This project is managed by [ASOCIATIA OPORTUNITATI SI CARIERE](https://oportunitatisicariere.ro) and used as a web scraper for the [peviitor.ro](https://peviitor.ro) job board project.

## Disclaimer

This scraper is designed for educational purposes and legitimate job data aggregation for the Romanian job market.
