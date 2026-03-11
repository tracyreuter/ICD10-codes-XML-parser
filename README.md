# ICD10-codes-XML-parser

The International Classification of Diseases, 10th Revision (ICD-10) is a diagnostic and procedure coding system used for billing, research, and healthcare analytics.

## Overview

This repository contains Python tools for extracting and transforming ICD-10 data from the [Centers for Medicare and Medicaid Services (CMS)](https://www.cms.gov/medicare/coding-billing/icd-10-codes) into analysis-ready formats. CMS provides ICD-10 data in XML format and web-based tables, which require parsing and restructuring for healthcare data engineering workflows. Example use cases include: integrating ICD-10 data with patient data from electronic health record (EHR) systems, insurance claims analyses, and many other forms of healthcare analytics and reporting.

## Scripts

### 1. parse_ICD10_xml_file.ipynb

Parses ICD-10 diagnostic codes from CMS XML files and converts them to CSV format.

- Reads an XML file containing ICD-10 codes (e.g., `icd10cm_tabular_2026.xml`)
- Navigates the nested XML structure (chapters → sections → diagnoses → sub-diagnoses)
- Extracts diagnostic codes and descriptions
- Creates a pandas DataFrame with code and name columns
- Removes duplicate entries
- Adds UTC timestamp for data lineage tracking
- Exports to CSV format

### 2. scrape_mdc_data_from_cms.ipynb

Scrapes Major Diagnostic Category (MDC) and MS-DRG data from CMS web pages.

- Reads a list of CMS URLs from `cms_mdc_urls.csv`
- Extracts HTML tables from multiple CMS web pages using pandas `read_html()`
- Consolidates data from 74+ reference tables
- Links diagnostic codes (DX) with MS-DRG (Medicare Severity Diagnosis Related Groups) and MDC classifications