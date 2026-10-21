# Data

All three inputs are public and small, so they are committed here.

| File | Contents | Source |
|---|---|---|
| `df.csv` | Daily WTI front-month futures close (`WTI`), US Dollar Index (`DXY`), CBOE VIX (`VIX`), WTI futures volume (`Volume`), 2006-01-03 → 2026-04-09 | Yahoo Finance via `yfinance` (`CL=F`, `DX-Y.NYB`, `^VIX`) |
| `WTI_spot_price.csv` | WTI Cushing spot price (`DCOILWTICO`) | [FRED: DCOILWTICO](https://fred.stlouisfed.org/series/DCOILWTICO) |
| `stocks.xlsx` | Weekly U.S. ending stocks of crude oil excluding SPR (thousand barrels), 1982 → 2026 | [EIA: WCESTUS1](https://www.eia.gov/dnav/pet/hist/LeafHandler.ashx?n=PET&s=WCESTUS1&f=W) |

Known data quirks, handled in the notebook:
- The futures settled at a negative price on 2020-04-20. Returns are computed only on positive prices.
- Seven days show zero futures volume. These are set to missing before computing the volume ratio.
- EIA stocks are dated by the week-ending Friday but published the following Wednesday. The notebook shifts them by
  +5 days before joining.
