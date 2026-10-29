## Dataset Overview

The dataset covers international maritime logistics and terminal efficiency from January 2021 to December 2024. It consists of three dimension tables and one fact table, with approximately 15,000 cargo movement records.

### Tables

| Table | Description | Estimated Rows |
|---|---|---:|
| `dim_terminal` | Terminal details, geographic locations, and regional hubs. | 50 |
| `dim_time` | Date attributes, including fiscal year, quarter, month, week, and shift. | 5,000 |
| `dim_vessel` | Vessel details, including category and build year. | 1,000 |
| `fact_cargo_movements` | Cargo movement records, container counts, movement durations, and route geometry. | 15,000 |

### Key Columns

| Column | Table | Description |
|---|---|---|
| `date_id` | `dim_time` | Date associated with the record. |
| `regional_hub` | `dim_terminal` | Regional classification: EMEA, APAC, or AMER. |
| `terminal_id` | `dim_terminal` | Unique terminal identifier. |
| `vessel_id` | `dim_vessel` | Unique vessel identifier. |
| `vessel_category` | `dim_vessel` | Vessel category: Tanker, Cargo, or Passenger. |
| `container_count` | `fact_cargo_movements` | Number of containers moved. |
| `move_duration` | `fact_cargo_movements` | Cargo movement duration in hours. |
| `movement_id` | `fact_cargo_movements` | Unique cargo movement identifier. |

### Relationships

- `fact_cargo_movements.vessel_id` → `dim_vessel.vessel_id`
- `fact_cargo_movements.terminal_id` → `dim_terminal.terminal_id`

Each cargo movement record represents one cargo movement and is associated with a vessel and a terminal.

### Data Scope

- **Period:** January 2021 to December 2024
- **Currency:** USD, as specified in the source dictionary; no currency-denominated measure is listed in the provided columns.
- **Regional hubs:** EMEA, APAC, and AMER.
