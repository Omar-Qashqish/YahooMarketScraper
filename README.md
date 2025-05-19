# 📈 Yahoo Finance Market Summary Uploader

This project is a Python-based automation script that fetches **live market data from Yahoo Finance** (across all major financial tabs like US, Europe, Asia, Commodities, Currencies, Cryptocurrencies, and Rates), and inserts the data directly into a **SQL Server database** for further processing or integration with company dashboards.

---

## 🔧 What the Script Does

- Scrapes **ticker summaries** from [https://finance.yahoo.com](https://finance.yahoo.com) using the official Yahoo Finance API (`quote?symbols=...`).
- Supports **multiple financial tabs** including:
  - US
  - EUROPE
  - ASIA
  - COMMODITIES
  - CURRENCIES
  - CRYPTOCURRENCIES
  - RATES
- **Keeps the data exactly as it appears** on the Yahoo Finance UI (no transformation).
- Inserts the collected data into a SQL Server table named `MarketSummary`.

---

## ✅ Sample Output in SQL Server (Live Data Snapshot)

Below is a full preview of what the uploaded data will look like inside the `MarketSummary` SQL Server table.  
The values are dynamically fetched from Yahoo Finance and stored **as-is** with no modifications.

| Tab              | Name                               | Price   | Change   | Percent Change |
|------------------|------------------------------------|---------|----------|----------------|
| US               | S&P Futures                        | [Live]  | [Live]   | [Live]         |
| US               | Dow Futures                        | [Live]  | [Live]   | [Live]         |
| US               | Nasdaq Futures                     | [Live]  | [Live]   | [Live]         |
| US               | Russell 2000 Futures               | [Live]  | [Live]   | [Live]         |
| US               | VIX                                | [Live]  | [Live]   | [Live]         |
| US               | Gold                               | [Live]  | [Live]   | [Live]         |
| EUROPE           | FTSE 100                           | [Live]  | [Live]   | [Live]         |
| EUROPE           | CAC 40                             | [Live]  | [Live]   | [Live]         |
| EUROPE           | DAX P                              | [Live]  | [Live]   | [Live]         |
| EUROPE           | Euronext 100 Index                 | [Live]  | [Live]   | [Live]         |
| EUROPE           | EUR/USD                            | [Live]  | [Live]   | [Live]         |
| EUROPE           | USD/GBP                            | [Live]  | [Live]   | [Live]         |
| ASIA             | SSE Composite Index                | [Live]  | [Live]   | [Live]         |
| ASIA             | Nikkei 225                         | [Live]  | [Live]   | [Live]         |
| ASIA             | Hang Seng                          | [Live]  | [Live]   | [Live]         |
| ASIA             | S&P/ASX 200 [XJO]                  | [Live]  | [Live]   | [Live]         |
| ASIA             | The Asia Dow (USD)                 | [Live]  | [Live]   | [Live]         |
| ASIA             | USD/JPY                            | [Live]  | [Live]   | [Live]         |
| RATES            | 13-Wk Bond                         | [Live]  | [Live]   | [Live]         |
| RATES            | 5-Yr Bond                          | [Live]  | [Live]   | [Live]         |
| RATES            | 10-Yr Bond                         | [Live]  | [Live]   | [Live]         |
| RATES            | 30-Yr Bond                         | [Live]  | [Live]   | [Live]         |
| RATES            | 2 Yr Yld Futures                   | [Live]  | [Live]   | [Live]         |
| RATES            | 10 Yr T-Note Futures               | [Live]  | [Live]   | [Live]         |
| COMMODITIES      | Crude Oil                          | [Live]  | [Live]   | [Live]         |
| COMMODITIES      | Gold                               | [Live]  | [Live]   | [Live]         |
| COMMODITIES      | Silver                             | [Live]  | [Live]   | [Live]         |
| COMMODITIES      | Copper Jul 25                      | [Live]  | [Live]   | [Live]         |
| COMMODITIES      | Natural Gas Jun 25                 | [Live]  | [Live]   | [Live]         |
| COMMODITIES      | Brent Crude Oil Last Day Financ    | [Live]  | [Live]   | [Live]         |
| CURRENCIES       | EUR/USD                            | [Live]  | [Live]   | [Live]         |
| CURRENCIES       | USD/JPY                            | [Live]  | [Live]   | [Live]         |
| CURRENCIES       | USD/GBP                            | [Live]  | [Live]   | [Live]         |
| CURRENCIES       | USD/AUD                            | [Live]  | [Live]   | [Live]         |
| CURRENCIES       | USD/CAD                            | [Live]  | [Live]   | [Live]         |
| CURRENCIES       | USD/MXN                            | [Live]  | [Live]   | [Live]         |
| CRYPTOCURRENCIES | Bitcoin USD                        | [Live]  | [Live]   | [Live]         |
| CRYPTOCURRENCIES | XRP USD                            | [Live]  | [Live]   | [Live]         |
| CRYPTOCURRENCIES | Ethereum USD                       | [Live]  | [Live]   | [Live]         |
| CRYPTOCURRENCIES | Tether USDt USD                    | [Live]  | [Live]   | [Live]         |
| CRYPTOCURRENCIES | BNB USD                            | [Live]  | [Live]   | [Live]         |
| CRYPTOCURRENCIES | Solana USD                         | [Live]  | [Live]   | [Live]         |

> ℹ️ All values are updated automatically each time the script runs. The formatting and text are preserved as received from Yahoo Finance.



---

## 🧾 Table Schema (`MarketSummary`)

| Column         | Type         | Description                                      |
|----------------|--------------|--------------------------------------------------|
| `Id`           | INT          | Auto-incremented primary key                     |
| `Tab`          | NVARCHAR(50) | The financial tab/category (e.g., US, Asia)      |
| `Name`         | NVARCHAR(100)| Market name or symbol                            |
| `Price`        | NVARCHAR(50) | Market price (stored as text, e.g., `"5,898.50"`)|
| `Change`       | NVARCHAR(50) | Absolute change (e.g., `"-77.00"` or `"+2.57"`)  |
| `PercentChange`| NVARCHAR(50) | Percentage change (e.g., `"(-1.29%)"`)           |
| `CreatedAt`    | DATETIME     | Timestamp when the row was inserted              |

---

## ⚙️ Technologies Used

- **Python**  
- **pandas**  
- **requests**  
- **BeautifulSoup (bs4)**
- **Selenium**
- **pyodbc** 
- **SQL Server 2022**  
- **ODBC Driver 17 for SQL Server**  
---
> ✅ All data is preserved as-is from Yahoo Finance with original formatting (strings with commas, signs, and percent symbols).

