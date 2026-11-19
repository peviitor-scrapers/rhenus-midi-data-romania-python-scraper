# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added
- Cauta.ro company-profile mapping and the official Rhenus job board as
  additional sources; Emprego job links come from its search page (#1).
- Tolerant employer matching (`_employer_matches`) for portals that truncate
  the legal name in JSON-LD (#1).
- Enriched non-personal fields: location, salary, date and expiry date (#1).

### Changed
- Company identity set to RHENUS MIDI DATA ROMANIA SRL (CUI `33231931`);
  config, docs and test fixtures rebranded (#1).
- Source identifier is now `mediere.anofm.ro, jobrapid.ro, bebee.com,
  jobica.ro, emprego.com, cauta.ro, rhenus.group` (#1).
- Stale-job scope covers all seven source URL prefixes (#1).

## [1.0.0] - 2026-11-19

### Added
- Python scraper for **RHENUS MIDI DATA ROMANIA SRL** (CUI `33231931`),
  reading jobs from ANOFM (`mediere.anofm.ro`).
- Publisher to peviitor v1 API: company upsert, job upload, stale-job delete.
- ANAF company validation with CUIScan fallback and cache.
- Unit, integration, e2e, and consistency tests.
- GitHub Actions workflows and GitHub Pages (`docs/`) with generated `jobs.md`.
- AI documentation under `ai/`.
