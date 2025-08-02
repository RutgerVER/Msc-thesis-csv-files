# Market Data Repository

This repository contains high-quality market data files organized into two main directories:

- **bbo/** — Best-Bid-Offer (BBO) snapshots for key indices
- **ohlc/** — Open-High-Low-Close (OHLC) bars for indices and options.

---

## 📁 bbo/

The `bbo/` folder holds mid-quote snapshots (best bid and best ask) sampled at high frequency.

| File Name                 | Description                           |
| ------------------------- | ------------------------------------- |
| `SPX_OPT_2025-01-01.csv`  | S&P 500 Index BBO data (tick-level)   |
| `SPXW_OPT_2025-01-01.csv` | S&P 500 Weekly Options Index BBO data |
| `VIX_OPT_2025-01-01.csv`  | CBOE Volatility Index (VIX) BBO data  |

Each CSV has the following columns:

| Column      | Type    | Description                                |
| ----------- | ------- | ------------------------------------------ |
| `timestamp` | string  | ISO 8601 timestamp (UTC)                   |
| `bid_px`    | float   | Best bid price                             |
| `bid_size`  | integer | Size at best bid                           |
| `ask_px`    | float   | Best ask price                             |
| `ask_size`  | integer | Size at best ask                           |
| `symbol`    | string  | Instrument ticker (e.g. `SPX-contract_id`) |

---

## 📁 ohlc/

The `ohlc/` folder contains bar-aggregated data for both indices and options as well as the SOFR (overnight financing rate), at multiple resolutions.

### 1. Daily OHLC for Indices & Options

| File Name                 | Symbol          | Bar Size | Description                         |
| ------------------------- | --------------- | -------- | ----------------------------------- | ---------------------------- | --- |
| `SPX_OPT_2025-01-01.csv`  | SPX             | 1 day    | Daily OHLC bars for SPX options     |
| `SPXW_OPT_2025-01-01.csv` | SPXW            | 1 day    | Daily OHLC bars for SPX Weekly Opt. |
| <!--                      | `VIX_daily.csv` | VIX      | 1 day                               | Daily OHLC bars for CBOE VIX | --> |

Each daily CSV includes:

| Column   | Type    | Description                                |
| -------- | ------- | ------------------------------------------ |
| `date`   | string  | Trading date (YYYY-MM-DD)                  |
| `open`   | float   | Opening price                              |
| `high`   | float   | Highest price                              |
| `low`    | float   | Lowest price                               |
| `close`  | float   | Closing price                              |
| `volume` | integer | Total traded volume                        |
| `symbol` | string  | Instrument ticker (e.g. `SPX-contract_id`) |

### 2. 1-Second OHLC for SPY

| File Name            | Symbol | Bar Size | Description                 |
| -------------------- | ------ | -------- | --------------------------- |
| `SPY_2025-01-01.csv` | SPY    | 1 second | Intraday 1-second OHLC bars |

The 1-second SPY file has these columns:

| Column      | Type    | Description                   |
| ----------- | ------- | ----------------------------- |
| `timestamp` | string  | ISO 8601 timestamp (UTC)      |
| `open`      | float   | Price at the start of the bar |
| `high`      | float   | Highest price during the bar  |
| `low`       | float   | Lowest price during the bar   |
| `close`     | float   | Price at the end of the bar   |
| `volume`    | integer | Volume traded in the bar      |

---

### 3. Daily OHLC for SOFR Futures (Jan 1 2025 – Jul 1st 2025)

| File Name                | Symbol  | Bar Size | Description                             |
| ------------------------ | ------- | -------- | --------------------------------------- |
| `SR1_FUT_2025-01-01.csv` | SR1_FUT | 1 day    | Daily OHLC bars for 1-Month SOFR Future |
| `SR3_FUT_2025-01-01.csv` | SR3_FUT | 1 day    | Daily OHLC bars for 3-Month SOFR Future |

Each SOFR futures CSV includes:

| Column   | Type    | Description                        |
| -------- | ------- | ---------------------------------- |
| `date`   | string  | Trading date (YYYY-MM-DD)          |
| `symbol` | string  | Instrument ticker (e.g. `SR1_FUT`) |
| `open`   | float   | Opening price                      |
| `high`   | float   | Highest price                      |
| `low`    | float   | Lowest price                       |
| `close`  | float   | Closing price                      |
| `volume` | integer | Total traded volume                |

## Usage

1. **Clone the repo**
   ```bash
   git clone https://github.com/your-org/market-data.git
   cd market-data
   ```
