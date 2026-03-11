# StockTracker

A desktop application that monitors stock price indicators and generates buy/sell alerts based on technical analysis. It uses customizable trading indicators to identify potential opportunities from your watchlist, saving time on daily manual analysis.

All metrics are defined and edited based on the personal experience and observation of the author Logan Yuan.

---

## Features

- **Automated Alert Engine** - Scans your entire watchlist and flags stocks with active buy/sell signals
- **Multi-Indicator Analysis** - Combines CCI, MACD, KDJ, and 100+ TA-Lib indicators per stock
- **Customizable Thresholds** - Tune each indicator's buy/sell trigger values to match your strategy
- **Interactive Charts** - Price charts with toggleable indicator overlays (CCI, MACD, KDJ)
- **Watchlist Management** - Add and remove stock tickers on the fly
- **Extensible Indicators** - Search and add any of 100+ TA-Lib indicators with auto-generated parameter fields
- **Persistent Configuration** - All settings and alerts are saved locally between sessions
- **Background Processing** - UI stays responsive while data is being fetched and analyzed
- **Standalone Executable** - Packaged with PyInstaller for easy distribution on Windows

---

## Screenshots

The application has three main tabs:

- **Home** - Dashboard showing the "Attention" list (stocks with active alerts), signal details, price chart, and indicator overlays
- **Stocks** - Watchlist management with stock preview and chart
- **Indicators** - Configure which indicators are active, add new ones, and tune parameters and thresholds

---

## Getting Started

### Prerequisites

- Python 3.8+
- TA-Lib C library (must be installed before the Python package)

### Installation

```bash
git clone https://github.com/your-username/StockTracker.git
cd StockTracker
pip install -r requirements.txt
```

### Run

```bash
python main.py
```

### Build Standalone Executable (Windows)

```bash
pyinstaller StockTracker.spec
```

The output will be in `dist/StockTracker/`.

---

## Usage

1. **Add Stocks** - Go to the Stocks tab and enter ticker symbols (e.g. `AAPL`, `TSLA`)
2. **Configure Indicators** - Go to the Indicators tab to enable/disable indicators and adjust thresholds
3. **Run Analysis** - On the Home tab, click **Update** to fetch data and run the alert engine
4. **Review Alerts** - Stocks with signals appear in the "Attention" list:
   - Green = BUY signal
   - Red = SELL signal
   - Orange = ALERT (watch closely)
5. **Inspect Signals** - Click a stock to see the detailed signal reasons and toggle indicator charts

---

## Default Indicators

| Indicator | Description | Buy Signal | Sell Signal |
|-----------|-------------|------------|-------------|
| **CCI** | Commodity Channel Index | Value < -100 (oversold) | Value > 100 (overbought) |
| **MACD** | Moving Average Convergence Divergence | Histogram crosses above zero | Histogram crosses below zero |
| **KDJ** | Stochastic Oscillator | J-value oversold + K/D crossover | J-value overbought + K/D crossover |

Additional indicators from TA-Lib (RSI, Bollinger Bands, ATR, OBV, etc.) can be added via the Indicators tab.

---

## Project Structure

```
StockTracker/
├── main.py                        # Entry point
├── requirements.txt               # Python dependencies
├── StockTracker.spec              # PyInstaller build config
│
├── core/                          # Business logic
│   ├── data_fetcher.py            # Fetch OHLCV data from Yahoo Finance
│   ├── indicators.py              # CCI, MACD, KDJ, and TA-Lib calculations
│   └── alert_engine.py            # Alert generation engine
│
├── storage/
│   └── settings_manager.py        # JSON-based config persistence
│
├── ui/                            # GUI (CustomTkinter)
│   ├── app.py                     # Main window and navigation
│   ├── home_page.py               # Dashboard with alerts and charts
│   ├── stock_settings_page.py     # Watchlist management
│   ├── indicator_settings_page.py # Indicator configuration
│   └── theme.py                   # Color palette and styling
│
└── data/                          # Runtime data (auto-generated)
    ├── settings.json              # User configuration
    └── alerts.json                # Latest alert results
```

---

## Dependencies

| Package | Purpose |
|---------|---------|
| `customtkinter` | Modern GUI framework |
| `yfinance` | Yahoo Finance market data |
| `pandas` | Data manipulation |
| `numpy` | Numerical computations |
| `matplotlib` | Chart rendering |
| `ta-lib` | 100+ technical analysis indicators |

---

## License

Personal project by Logan Yuan. All rights reserved.
