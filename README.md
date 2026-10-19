# US Commodity Flow Survey 2012 and 2017: Power BI Dashboard

An 8 page Power BI dashboard built on the US Census Bureau Commodity Flow Survey (CFS) public use file, covering 10,526,184 shipment records: 4,547,661 from 2012 and 5,978,523 from 2017.

**Author:** Eric Asiedu-Akrofi

## Download
The full Power BI project (PBIP with semantic model, report and data) is in this repository. See Opening the project below.

## Pages
1. Operations Overview
2. Mode Performance
3. Commodity & Industry
4. Network & Corridors
5. 2012 to 2017 Comparison
6. Export & Special Shipments
7. Detailed Records
8. Quality Control

## Screenshots

### Operations Overview
![Operations Overview](screenshots/still_p1.png)

### Mode Performance
![Mode Performance](screenshots/still_p2.png)

### Commodity & Industry
![Commodity & Industry](screenshots/still_p3.png)

### Network & Corridors
![Network & Corridors](screenshots/still_p4.png)

### 2012 to 2017 Comparison
![2012 to 2017 Comparison](screenshots/still_p5.png)

### Export & Special Shipments
![Export & Special Shipments](screenshots/still_p6.png)

### Detailed Records
![Detailed Records](screenshots/still_p7.png)

### Quality Control
![Quality Control](screenshots/still_p8.png)

## Source
Official US Census Bureau Commodity Flow Survey public use microdata files:
- 2012 CFS Public Use File: https://www.census.gov/data/datasets/2012/econ/cfs/historical-datasets.html
- 2017 CFS Public Use File: https://www.census.gov/data/datasets/2017/econ/cfs/historical-datasets.html

Both years are loaded in full. A SURVEY_YEAR column (2012 or 2017) was added to every row; all other columns are as published. Weighted totals: 2012 $13.85 trillion and 11.30 billion tons; 2017 $14.52 trillion and 12.47 billion tons.

## Opening the project
1. Download or clone this repository.
2. The shipments data is split into parts because GitHub limits files to 100 MB. Rebuild `data/FactShipments.csv` before opening:
   - Windows PowerShell, from the `data` folder:
     `$f = Get-ChildItem FactShipments_parts\*.csv | Sort-Object Name; Get-Content $f[0] | Set-Content FactShipments.csv; $f | Select-Object -Skip 1 | ForEach-Object { Get-Content $_ | Select-Object -Skip 1 | Add-Content FactShipments.csv }`
   - Mac or Linux: `cd data && (head -1 FactShipments_parts/FactShipments_part01.csv; for f in FactShipments_parts/*.csv; do tail -n +2 "$f"; done) > FactShipments.csv`
3. Open `CFS_2012_2017.pbip` in Power BI Desktop and click Refresh.
