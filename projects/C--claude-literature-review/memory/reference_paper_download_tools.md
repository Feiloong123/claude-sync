---
name: Paper download tools
description: scidownl CLI tool and custom downloader script for academic paper PDFs
type: reference
originSessionId: c2344b10-2b89-475e-8cab-b1f8bc2c8758
---
**scidownl** (pip package v1.0.2): CLI + Python API for Sci-Hub downloads. Security reviewed — clean code, no malicious behavior. Supports DOI/PMID/title search.

Usage: `scihub -d <DOI> -o <output_dir>` or via Python API `scidownl.api.scihub.scihub_download(keyword=doi, out=dir)`.

Limitations: Sci-Hub domains frequently blocked in China; DNS resolution fails for `.se` domains; page parser may break when Sci-Hub changes HTML structure.

**Custom downloader**: `scripts/download_papers.py` — tries OA publisher first, then Sci-Hub with multiple mirrors. Handles MDPI (via CDN), De Gruyter, RSC, Elsevier.

**Known issue**: MDPI direct access may be IP-blocked (403). Use MDPI CDN URL pattern: `https://mdpi-res.com/d_attachment/<journal>/<journal>-<vol>-<art>/article_deploy/<journal>-<vol>-<art>.pdf?version=<ver>`.
