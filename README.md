# US Commodity Flow Survey 2012 and 2017: Power BI Dashboard

![US Freight in Motion: dashboard preview](screenshots/preview.gif)

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

## Highlights

**Title card: US Freight in Motion, Commodity Flow Survey 2012 and 2017**

![Title card: US Freight in Motion, Commodity Flow Survey 2012 and 2017](screenshots/intro_title_card.png)

**Headline KPIs across both surveys: $28.37T shipment value, 23.77bn tons, 26.28bn estimated shipments**

![Headline KPIs across both surveys: $28.37T shipment value, 23.77bn tons, 26.28bn estimated shipments](screenshots/p1_kpi_cards_closeup.png)

**Shipment value rose from $13.85T in 2012 to $14.52T in 2017; tonnage from 11.30bn to 12.47bn tons**

![Shipment value rose from $13.85T in 2012 to $14.52T in 2017; tonnage from 11.30bn to 12.47bn tons](screenshots/p1_value_tonnage_2012_vs_2017_closeup.png)

**For hire truck carries 47.6% of shipment value with a mode label across 2012 and 2017**

![For hire truck carries 47.6% of shipment value with a mode label across 2012 and 2017](screenshots/p2_mode_share_donuts_closeup.png)

**Mode mix by survey year: for hire truck value splits 48.3% (2012) and 51.7% (2017)**

![Mode mix by survey year: for hire truck value splits 48.3% (2012) and 51.7% (2017)](screenshots/p2_mode_mix_by_year_closeup.png)

**Mixed freight is the top commodity at $2.82T across both surveys**

![Mixed freight is the top commodity at $2.82T across both surveys](screenshots/p3_top_commodities_closeup.png)

**Petroleum merchant wholesalers fell from 9.5% of value in 2012 to 5.9% in 2017**

![Petroleum merchant wholesalers fell from 9.5% of value in 2012 to 5.9% in 2017](screenshots/p3_industry_heatmap_closeup.png)

**Largest state flow: Texas to Texas at $2.58T, then California to California at $1.98T**

![Largest state flow: Texas to Texas at $2.58T, then California to California at $1.98T](screenshots/p4_state_heatmap_closeup.png)

**2012 to 2017: value +4.80% ($665.14bn), tonnage +10.35%, ton miles +4.97%**

![2012 to 2017: value +4.80% ($665.14bn), tonnage +10.35%, ton miles +4.97%](screenshots/p5_comparison_kpis_closeup.png)

**By mode: truck and rail +71.9%, parcel +25.4%, rail down 48.9%**

![By mode: truck and rail +71.9%, parcel +25.4%, rail down 48.9%](screenshots/p5_mode_change_charts_closeup.png)

**Exports are 7.8% of value ($2.20T); hazmat 14.2%; temperature controlled 12.5%**

![Exports are 7.8% of value ($2.20T); hazmat 14.2%; temperature controlled 12.5%](screenshots/p6_export_hazmat_temp_kpis_closeup.png)

**Shipment level detail: largest group is 2012 Texas gasoline, jet fuel and ethanol by for hire truck, $182.30bn**

![Shipment level detail: largest group is 2012 Texas gasoline, jet fuel and ethanol by for hire truck, $182.30bn](screenshots/p7_records_table_closeup.png)

**12 validation checks computed from the loaded data: 10,526,184 rows, zero null weight factors**

![12 validation checks computed from the loaded data: 10,526,184 rows, zero null weight factors](screenshots/p8_qc_checks_closeup.png)

**Motion: KPI cards counting up as the page builds**

![Motion: KPI cards counting up as the page builds](screenshots/anim_p1_cards_building.png)

**Motion: mode donuts sweeping in**

![Motion: mode donuts sweeping in](screenshots/anim_p2_donuts_sweeping.png)

**Motion: spotlight callout on the 2012 to 2017 comparison**

![Motion: spotlight callout on the 2012 to 2017 comparison](screenshots/anim_p5_spotlight_callout.png)

**Outro: Built in Power BI**

![Outro: Built in Power BI](screenshots/outro_card.png)

## Full page screenshots

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
