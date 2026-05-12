# Flow Visualizer

A static web page for visualizing SF Bay tidal flow data.

## Usage

Serve the directory with any HTTP server (required for CSV loading):

```
python3 -m http.server 8080
```

Then open `http://localhost:8080` in a browser.

## Data

To add new tide data source:

* locate station: https://tidesandcurrents.noaa.gov/tide_predictions.html
* On station page follow link to Annual Published Tid Tables
* Select 24hr time format and TXT (tide) or CVS (current) format
* Move downloaded file into data directory
* Ask claude to add it for you ;)

To add new solar data source:

* Vist: https://aa.usno.navy.mil/data/RS_OneYear
* download sunrise/sunset data first
* download civil twilight as a separate file

## Features

- Multiple stations displayed simultaneously on one chart
- Checkboxes to show/hide each station
- Line color = station, point color = event type (ebb/flood/slack)
- Datetime range picker with quick-select buttons (1–30 days)
- Defaults to current time → 24 hours ahead

## Stations

| ID | Name | Location | Depth |
|----|------|----------|-------|
| SFB1203 | 0.46 nm E of SFB1203 | 37.8201° N 122.4730° W | 30 ft |
| SFB1204 | Alcatraz Island, SW of SFB1204 | 37.8143° N 122.4320° W | 2 ft |
| SFB1204 | Alcatraz Island, SW of SFB1204 | 37.8143° N 122.4320° W | 21 ft |
| SFB1204 | Alcatraz Island, SW of SFB1204 | 37.8143° N 122.4320° W | 57 ft |
| SFB1332 | Sacramento River Light 14 | 38.0772° N 121.7639° W | 3 ft |
| 9415339 | Marshall, Tomales Bay | 38.1617° N 122.8930° W | — |

## Data Format

CSV files in `data/` named `[station_id]_[depth]_Annual_[year].csv`:

```
Date_Time (LST_LDT), Event, Speed (knots)
2026-01-01 01:27, ebb,-0.9
2026-01-01 03:38, slack,-
2026-01-01 07:09, flood,2.7
```

To add a station, append an entry to the `STATIONS` array in `index.html`.
