# VoltRelay Energy — Data Analytics Hackathon

## Project Overview

VoltRelay Energy is a growing EV battery-swapping network serving electric 2W/3W riders. This project investigates why service failures are increasing despite network growth, where operational and commercial problems are concentrated, and what actions VoltRelay should prioritize.

The analysis covers **3,877,013 swap attempts** across six Indian cities and links swap events with rider, station, battery, station telemetry, support-ticket, city-context and fleet-partner data.

## Business Problem

VoltRelay is experiencing:

- Rapid growth in completed swaps and revenue
- Increasing service failures and queue abandonment
- Declining new-rider retention
- Pressure on contribution economics

The goal is to identify the major drivers, locate the highest-impact problem areas, and translate the evidence into actionable business recommendations.

## Key Findings

1. **Service availability is the largest failure driver.** `failed_no_charged_battery` represents about 58% of failures, while `abandoned_queue` represents about 30%.
2. **Failures are concentrated geographically.** Jaipur and Delhi NCR show relatively high failure rates, and the top 20 stations account for about 30% of failures.
3. **Gen1 stations show higher observed failure rates** than Gen2/Gen3 stations, supporting targeted upgrade analysis.
4. **Low charged-battery inventory is strongly associated with higher hourly failure rates**, especially during peak evening demand.
5. **Battery cohorts differ in performance.** Kyron-linked events show lower average SOH and higher battery-linked support-ticket rates than the other suppliers in the observed data.
6. **First-month service experience is associated with retention.** Riders with higher first-month failure exposure have lower next-calendar-month activity.
7. **Partner economics contain localized discount leakage.** FP-03 shows a large effective discount increase and lower realized revenue per completed swap after its amendment.

## Recommended Action Plan

### 1. Stabilize high-risk stations
Prioritize high-volume, high-failure stations, especially where Gen1 equipment and peak-hour congestion overlap.

### 2. Improve peak-hour battery availability
Forecast station-hour demand and pre-position charged batteries before the evening peak.

### 3. Upgrade high-impact Gen1 stations
Use failure rate, volume and utilization to prioritize retrofit/maintenance investment.

### 4. Introduce battery quality controls
Monitor SOH and manufacturing-lot performance; rotate, quarantine or retire weak cohorts.

### 5. Protect new riders
Create a first-30-day recovery process after repeated failures, excessive queue exposure or no-battery incidents.

### 6. Repair partner economics
Review discount-heavy partner agreements, particularly FP-03, using contribution thresholds and volume-based terms.

### 7. Expand selectively
Prioritize expansion only where demand and utilization can support the investment.

## Project Files

- `VoltRelay_Final_Analysis.ipynb` — complete analysis notebook
- `VoltRelay_Final_Report.pdf` — final report
- `VoltRelay_Final_Report.docx` — editable report
- `VoltRelay_3_Minute_Demo_Script.txt` — demo video script
- `VoltRelay_Analysis_Tables.xlsx` — supporting analysis tables

## Data Note

The raw hackathon datasets are not included in this repository because the swap-event data is very large. The analysis was performed using the complete **3,877,013-row swap-event dataset** split into eight local CSV parts, together with the other hackathon-provided datasets.

## Methodology Notes

The documented firmware timestamp issue affecting `v3.2.0` stations between March 10 and April 14, 2025 was corrected by adding 5 hours 30 minutes to affected event timestamps.

Telemetry blanks were treated as missing rather than zero. Implausible odometer/SOC values were flagged rather than silently treated as valid.

The source data does not contain a direct accounting contribution-margin field. Where economics are discussed, the analysis uses a transparent operating contribution proxy rather than presenting it as an accounting margin.

## Disclaimer

This is a synthetic hackathon dataset. Findings are intended for the hackathon scenario and should be interpreted as observational evidence rather than causal proof.
