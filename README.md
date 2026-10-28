# demo-datasets

Public datasets used in demos and tutorials, organised by dataset. Every file can be fetched directly from its raw URL, with no login.

Raw URL form: `https://raw.githubusercontent.com/edoardo-orsi-lab/demo-datasets/main/<path>`

## NYC taxi (`nyc-taxi/`)

Yellow taxi trips for January 2024, plus small lookup and rule tables. Details in [nyc-taxi/README.md](nyc-taxi/README.md).

- Source: [NYC Taxi & Limousine Commission (TLC) Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).
- Terms: published by the City of New York as open data; use is subject to the [NYC Open Data terms of use](https://www.nyc.gov/home/terms-of-use.page). This repository adds a row id and derived lookup tables; it is not affiliated with or endorsed by the TLC.

| File | Raw URL |
|---|---|
| `nyc-taxi/trips/yellow_tripdata_2024-01_ride_id.parquet` | https://raw.githubusercontent.com/edoardo-orsi-lab/demo-datasets/main/nyc-taxi/trips/yellow_tripdata_2024-01_ride_id.parquet |
| `nyc-taxi/lookups/zones.csv` | https://raw.githubusercontent.com/edoardo-orsi-lab/demo-datasets/main/nyc-taxi/lookups/zones.csv |
| `nyc-taxi/lookups/payments.csv` | https://raw.githubusercontent.com/edoardo-orsi-lab/demo-datasets/main/nyc-taxi/lookups/payments.csv |
| `nyc-taxi/lookups/vendors.csv` | https://raw.githubusercontent.com/edoardo-orsi-lab/demo-datasets/main/nyc-taxi/lookups/vendors.csv |
| `nyc-taxi/lookups/time_rules.csv` | https://raw.githubusercontent.com/edoardo-orsi-lab/demo-datasets/main/nyc-taxi/lookups/time_rules.csv |
| `nyc-taxi/lookups/zone_rules.csv` | https://raw.githubusercontent.com/edoardo-orsi-lab/demo-datasets/main/nyc-taxi/lookups/zone_rules.csv |
