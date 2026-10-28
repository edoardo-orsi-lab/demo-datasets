# NYC taxi, January 2024

## Source

NYC Taxi & Limousine Commission (TLC) [Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page), yellow taxi trips for January 2024 (`yellow_tripdata_2024-01.parquet`), and the TLC [taxi zone lookup](https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv). Code meanings follow the TLC [yellow trip data dictionary](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf). Published as open data by the City of New York; see the [NYC Open Data terms of use](https://www.nyc.gov/home/terms-of-use.page).

## Trips

`trips/yellow_tripdata_2024-01_ride_id.parquet`: 2,964,624 rows, about 62 MB.

What we changed: added a `ride_id` column (int64), numbered 1..N in the original file order. Every other column and row is unchanged.

| Column | Type |
|---|---|
| ride_id | int64 |
| VendorID | int32 |
| tpep_pickup_datetime | timestamp[ns] |
| tpep_dropoff_datetime | timestamp[ns] |
| passenger_count | int64 |
| trip_distance | double |
| RatecodeID | int64 |
| store_and_fwd_flag | string |
| PULocationID | int32 |
| DOLocationID | int32 |
| payment_type | int64 |
| fare_amount | double |
| extra | double |
| mta_tax | double |
| tip_amount | double |
| tolls_amount | double |
| improvement_surcharge | double |
| total_amount | double |
| congestion_surcharge | double |
| Airport_fee | double |

## Lookups

All CSV, UTF-8, with a header row.

- `lookups/zones.csv`: TLC taxi zone lookup, unchanged apart from LF line endings. Columns `LocationID, Borough, Zone, service_zone`; 265 rows. Joins to `PULocationID` / `DOLocationID`.
- `lookups/payments.csv`: payment type codes. Columns `payment_type, payment`; 7 rows. Joins to `payment_type`.
- `lookups/vendors.csv`: technology vendor codes. Columns `VendorID, vendor`; 4 rows. Joins to `VendorID`.
- `lookups/time_rules.csv`: regex rules that cut `tpep_pickup_datetime` into a `day` (YYYY-MM-DD) and an `hour` (HH:00).
- `lookups/zone_rules.csv`: regex rules that give every zone a unique, readable name (the two Corona zones and the three island zones share a name in the source, so their id is appended; `N/A` values get a label).

Rule tables share the columns `description, execution_order, source_cols, pattern, replacement, target_col, overwrite_if_populated`. Rules run in `execution_order`; `source_cols` lists the input columns (comma-separated, concatenated before matching); `replacement` uses `${n}` for capture groups.
