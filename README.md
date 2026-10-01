# Retail sales-line trends without misleading month comparisons

Public-data learning study | Draft for review | Prepared with assistance

This reuses the same verified retail calculation as the personal portfolio site draft. It examines UCI Online Retail, not a real client engagement. The name of this directory is provisional: the analysis is sales-line trends and cancellation handling, not a matched customer returns-rate study.

## Results

541,909 raw lines become 536,641 after removing 5,268 exact duplicates. Deduplication is a modeling choice, not proof that those lines were mistakes.

524,878 positive sale lines have GBP 10,642,110.80 in line value. A positive sale line excludes C-prefix invoices, non-positive quantities and non-positive unit prices. This is not profit or net accounting revenue.

9,251 lines carry the cancellation prefix. The subset with negative quantity and positive price totals GBP 893,979.73 in absolute line value. It is not a matched returns cohort or a reliable return rate: original purchase matching, reasons and accounting adjustments are not analyzed.

For complete-month comparisons the analysis uses January-November 2011 only: 459,054 sale lines and GBP 9,182,867.74 in value. November is highest within that window at GBP 1,503,866.78 across 82,004 lines. December 2011 has only nine days, so comparing it with a full November would mislead. One year cannot establish stable seasonality.

135,037 / 536,641 deduplicated lines (25.2%) lack CustomerID. They remain in aggregate sales; customer segmentation would need separate handling.

## Reproduce

Download and extract the original Excel file from the exact source link below. The large raw Excel is deliberately not included in the review ZIP.

```sh
python -m pip install -r requirements.txt
python analysis/analyze.py --retail '/path/to/Online Retail.xlsx'
```

InvoiceNo and StockCode are read as text. Output aggregates and source-file SHA256 are under `data/`. The retail script is the portfolio site's implementation with only the unrelated synthetic-quality section removed. Its retail output was independently rerun from the original Excel and matched all the site's reported retail results exactly.

## Source and license

Daqing Chen, *Online Retail*, UCI Machine Learning Repository (2015), DOI 10.24432/C5BW33. Source page lists CC BY 4.0. New analysis/aggregates are transformations. Preserve this attribution if shared.

- https://archive.ics.uci.edu/dataset/352/online+retail
- https://archive.ics.uci.edu/static/public/352/online+retail.zip

Source describes transactions from 1 December 2010 to 9 December 2011 at a UK-based non-store retailer, sterling unit prices, and C-prefix cancellation invoices. Data accessed 1 October 2026. Source license applies to the dataset; no separate code license selected.
