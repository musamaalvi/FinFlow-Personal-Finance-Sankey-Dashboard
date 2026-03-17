# 💸 FinFlow — Personal Finance Sankey Dashboard

> **See exactly where your money goes.** FinFlow turns your bank transaction CSV into a beautiful, interactive Sankey diagram — with drill-down transaction tables, category filters, and month-by-month breakdowns.

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![No dependencies](https://img.shields.io/badge/External%20deps-pandas%20%2B%20openpyxl-orange)

---

## What it looks like

The Sankey chart shows your **income flowing into spending categories** — the wider the flow, the more you spent there. Click any category to drill down into individual transactions.

---

## Features

- 📊 **Interactive Sankey chart** — income → spending categories, sized by amount
- 🗓️ **Filter by year and month** — zoom into any period instantly
- 🏷️ **Category toggles** — include or exclude entire categories from the chart
- 🔍 **Transaction drill-down** — click any flow to see individual transactions below
- ☑️ **Per-transaction checkboxes** — deselect specific transactions to exclude them from totals
- 🔎 **Search** — filter transactions by merchant or description
- 📋 **Excel workbook** — multi-sheet `.xlsx` with monthly summary, category breakdown, and raw data
- 🏠 **Fully offline** — one HTML file, no server, no internet required

---

## Quickstart

### 1. Install dependencies (one time only)

```bash
pip3 install pandas openpyxl
```

### 2. Run

```bash
python3 generate_sankey.py your_transactions.csv
```

This outputs two files in your current directory:
- `Sankey_Chart.html` — open in any browser (Chrome/Firefox/Safari)
- `transactions.xlsx` — open in Excel or Numbers

### 3. Test with the sample file

A sample file is included so you can try it immediately:

```bash
python3 generate_sankey.py sample_transactions.csv
```

---

## CSV Format

FinFlow expects a CSV with **at minimum these 5 columns** (extra columns are ignored):

| Column | Description | Example |
|--------|-------------|---------|
| `Date` | Transaction date | `2024-03-15` |
| `Merchant Name` | Merchant name (can be blank) | `Tesco` |
| `Description` | Transaction description | `TESCO STORES 3321` |
| `Amount` | Positive = income, negative = expense | `-54.20` |
| `Category` | Spending category | `Groceries` |

> **Tip:** Most UK banks (Halifax, Barclays, Monzo, Starling) let you export a CSV from the app. The column names can be adjusted at the top of `generate_sankey.py` if yours differ.

---

## Configuring column names

If your CSV uses different column names, edit the `CONFIG` section at the top of `generate_sankey.py`:

```python
DATE_COL        = 'Date'
MERCHANT_COL    = 'Merchant Name'
DESCRIPTION_COL = 'Description'
AMOUNT_COL      = 'Amount'
CATEGORY_COL    = 'Category'
INCOME_CATEGORY = 'Income'           # Category value that means income
EXCLUDE_CATS    = ['Internal Transfers']  # Categories to ignore entirely
```

---

## How it works

```
your_transactions.csv
        │
        ▼
 generate_sankey.py
        │
        ├──▶ transactions.xlsx
        │      ├─ 📋 Transactions      (raw data)
        │      ├─ 📊 Monthly Summary   (income vs expenses by month)
        │      ├─ 🏷️ Categories        (all-time spending by category)
        │      └─ 🌊 Sankey Data       (the flow data)
        │
        └──▶ Sankey_Chart.html
               └─ Interactive Sankey + drill-down tables
```

---

## Project structure

```
finflow/
├── generate_sankey.py      # Main script — run this
├── sample_transactions.csv # Sample data to test with
└── README.md
```

---

## Requirements

- Python 3.8+
- `pandas`
- `openpyxl`
- A modern browser (Chrome, Firefox, Safari, Edge)

---

## GitHub Description

> One Python script that turns your bank transaction CSV into an interactive Sankey dashboard — filter by month, drill into categories, and see exactly where your income goes.

---

## License

MIT — do whatever you like with it.
