# Trade
# 📈 Binance Futures Trading Bot (Testnet)

A simplified Python trading bot to place **Market** and **Limit** orders on the **Binance Futures Testnet** using the official Binance API. Designed for beginners who want to learn algorithmic trading and automation with clean, structured Python code.

---

## ⚙️ Features

- ✅ Connects securely to Binance **Futures Testnet**
- ✅ Place **Market** and **Limit** orders
- ✅ Supports both **Buy** and **Sell** trades
- ✅ Validates user input from command-line interface (CLI)
- ✅ Logs all API requests, responses, and errors
- ✅ Clear structure for reusability and easy extension

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/TradeBot.git
cd TradeBot
2. Set Up a Virtual Environment (Recommended)
python -m venv venv
source venv/bin/activate  # For Windows: venv\Scripts\activate
3. Install Requirements
pip install -r requirements.txt
🔑 Binance Testnet API Setup

Go to Binance Futures Testnet
Create an account or log in
Generate:
API Key
Secret Key
Enable Futures access for your API keys
Use this testnet base URL in your code:

https://testnet.binancefuture.com
🧾 Sample Usage

Run your bot using:

python trade_bot.py
You'll be prompted to enter:

API Key and Secret
Trading Symbol (e.g., BTCUSDT)
Order Type (MARKET / LIMIT)
Order Side (BUY / SELL)
Quantity
Price (for LIMIT orders only)
🧰 Project Structure

.
├── trade_bot.py          # Main Python script
├── requirements.txt      # Python dependencies
├── trading_bot.log       # Log file for trade history & errors
└── README.md             # This guide
📦 Requirements

python-binance==1.0.17
aiohttp
cryptography
cchardet
Install with:

pip install -r requirements.txt
📝 Logging

All API interactions and errors are logged in:

trading_bot.log
You can check this file to review trade history or diagnose issues.

📌 Future Improvements

 Add support for Stop-Limit, OCO orders
 Integrate Telegram/email alerts
 Build a basic UI using Streamlit or Flask
 Add backtesting support using historical data
👨‍💻 Author

Made with ❤️ by Shivam Mehta
📍 Gurugram, India
🔗 https://www.linkedin.com/in/shivam-mehta-815920318/
