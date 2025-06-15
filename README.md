import logging
import sys
import time
from binance.client import Client
from binance.enums import *
from binance.exceptions import BinanceAPIException

# Configure logging
logging.basicConfig(filename='trading_bot.log', level=logging.INFO,
                    format='%(asctime)s - %(levelname)s - %(message)s')

class BasicBot:
    def __init__(self, api_key, api_secret, testnet=True):
        if testnet:
            self.base_url = 'https://testnet.binancefuture.com'
        else:
            self.base_url = 'https://fapi.binance.com'

        self.client = Client(api_key, api_secret)
        self.client.FUTURES_URL = self.base_url

    def place_order(self, symbol, side, order_type, quantity, price=None):
        try:
            if order_type == ORDER_TYPE_MARKET:
                order = self.client.futures_create_order(
                    symbol=symbol,
                    side=side,
                    type=ORDER_TYPE_MARKET,
                    quantity=quantity
                )
            elif order_type == ORDER_TYPE_LIMIT:
                order = self.client.futures_create_order(
                    symbol=symbol,
                    side=side,
                    type=ORDER_TYPE_LIMIT,
                    timeInForce=TIME_IN_FORCE_GTC,
                    quantity=quantity,
                    price=price
                )
            else:
                raise ValueError("Unsupported order type")

            logging.info(f"Order placed: {order}")
            return order

        except BinanceAPIException as e:
            logging.error(f"Binance API Exception: {e}")
            return None
        except Exception as e:
            logging.error(f"General Exception: {e}")
            return None


def main():
    api_key = input("Enter your Binance API Key: ")
    api_secret = input("Enter your Binance API Secret: ")
    bot = BasicBot(api_key, api_secret)

    symbol = input("Enter trading symbol (e.g., BTCUSDT): ").upper()
    side = input("Buy or Sell: ").upper()
    order_type = input("Order type (MARKET/LIMIT): ").upper()
    quantity = float(input("Enter quantity: "))

    price = None
    if order_type == 'LIMIT':
        price = input("Enter limit price: ")

    order = bot.place_order(symbol=symbol, side=side, order_type=order_type, quantity=quantity, price=price)

    if order:
        print("Order executed successfully:")
        print(order)
    else:
        print("Order failed. Check logs for details.")


if __name__ == '__main__':
    main()
