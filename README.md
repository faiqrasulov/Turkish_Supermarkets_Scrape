# Turkish supermarket price scraper and landed-cost table

> Project from 2023, kept as it was written.

Collects supermarket shelf prices from marketkarsilastir.com and turns them into a table of what
each product would cost landed in Azerbaijan.

## What it does

1. **Scrape.** Selenium and BeautifulSoup walk eight categories (dairy and breakfast, staples,
   bakery, drinks, snacks, ready meals, baby care, cleaning) and read every product page: barcode,
   name, origin, producer, net quantity, and the price in each chain.
2. **Clean.** Normalise product names and barcodes, extract brands and merge their spellings.
3. **Price.** Convert lira to manat, remove 18% VAT, and apply a landed-cost coefficient
   (transport 6%, customs 15.5%, other costs 3%, VAT 18%, margin).
4. **Summarise.** Minimum and average price per barcode across chains.

The saved run of 16 June 2023 holds **26,971 price rows** in 19 columns.

## Run it

```bash
pip install selenium webdriver-manager beautifulsoup4 pandas numpy tqdm psutil openpyxl
jupyter notebook MARKETKARSHILASHTIR.ipynb
```

## Limits

- The selectors and category page counts are from June 2023.
- The exchange rate and the cost percentages are constants in the notebook.
- Column names are in Azerbaijani (`MEHSUL AD` = product name, `QIYMET` = price).
- The multithreaded version is kept commented out; the single-thread version is the one that ran.

## Files

| File | Content |
|---|---|
| `MARKETKARSHILASHTIR.ipynb` | Scraper and price table |
| `MARKETKARSHILASHTIR.html` | Rendered copy |
