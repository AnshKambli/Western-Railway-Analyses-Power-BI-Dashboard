# Mumbai Western Railway Intelligence Dashboard

A 7-page Power BI dashboard that analyses crowding, passenger demand, train operations, and fare enforcement on the Mumbai Western Railway line, and ranks stations by operational risk.

> **Data note:** [FILL: state the truth here. Example: "All data is simulated, modeled on Western line operations. No real Western Railway data is used, and this project has no affiliation with Indian Railways."]

## Business Questions

1. Which services and time bands run over rated capacity, and how bad is it?
2. When does demand peak, and is train supply matched to it?
3. Which stations combine heavy footfall, crowding, and fare-evasion risk?
4. Where is enforcement concentrated, and where is revenue being lost?

## Key Findings

<!-- Pull these from your Findings page. Use real numbers. -->
- [FILL: e.g. Slow services run at X% of rated capacity during peak vs Y% off-peak]
- [FILL: e.g. Peak hours carry X% of passengers but only Y% of scheduled trains]
- [FILL: e.g. Top 3 risk stations: A, B, C, driven mainly by crowding / ticketless travel]
- [FILL: recommendation, e.g. add N peak slow services between 8-10 AM or shift enforcement to station X]

## Dashboard Pages

| Page | What it answers | Main visuals |
|---|---|---|
| **Executive** | Headline health of the network | KPI cards (passengers, trains/day, peak share, segments over capacity, revenue), demand trend, class mix, summary table |
| **Train & Operation** | How supply is scheduled | Peak vs off-peak trains/hour, trains per hour, service mix (slow vs fast), train schedule |
| **Station & Crowd** | Where crowding happens | Load factor heatmap by station and hour, overcrowded segments, direction and service-type slicers |
| **Passenger Demand** | Who travels, when, and where | Boarding-hour demand, ticket-type and class split, pass-holder share, avg trip km, board/alight table |
| **Fines & Violations** | Enforcement and fare evasion | Violations by type, time band, day type, ticketless %, violations per 1,000 passengers |
| **Peak Hours** | Peak vs off-peak behavior | Passengers by hour, load factor by service type and period |
| **Findings** | Decisions | Station risk score table and written findings |

## Data Model

Star-style model with `stations` as the central dimension.

| Table | Grain / purpose |
|---|---|
| `stations` | Station dimension |
| `trains` | One row per train: service type, departure hour, destination |
| `train_stops` | Train-to-station stop schedule |
| `train_frequency` | Trains per hour by service |
| `segment_occupancy` | Load per track segment, hour, direction, service type |
| `passenger_ticket_demand` | Boarding/alighting station, hour, class, ticket type, trip km, passenger count, fare, revenue |
| `season_pass_sales` | Season pass sales |
| `fines_violations` | Fine records: type, amount, hour, station |
| `_Measures` | All DAX measures (kept in a dedicated table) |
| `Text` | Dynamic text measures that drive the commentary on each page |

[FILL: add a screenshot of the model view as `screenshots/model.png`]

## Key DAX Measures

**Demand:** Total Passengers, Alighting Passengers, Passengers per Train, Avg Trip km, Pass Holder Share, Peak Share
**Revenue:** Ticket Revenue, Total Revenue
**Capacity:** Avg Load Factor, Max Load Factor, % Overcrowded, Overcrowded Segments, Slow Avg Load
**Operations:** Trains Scheduled, Peak Trains/Hour, Off-Peak Trains/Hour, Peak Ratio, Avg Stops per Train, Slow Stops per Train
**Enforcement:** Total Violations, Violations per 1000, Ticketless %
**Composite:** Risk Score (combines crowding, enforcement, footfall, and revenue per station)

[FILL: one sentence on how Risk Score is calculated, e.g. weights and normalization. A reviewer will ask.]

## Design Decisions

- Measures live in one `_Measures` table, with no implicit measures in visuals.
- Consistent page layout with navigation buttons on every page.
- Dynamic text measures keep the written commentary in sync with slicer selections.
- [FILL: any validation you did, e.g. reconciled total passengers against the source CSV.]

## Tech Stack

Power BI Desktop, DAX, Power Query, [FILL: Python/SQL if used to generate or prepare the data]

## How to Open

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
2. Open `TrainAnalyses.pbix`.
3. [FILL: note whether the data is embedded or needs the CSVs in `/data`.]

## Repo Structure

```
├── TrainAnalyses.pbix
├── README.md
├── screenshots/
├── data/            # [FILL: if sharing data]
└── report.pdf       # [FILL: PDF export of all pages]
```

## Limitations

- [FILL: e.g. Data is simulated, so findings illustrate method, not real-world conditions.]
- [FILL: e.g. Single-day or single-period snapshot, no trend over months.]
- Risk Score weights are judgment-based and not validated against real incident data.

## Author

**Ansh Kambli** | [GitHub](https://github.com/AnshKambli) | [LinkedIn](https://linkedin.com/in/ansh-kambli-3598b1251) | [Portfolio](https://anshkambli.github.io/Portfolio)
