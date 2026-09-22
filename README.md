# Essential Drugs Reference Extraction

Transcription of a printed Persian *Model List of Essential Medicines* into structured,
machine-readable data: per-drug records with mechanism-of-action grouping, plus the page map
that ties each record back to its source page. Output of an OCR-then-verify pass over the
book's tabular layout.

**Suggested repo name:** `essential-drugs-extraction`
**Stack:** Python 3, PyMuPDF, Tesseract OCR, JSON datasets
**Status:** finished
**Last modified:** 2026-09-13

## What it does

- `ocr_extracted_200.json` - raw extraction of the ~200-entry monograph, one object per drug.
- `all_200_extracted.json` - merged pass combining OCR output with page-heading context.
- `clean_200_drugs.json` - normalised dataset: `group_mech` mechanism classes
  (e.g. `SULFONYLUREA (Insulin secretion)`), fixed RTL text, de-duplicated rows.
- `complete_page_map_200.json` / `complete_page_map_200_verified.json` - drug to source-page
  index; the `verified` file is the version where each mapping was checked against the page
  image rather than inferred from order.

## Notes

- The verified page map exists because the unverified one misassigned entries: page order in
  the printed book does not follow the list order, so positional inference put one drug's
  text under another's heading.
- `baseline_titles.txt` holds the section headings used as the extraction target list.
- Clinical reference data only - no patient data and no scraped personal records.
