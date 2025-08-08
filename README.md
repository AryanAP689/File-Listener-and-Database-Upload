# File-Listener-and-Database-Upload
# Task 3 — Automated Sales Data Processing & Tracking (Google Colab)

## Overview
This module implements an automated **sales data ingestion pipeline** that:
1. Reads incoming sales files (`.csv`, `.xlsx`, `.xls`) from a designated folder.
2. Cleans and deduplicates records using a primary key (`ORDERNUMBER`).
3. Stores the processed data into an **SQLite database** (`sales.db`).
4. Tracks processed files to avoid reprocessing.
5. Moves files into `processed/` or `failed/` directories for organization.

The solution is implemented in **Google Colab** for portability.  
Colab was chosen to ensure that:
- The code runs identically across different operating systems without additional setup.
- No OS-specific file watcher dependencies are required.
- Users without local Python environments can still execute the task end-to-end.

In a local environment, this same logic can be adapted to use event-driven file monitoring (e.g., `watchdog`) instead of polling.

---

## Features
- **Multi-format support:** `.csv`, `.xlsx`, `.xls`
- **Encoding handling:** UTF-8 with fallback to Latin1 for messy CSV exports
- **Automatic deduplication:** Based on `ORDERNUMBER` (configurable)
- **Processed file tracking:** Maintains a log in the `processed_files` table
- **Folder organization:**
  - `data/` — incoming files
  - `processed/` — successfully processed files
  - `failed/` — files that could not be processed
- **Database storage:** SQLite for portability and easy querying

---

