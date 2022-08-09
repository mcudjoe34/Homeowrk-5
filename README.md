# Homeowrk-5
{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 8,
   "id": "f47f9f73-8671-4901-be78-e06b58992aa5",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Initial imports\n",
    "import os\n",
    "import requests\n",
    "import pandas as pd\n",
    "import alpaca_trade_api as tradeapi\n",
    "from MCForecastTools import MCSimulation\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "id": "32b95e2a-fe68-41f0-afa9-bdf073d21034",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Set Alpaca API key and secret\n",
    "alpaca_api_key = \"AKW5KZCS45SAHRVTAVKH\"\n",
    "alpaca_secret_key = \"XUuRGqHC9Jtb9RxGtv6B3wacmUFVIxw11NAW5a6u\"\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "id": "17c8cc40-48e2-46b2-b08e-d85a8300d49b",
   "metadata": {
    "jupyter": {
     "source_hidden": true
    },
    "tags": []
   },
   "outputs": [],
   "source": [
    "# Crypto API URLs\n",
    "btc_url = \"https://api.alternative.me/v2/ticker/Bitcoin/?convert=USD\"\n",
    "eth_url = \"https://api.alternative.me/v2/ticker/Ethereum/?convert=USD\""
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "id": "49cf17c2-dfc5-4b1e-bc6e-c9eb741971e2",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Create the Alpaca API object\n",
    "alpaca = tradeapi.REST(\n",
    "    alpaca_api_key,\n",
    "    alpaca_secret_key,\n",
    "    api_version=\"v2\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "id": "e4d46f80-624b-4ca1-8482-5ac6d5c59937",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Alpaca Key type: <class 'str'>\n",
      "Alpaca Secret Key type: <class 'str'>\n"
     ]
    }
   ],
   "source": [
    "# Verify that Alpaca key and secret were correctly loaded\n",
    "print(f\"Alpaca Key type: {type(alpaca_api_key)}\")\n",
    "print(f\"Alpaca Secret Key type: {type(alpaca_secret_key)}\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "7b6f08fc-f73b-453b-b879-3cc96a330800",
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "id": "12436093-2920-4fa9-aefe-c9d848206bbc",
   "metadata": {
    "tags": []
   },
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'my_btc' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [7]\u001b[0m, in \u001b[0;36m<cell line: 15>\u001b[1;34m()\u001b[0m\n\u001b[0;32m     12\u001b[0m eth_price \u001b[38;5;241m=\u001b[39m eth_response[\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mdata\u001b[39m\u001b[38;5;124m'\u001b[39m][\u001b[38;5;124m'\u001b[39m\u001b[38;5;124m1027\u001b[39m\u001b[38;5;124m'\u001b[39m][\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mquotes\u001b[39m\u001b[38;5;124m'\u001b[39m][\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mUSD\u001b[39m\u001b[38;5;124m'\u001b[39m][\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mprice\u001b[39m\u001b[38;5;124m'\u001b[39m]\n\u001b[0;32m     14\u001b[0m \u001b[38;5;66;03m# Compute current value of my crpto\u001b[39;00m\n\u001b[1;32m---> 15\u001b[0m my_btc_value \u001b[38;5;241m=\u001b[39m \u001b[43mmy_btc\u001b[49m \u001b[38;5;241m*\u001b[39m btc_price\n\u001b[0;32m     16\u001b[0m my_eth_value \u001b[38;5;241m=\u001b[39m my_eth \u001b[38;5;241m*\u001b[39m eth_price\n\u001b[0;32m     18\u001b[0m \u001b[38;5;66;03m# Print current crypto wallet balance\u001b[39;00m\n",
      "\u001b[1;31mNameError\u001b[0m: name 'my_btc' is not defined"
     ]
    }
   ],
   "source": [
    "# Set current amount of shares\n",
    "my_BTC = 1.3\n",
    "my_ETH = 5.2\n",
    "\n",
    "# Fetch current BTC price\n",
    "btc_response = requests.get(btc_url).json()\n",
    "btc_price = btc_response['data']['1']['quotes']['USD']['price']\n",
    "\n",
    "\n",
    "# Fetch current ETH price\n",
    "eth_response = requests.get(eth_url).json()\n",
    "eth_price = eth_response['data']['1027']['quotes']['USD']['price']\n",
    "\n",
    "# Compute current value of my crpto\n",
    "my_btc_value = my_btc * btc_price\n",
    "my_eth_value = my_eth * eth_price\n",
    "\n",
    "# Print current crypto wallet balance\n",
    "print(f\"The current value of your {my_btc} BTC is ${my_btc_value:0.2f}\")\n",
    "print(f\"The current value of your {my_eth} ETH is ${my_eth_value:0.2f}\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 49,
   "id": "8c9b4440-12f5-48f6-b7f7-caf3b6fc3304",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Set current amount of shares\n",
    "my_agg = 200\n",
    "my_spy = 50"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "id": "961fe78a-26c5-4e5f-986e-8a309f766545",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Set Alpaca API key and secret\n",
    "alpaca_api_key = \"AKW5KZCS45SAHRVTAVKH\"\n",
    "alpaca_secret_key = \"XUuRGqHC9Jtb9RxGtv6B3wacmUFVIxw11NAW5a6u\"\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "id": "65c20346-60ce-4e3d-9c24-f78f4525911a",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Set start and end datetimes as Today\n",
    "start_date = pd.Timestamp(\"2022-08-08\", tz=\"America/New_York\").isoformat()\n",
    "end_date = pd.Timestamp(\"2022-08-08\", tz=\"America/New_York\").isoformat()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "id": "41339ca9-c632-4397-82e2-00dac034559c",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Set the tickers\n",
    "tickers = ['AGG', 'SPY']\n",
    "\n",
    "# Set timeframe to \"1Day\" for Alpaca API\n",
    "timeframe = \"1Day\"\n",
    "\n",
    "# Get current closing prices for SPY and AGG\n",
    "df_investments = alpaca.get_bars(\n",
    "    tickers,\n",
    "    timeframe,\n",
    "    start = today\n",
    ").df\n",
    "\n",
    "df_investments"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "id": "354f4fc7-83ed-455b-9845-4eb6f87dfab6",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Alpaca Key type: <class 'NoneType'>\n",
      "Alpaca Secret Key type: <class 'NoneType'>\n"
     ]
    }
   ],
   "source": [
    "# Separate ticker data\n",
    "AGG = df_investments[df_investments['symbol']=='AGG'].drop('symbol', axis=1)\n",
    "SPY = df_investments[df_investments['symbol']=='SPY'].drop('symbol', axis=1)\n",
    "\n",
    "# Concatenate the ticker DataFrames\n",
    "df_investments = pd.concat([AGG, SPY],axis=1, keys=['AGG','SPY'])\n",
    "\n",
    "# Preview DataFrame\n",
    "df_investments.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "id": "ff79d25e-023e-4cec-bcfd-df0247be7ca0",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'tradeapi' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [25]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Create the Alpaca API object\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m alpaca \u001b[38;5;241m=\u001b[39m \u001b[43mtradeapi\u001b[49m\u001b[38;5;241m.\u001b[39mREST(\n\u001b[0;32m      3\u001b[0m     alpaca_api_key,\n\u001b[0;32m      4\u001b[0m     alpaca_secret_key,\n\u001b[0;32m      5\u001b[0m     api_version\u001b[38;5;241m=\u001b[39m\u001b[38;5;124m\"\u001b[39m\u001b[38;5;124mv2\u001b[39m\u001b[38;5;124m\"\u001b[39m)\n",
      "\u001b[1;31mNameError\u001b[0m: name 'tradeapi' is not defined"
     ]
    }
   ],
   "source": [
    "# Find CLose Prices of Crypto\n",
    "agg_close_price = float(df_investments['AGG']['close'][-1])\n",
    "spy_close_price = float(df_investments['SPY']['close'][-1])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "id": "d316c1f9-59be-48d7-8cf4-1cb4acc43bb5",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'alpaca' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [26]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Get current price data for AGG and SPY\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m df_portfolio \u001b[38;5;241m=\u001b[39m \u001b[43malpaca\u001b[49m\u001b[38;5;241m.\u001b[39mget_bars(\n\u001b[0;32m      3\u001b[0m     tickers,\n\u001b[0;32m      4\u001b[0m     timeframe,\n\u001b[0;32m      5\u001b[0m     start \u001b[38;5;241m=\u001b[39m today,\n\u001b[0;32m      6\u001b[0m     end \u001b[38;5;241m=\u001b[39m today\n\u001b[0;32m      7\u001b[0m )\u001b[38;5;241m.\u001b[39mdf\n\u001b[0;32m      9\u001b[0m \u001b[38;5;66;03m# Reorganize the DataFrame\u001b[39;00m\n\u001b[0;32m     10\u001b[0m \u001b[38;5;66;03m# Separate ticker data\u001b[39;00m\n\u001b[0;32m     11\u001b[0m AAPL \u001b[38;5;241m=\u001b[39m df_portfolio[df_portfolio[\u001b[38;5;124m'\u001b[39m\u001b[38;5;124msymbol\u001b[39m\u001b[38;5;124m'\u001b[39m]\u001b[38;5;241m==\u001b[39m\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mAGG\u001b[39m\u001b[38;5;124m'\u001b[39m]\u001b[38;5;241m.\u001b[39mdrop(\u001b[38;5;124m'\u001b[39m\u001b[38;5;124msymbol\u001b[39m\u001b[38;5;124m'\u001b[39m, axis\u001b[38;5;241m=\u001b[39m\u001b[38;5;241m1\u001b[39m)\n",
      "\u001b[1;31mNameError\u001b[0m: name 'alpaca' is not defined"
     ]
    }
   ],
   "source": [
    "# Get current price data for AGG and SPY\n",
    "df_portfolio = alpaca.get_bars(\n",
    "    tickers,\n",
    "    timeframe,\n",
    "    start = today,\n",
    "    end = today\n",
    ").df\n",
    "\n",
    "# Reorganize the DataFrame\n",
    "# Separate ticker data\n",
    "AAPL = df_portfolio[df_portfolio['symbol']=='AGG'].drop('symbol', axis=1)\n",
    "MSFT = df_portfolio[df_portfolio['symbol']=='SPY'].drop('symbol', axis=1)\n",
    "\n",
    "# Concatenate the ticker DataFrames\n",
    "df_portfolio = pd.concat([AGG, SPY],axis=1, keys=['AGG','SPY'])\n",
    "\n",
    "# Display sample data\n",
    "df_portfolio"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 31,
   "id": "f30f0a9d-95f3-43f5-9b6f-083d9c8d3e67",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Format start and end dates as ISO format for one year period\n",
    "start = pd.Timestamp(\"2021-08-08\", tz=\"America/New_York\").isoformat()\n",
    "end = pd.Timestamp(\"2021-08-08\", tz=\"America/New_York\").isoformat()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "id": "78c9ccd2-ca89-4e24-a5d3-c0676df2e21c",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'df_portfolio' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [32]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Fetch the current closing prices from the DataFrame\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m msft_price \u001b[38;5;241m=\u001b[39m \u001b[38;5;28mfloat\u001b[39m(\u001b[43mdf_portfolio\u001b[49m[\u001b[38;5;124m\"\u001b[39m\u001b[38;5;124mAGG\u001b[39m\u001b[38;5;124m\"\u001b[39m][\u001b[38;5;124m\"\u001b[39m\u001b[38;5;124mclose\u001b[39m\u001b[38;5;124m\"\u001b[39m])\n\u001b[0;32m      3\u001b[0m aapl_price \u001b[38;5;241m=\u001b[39m \u001b[38;5;28mfloat\u001b[39m(df_portfolio[\u001b[38;5;124m\"\u001b[39m\u001b[38;5;124mSPY\u001b[39m\u001b[38;5;124m\"\u001b[39m][\u001b[38;5;124m\"\u001b[39m\u001b[38;5;124mclose\u001b[39m\u001b[38;5;124m\"\u001b[39m])\n",
      "\u001b[1;31mNameError\u001b[0m: name 'df_portfolio' is not defined"
     ]
    }
   ],
   "source": [
    "# Fetch the current closing prices from the DataFrame\n",
    "msft_price = float(df_portfolio[\"AGG\"][\"close\"])\n",
    "aapl_price = float(df_portfolio[\"SPY\"][\"close\"])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 35,
   "id": "a3d3acd0-78e8-498e-adb2-c71494e4a12a",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'msft_price' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [35]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Compute the current value of shares\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m msft_value \u001b[38;5;241m=\u001b[39m \u001b[43mmsft_price\u001b[49m \u001b[38;5;241m*\u001b[39m df_shares\u001b[38;5;241m.\u001b[39mloc[\u001b[38;5;124m\"\u001b[39m\u001b[38;5;124mAGG\u001b[39m\u001b[38;5;124m\"\u001b[39m][\u001b[38;5;124m\"\u001b[39m\u001b[38;5;124mshares\u001b[39m\u001b[38;5;124m\"\u001b[39m]\n\u001b[0;32m      3\u001b[0m aapl_value \u001b[38;5;241m=\u001b[39m aapl_price \u001b[38;5;241m*\u001b[39m df_shares\u001b[38;5;241m.\u001b[39mloc[\u001b[38;5;124m\"\u001b[39m\u001b[38;5;124mSPY\u001b[39m\u001b[38;5;124m\"\u001b[39m][\u001b[38;5;124m\"\u001b[39m\u001b[38;5;124mshares\u001b[39m\u001b[38;5;124m\"\u001b[39m]\n\u001b[0;32m      4\u001b[0m \u001b[38;5;66;03m# Print current value of shares\u001b[39;00m\n",
      "\u001b[1;31mNameError\u001b[0m: name 'msft_price' is not defined"
     ]
    }
   ],
   "source": [
    "# Compute the current value of shares\n",
    "msft_value = msft_price * df_shares.loc[\"AGG\"][\"shares\"]\n",
    "aapl_value = aapl_price * df_shares.loc[\"SPY\"][\"shares\"]\n",
    "# Print current value of shares\n",
    "print(f\"The current value of your {my_spy} SPY shares is ${my_spy_value:0.2f}\")\n",
    "print(f\"The current value of your {my_agg} AGG shares is ${my_agg_value:0.2f}\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "e75dfd4f-802f-4b07-a853-61c8a5f4f41f",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Set monthly income\n",
    "monthly_income = 12000\n",
    "\n",
    "# Combine financial assets data\n",
    "savings_data = [ my_btc_value + my_eth_value, my_spy_value + my_agg_value,]\n",
    "\n",
    "# Create savings Df\n",
    "df_savings = pd.DataFrame(savings_data, columns=['amount'], index=['crypto', 'shares'])\n",
    "\n",
    "# Display savings DataFrame\n",
    "display(df_savings)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "id": "d62387ef-2da2-487a-ad91-ee2c690bfe6b",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'df_savings' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [12]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Plot savings pie chart\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m \u001b[43mdf_savings\u001b[49m\u001b[38;5;241m.\u001b[39mplot\u001b[38;5;241m.\u001b[39mpie(y\u001b[38;5;241m=\u001b[39m\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mamount\u001b[39m\u001b[38;5;124m'\u001b[39m)\n",
      "\u001b[1;31mNameError\u001b[0m: name 'df_savings' is not defined"
     ]
    }
   ],
   "source": [
    "# Plot savings pie chart\n",
    "df_savings.plot.pie(y='amount')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "id": "3e6b2648-557d-46c4-b145-503d6d721b9c",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'monthly_income' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [13]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Set ideal emergency fund\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m emergency_fund \u001b[38;5;241m=\u001b[39m \u001b[43mmonthly_income\u001b[49m \u001b[38;5;241m*\u001b[39m \u001b[38;5;241m3\u001b[39m\n\u001b[0;32m      4\u001b[0m \u001b[38;5;66;03m# Calculate total amount of savings\u001b[39;00m\n\u001b[0;32m      5\u001b[0m total_savings \u001b[38;5;241m=\u001b[39m \u001b[38;5;28mfloat\u001b[39m(df_savings\u001b[38;5;241m.\u001b[39msum())\n",
      "\u001b[1;31mNameError\u001b[0m: name 'monthly_income' is not defined"
     ]
    }
   ],
   "source": [
    "# Set ideal emergency fund\n",
    "emergency_fund = monthly_income * 3\n",
    "\n",
    "# Calculate total amount of savings\n",
    "total_savings = float(df_savings.sum())\n",
    "\n",
    "# Validate saving health\n",
    "if total_savings > emergency_fund:\n",
    "    print('Congratulations! You have enough money in your emergency fund.')\n",
    "elif total_savings == emergency_fund:\n",
    "    print('Great, You have saved three times your monthly expenses! Keep pushing to increase your savings.')\n",
    "else:\n",
    "    print(f'You are ${(emergency_fund - total_savings):0.2f} away from your emergency fund goal, continue saving between 10% and 20% of your monthly income to reach your goal.')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "id": "332beaf0-c6f6-468e-aee4-10367da53375",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Set start and end dates of five years back from today.\n",
    "# Sample results may vary from the solution based on the time frame chosen\n",
    "start_date = pd.Timestamp('2016-08-08', tz='America/New_York').isoformat()\n",
    "end_date = pd.Timestamp('2022-08-08', tz='America/New_York').isoformat()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "id": "7c5d2f6c-406b-4565-82c7-0a4e97dd67aa",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'tickers' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [15]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Get 5 years' worth of historical data for SPY and AGG\u001b[39;00m\n\u001b[0;32m      2\u001b[0m df_stock_data \u001b[38;5;241m=\u001b[39m alpaca\u001b[38;5;241m.\u001b[39mget_bars(\n\u001b[1;32m----> 3\u001b[0m     \u001b[43mtickers\u001b[49m,\n\u001b[0;32m      4\u001b[0m     timeframe,\n\u001b[0;32m      5\u001b[0m     start\u001b[38;5;241m=\u001b[39mstart_date,\n\u001b[0;32m      6\u001b[0m     end\u001b[38;5;241m=\u001b[39mend_date\n\u001b[0;32m      7\u001b[0m )\u001b[38;5;241m.\u001b[39md\n",
      "\u001b[1;31mNameError\u001b[0m: name 'tickers' is not defined"
     ]
    }
   ],
   "source": [
    "# Get 5 years' worth of historical data for SPY and AGG\n",
    "df_stock_data = alpaca.get_bars(\n",
    "    tickers,\n",
    "    timeframe,\n",
    "    start=start_date,\n",
    "    end=end_date\n",
    ").d"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "id": "b5485048-441e-47ca-8b0f-a9f026956a27",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'df_stock_data' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [16]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Separate ticker data\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m AGG \u001b[38;5;241m=\u001b[39m \u001b[43mdf_stock_data\u001b[49m[df_stock_data[\u001b[38;5;124m'\u001b[39m\u001b[38;5;124msymbol\u001b[39m\u001b[38;5;124m'\u001b[39m]\u001b[38;5;241m==\u001b[39m\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mAGG\u001b[39m\u001b[38;5;124m'\u001b[39m]\u001b[38;5;241m.\u001b[39mdrop(\u001b[38;5;124m'\u001b[39m\u001b[38;5;124msymbol\u001b[39m\u001b[38;5;124m'\u001b[39m, axis\u001b[38;5;241m=\u001b[39m\u001b[38;5;241m1\u001b[39m)\n\u001b[0;32m      3\u001b[0m SPY \u001b[38;5;241m=\u001b[39m df_stock_data[df_stock_data[\u001b[38;5;124m'\u001b[39m\u001b[38;5;124msymbol\u001b[39m\u001b[38;5;124m'\u001b[39m]\u001b[38;5;241m==\u001b[39m\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mSPY\u001b[39m\u001b[38;5;124m'\u001b[39m]\u001b[38;5;241m.\u001b[39mdrop(\u001b[38;5;124m'\u001b[39m\u001b[38;5;124msymbol\u001b[39m\u001b[38;5;124m'\u001b[39m, axis\u001b[38;5;241m=\u001b[39m\u001b[38;5;241m1\u001b[39m)\n",
      "\u001b[1;31mNameError\u001b[0m: name 'df_stock_data' is not defined"
     ]
    }
   ],
   "source": [
    "# Separate ticker data\n",
    "AGG = df_stock_data[df_stock_data['symbol']=='AGG'].drop('symbol', axis=1)\n",
    "SPY = df_stock_data[df_stock_data['symbol']=='SPY'].drop('symbol', axis=1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "id": "0c2a0501-1f76-4290-8d0d-52e7b859de3a",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'AGG' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [17]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Concatenate the ticker DataFrames\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m df_stock_data \u001b[38;5;241m=\u001b[39m pd\u001b[38;5;241m.\u001b[39mconcat([\u001b[43mAGG\u001b[49m, SPY],axis\u001b[38;5;241m=\u001b[39m\u001b[38;5;241m1\u001b[39m, keys\u001b[38;5;241m=\u001b[39m[\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mAGG\u001b[39m\u001b[38;5;124m'\u001b[39m,\u001b[38;5;124m'\u001b[39m\u001b[38;5;124mSPY\u001b[39m\u001b[38;5;124m'\u001b[39m])\n\u001b[0;32m      4\u001b[0m \u001b[38;5;66;03m# Display sample data\u001b[39;00m\n\u001b[0;32m      5\u001b[0m df_stock_data\u001b[38;5;241m.\u001b[39mhead()\n",
      "\u001b[1;31mNameError\u001b[0m: name 'AGG' is not defined"
     ]
    }
   ],
   "source": [
    "# Concatenate the ticker DataFrames\n",
    "df_stock_data = pd.concat([AGG, SPY],axis=1, keys=['AGG','SPY'])\n",
    "\n",
    "# Display sample data\n",
    "df_stock_data.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "id": "4cae2fac-d7e1-4c86-9be9-a05566b25444",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'df_stock_data' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [18]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Configuring a Monte Carlo simulation to forecast 30 years cumulative returns\u001b[39;00m\n\u001b[0;32m      2\u001b[0m MC_thirty_year \u001b[38;5;241m=\u001b[39m MCSimulation(\n\u001b[1;32m----> 3\u001b[0m     portfolio_data \u001b[38;5;241m=\u001b[39m \u001b[43mdf_stock_data\u001b[49m,\n\u001b[0;32m      4\u001b[0m     weights \u001b[38;5;241m=\u001b[39m [\u001b[38;5;241m.40\u001b[39m,\u001b[38;5;241m.60\u001b[39m],\n\u001b[0;32m      5\u001b[0m     num_simulation \u001b[38;5;241m=\u001b[39m \u001b[38;5;241m500\u001b[39m,\n\u001b[0;32m      6\u001b[0m     num_trading_days \u001b[38;5;241m=\u001b[39m \u001b[38;5;241m252\u001b[39m \u001b[38;5;241m*\u001b[39m \u001b[38;5;241m30\u001b[39m\n\u001b[0;32m      7\u001b[0m )\n",
      "\u001b[1;31mNameError\u001b[0m: name 'df_stock_data' is not defined"
     ]
    }
   ],
   "source": [
    "# Configuring a Monte Carlo simulation to forecast 30 years cumulative returns\n",
    "MC_thirty_year = MCSimulation(\n",
    "    portfolio_data = df_stock_data,\n",
    "    weights = [.40,.60],\n",
    "    num_simulation = 500,\n",
    "    num_trading_days = 252 * 30\n",
    ")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "id": "21e34427-dac8-4e5b-81d8-ccdb079308a9",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'MC_thirty_year' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [19]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Printing the simulation input data\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m \u001b[43mMC_thirty_year\u001b[49m\u001b[38;5;241m.\u001b[39mportfolio_data\u001b[38;5;241m.\u001b[39mhead()\n",
      "\u001b[1;31mNameError\u001b[0m: name 'MC_thirty_year' is not defined"
     ]
    }
   ],
   "source": [
    "# Printing the simulation input data\n",
    "MC_thirty_year.portfolio_data.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "id": "58f2e284-8c19-4c41-a7e3-2356b3136fa1",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'MC_thirty_year' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [20]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Plot simulation outcomes\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m line_plot \u001b[38;5;241m=\u001b[39m \u001b[43mMC_thirty_year\u001b[49m\u001b[38;5;241m.\u001b[39mplot_simulation()\n",
      "\u001b[1;31mNameError\u001b[0m: name 'MC_thirty_year' is not defined"
     ]
    }
   ],
   "source": [
    "# Plot simulation outcomes\n",
    "line_plot = MC_thirty_year.plot_simulation()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "id": "1dab8748-83ce-4bff-b150-3bc796c52277",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'MC_thirty_year' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [21]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Fetch summary statistics from the Monte Carlo simulation results\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m table \u001b[38;5;241m=\u001b[39m \u001b[43mMC_thirty_year\u001b[49m\u001b[38;5;241m.\u001b[39msummarize_cumulative_return()\n\u001b[0;32m      4\u001b[0m \u001b[38;5;66;03m# Print summary statistics\u001b[39;00m\n\u001b[0;32m      5\u001b[0m \u001b[38;5;28mprint\u001b[39m(table)\n",
      "\u001b[1;31mNameError\u001b[0m: name 'MC_thirty_year' is not defined"
     ]
    }
   ],
   "source": [
    "# Fetch summary statistics from the Monte Carlo simulation results\n",
    "table = MC_thirty_year.summarize_cumulative_return()\n",
    "\n",
    "# Print summary statistics\n",
    "print(table)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "id": "490a1bb3-03bf-4376-8680-2f2db7448a62",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'df_savings' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [22]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Set initial investment\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m initial_investment \u001b[38;5;241m=\u001b[39m \u001b[38;5;28mfloat\u001b[39m(\u001b[43mdf_savings\u001b[49m\u001b[38;5;241m.\u001b[39msum())\n\u001b[0;32m      4\u001b[0m \u001b[38;5;66;03m# Use the lower and upper `95%` confidence intervals to calculate the range of the possible outcomes of our $20,000\u001b[39;00m\n\u001b[0;32m      5\u001b[0m ci_lower \u001b[38;5;241m=\u001b[39m \u001b[38;5;28mround\u001b[39m(tbl[\u001b[38;5;241m8\u001b[39m] \u001b[38;5;241m*\u001b[39m initial_investment,\u001b[38;5;241m2\u001b[39m)\n",
      "\u001b[1;31mNameError\u001b[0m: name 'df_savings' is not defined"
     ]
    }
   ],
   "source": [
    "# Set initial investment\n",
    "initial_investment = float(df_savings.sum())\n",
    "\n",
    "# Use the lower and upper `95%` confidence intervals to calculate the range of the possible outcomes of our $20,000\n",
    "ci_lower = round(tbl[8] * initial_investment,2)\n",
    "ci_upper = round(tbl[9] * initial_investment,2)\n",
    "\n",
    "# Print results\n",
    "print(f'There is a 95% chance that an initial investment of ${initial_investment} in the portfolio'\n",
    "      f' over the next 30 years will end within in the range of'\n",
    "      f' ${ci_lower} and ${ci_upper}')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "id": "b8a19489-7c25-4338-acf4-0c7db2fcd24c",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'df_stock_data' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [23]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Configuring a Monte Carlo simulation to forecast 5 years cumulative returns\u001b[39;00m\n\u001b[0;32m      2\u001b[0m MC_five_year \u001b[38;5;241m=\u001b[39m MCSimulation(\n\u001b[1;32m----> 3\u001b[0m     portfolio_data \u001b[38;5;241m=\u001b[39m \u001b[43mdf_stock_data\u001b[49m,\n\u001b[0;32m      4\u001b[0m     weights \u001b[38;5;241m=\u001b[39m [\u001b[38;5;241m.80\u001b[39m,\u001b[38;5;241m.20\u001b[39m],\n\u001b[0;32m      5\u001b[0m     num_simulation \u001b[38;5;241m=\u001b[39m \u001b[38;5;241m500\u001b[39m,\n\u001b[0;32m      6\u001b[0m     num_trading_days \u001b[38;5;241m=\u001b[39m \u001b[38;5;241m252\u001b[39m \u001b[38;5;241m*\u001b[39m \u001b[38;5;241m5\u001b[39m\n\u001b[0;32m      7\u001b[0m )\n",
      "\u001b[1;31mNameError\u001b[0m: name 'df_stock_data' is not defined"
     ]
    }
   ],
   "source": [
    "# Configuring a Monte Carlo simulation to forecast 5 years cumulative returns\n",
    "MC_five_year = MCSimulation(\n",
    "    portfolio_data = df_stock_data,\n",
    "    weights = [.80,.20],\n",
    "    num_simulation = 500,\n",
    "    num_trading_days = 252 * 5\n",
    ")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "id": "6e1eee67-779a-425a-8220-b228f309dd2f",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'MC_five_year' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [24]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Running a Monte Carlo simulation to forecast 5 years cumulative returns\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m \u001b[43mMC_five_year\u001b[49m\u001b[38;5;241m.\u001b[39mcalc_cumulative_return()\n",
      "\u001b[1;31mNameError\u001b[0m: name 'MC_five_year' is not defined"
     ]
    }
   ],
   "source": [
    "# Running a Monte Carlo simulation to forecast 5 years cumulative returns\n",
    "MC_five_year.calc_cumulative_return()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "id": "4f06c6d8-8072-4944-b918-5da03c0b5153",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'MC_five_year' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [25]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Plot simulation outcomes\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m line_plot_five \u001b[38;5;241m=\u001b[39m \u001b[43mMC_five_year\u001b[49m\u001b[38;5;241m.\u001b[39mplot_simulation()\n",
      "\u001b[1;31mNameError\u001b[0m: name 'MC_five_year' is not defined"
     ]
    }
   ],
   "source": [
    "# Plot simulation outcomes\n",
    "line_plot_five = MC_five_year.plot_simulation()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "id": "f7138dad-4bf0-4e25-946f-0954f9898fae",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'MC_five_year' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [26]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Plot probability distribution and confidence intervals\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m dist_plot_five \u001b[38;5;241m=\u001b[39m \u001b[43mMC_five_year\u001b[49m\u001b[38;5;241m.\u001b[39mplot_distribution()\n",
      "\u001b[1;31mNameError\u001b[0m: name 'MC_five_year' is not defined"
     ]
    }
   ],
   "source": [
    "# Plot probability distribution and confidence intervals\n",
    "dist_plot_five = MC_five_year.plot_distribution()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "id": "06a8d0e6-f064-4bd8-9435-1fda56fb43ad",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'tbl_five' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [27]\u001b[0m, in \u001b[0;36m<cell line: 5>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      2\u001b[0m initial_investment \u001b[38;5;241m=\u001b[39m \u001b[38;5;241m20000\u001b[39m \u001b[38;5;241m*\u001b[39m \u001b[38;5;241m3\u001b[39m\n\u001b[0;32m      4\u001b[0m \u001b[38;5;66;03m# Use the lower and upper `95%` confidence intervals to calculate the range of the possible outcomes of our $60,000\u001b[39;00m\n\u001b[1;32m----> 5\u001b[0m ci_lower_five \u001b[38;5;241m=\u001b[39m \u001b[38;5;28mround\u001b[39m(\u001b[43mtbl_five\u001b[49m[\u001b[38;5;241m8\u001b[39m] \u001b[38;5;241m*\u001b[39m initial_investment,\u001b[38;5;241m2\u001b[39m)\n\u001b[0;32m      6\u001b[0m ci_upper_five \u001b[38;5;241m=\u001b[39m \u001b[38;5;28mround\u001b[39m(tbl_five[\u001b[38;5;241m9\u001b[39m] \u001b[38;5;241m*\u001b[39m initial_investment,\u001b[38;5;241m2\u001b[39m)\n\u001b[0;32m      8\u001b[0m \u001b[38;5;66;03m# Print results\u001b[39;00m\n",
      "\u001b[1;31mNameError\u001b[0m: name 'tbl_five' is not defined"
     ]
    }
   ],
   "source": [
    "# Set initial investment\n",
    "initial_investment = 20000 * 3\n",
    "\n",
    "# Use the lower and upper `95%` confidence intervals to calculate the range of the possible outcomes of our $60,000\n",
    "ci_lower_five = round(tbl_five[8] * initial_investment,2)\n",
    "ci_upper_five = round(tbl_five[9] * initial_investment,2)\n",
    "\n",
    "# Print results\n",
    "print(f'There is a 95% chance that an initial investment of ${initial_investment} in the portfolio'\n",
    "      f' over the next 5 years will end within in the range of'\n",
    "      f' ${ci_lower_five} and ${ci_upper_five}')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "id": "90a96a07-2e93-4d71-a858-016eafa37937",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'df_stock_data' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [28]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Configuring a Monte Carlo simulation to forecast 10 years cumulative returns\u001b[39;00m\n\u001b[0;32m      2\u001b[0m MC_ten_year \u001b[38;5;241m=\u001b[39m MCSimulation(\n\u001b[1;32m----> 3\u001b[0m     portfolio_data \u001b[38;5;241m=\u001b[39m \u001b[43mdf_stock_data\u001b[49m,\n\u001b[0;32m      4\u001b[0m     weights \u001b[38;5;241m=\u001b[39m [\u001b[38;5;241m.80\u001b[39m,\u001b[38;5;241m.20\u001b[39m],\n\u001b[0;32m      5\u001b[0m     num_simulation \u001b[38;5;241m=\u001b[39m \u001b[38;5;241m500\u001b[39m,\n\u001b[0;32m      6\u001b[0m     num_trading_days \u001b[38;5;241m=\u001b[39m \u001b[38;5;241m252\u001b[39m \u001b[38;5;241m*\u001b[39m \u001b[38;5;241m10\u001b[39m\n\u001b[0;32m      7\u001b[0m )\n",
      "\u001b[1;31mNameError\u001b[0m: name 'df_stock_data' is not defined"
     ]
    }
   ],
   "source": [
    "# Configuring a Monte Carlo simulation to forecast 10 years cumulative returns\n",
    "MC_ten_year = MCSimulation(\n",
    "    portfolio_data = df_stock_data,\n",
    "    weights = [.80,.20],\n",
    "    num_simulation = 500,\n",
    "    num_trading_days = 252 * 10\n",
    ")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "id": "bde23b38-d3d2-4ac3-bf59-1e7fd3553967",
   "metadata": {},
   "outputs": [
    {
     "ename": "NameError",
     "evalue": "name 'MC_ten_year' is not defined",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mNameError\u001b[0m                                 Traceback (most recent call last)",
      "Input \u001b[1;32mIn [33]\u001b[0m, in \u001b[0;36m<cell line: 2>\u001b[1;34m()\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[38;5;66;03m# Plot simulation outcomes\u001b[39;00m\n\u001b[1;32m----> 2\u001b[0m line_plot_ten \u001b[38;5;241m=\u001b[39m \u001b[43mMC_ten_year\u001b[49m\u001b[38;5;241m.\u001b[39mplot_simulation()\n\u001b[0;32m      3\u001b[0m \u001b[38;5;66;03m# Plot probability distribution and confidence intervals\u001b[39;00m\n\u001b[0;32m      4\u001b[0m dist_plot_ten \u001b[38;5;241m=\u001b[39m MC_ten_year\u001b[38;5;241m.\u001b[39mplot_distribution()\n",
      "\u001b[1;31mNameError\u001b[0m: name 'MC_ten_year' is not defined"
     ]
    }
   ],
   "source": [
    "# Plot simulation outcomes\n",
    "line_plot_ten = MC_ten_year.plot_simulation()\n",
    "# Plot probability distribution and confidence intervals\n",
    "dist_plot_ten = MC_ten_year.plot_distribution()\n",
    "# Fetch summary statistics from the Monte Carlo simulation results\n",
    "tbl_ten = MC_ten_year.summarize_cumulative_return()\n",
    "\n",
    "# Print summary statistics\n",
    "print(tbl_ten)\n",
    "\n",
    "# Set initial investment\n",
    "initial_investment = 20000 * 3\n",
    "\n",
    "# Use the lower and upper `95%` confidence intervals to calculate the range of the possible outcomes of our $60,000\n",
    "ci_lower_ten = round(tbl_ten[8] * initial_investment,2)\n",
    "ci_upper_ten = round(tbl_ten[9] * initial_investment,2)\n",
    "\n",
    "# Print results\n",
    "print(f'There is a 95% chance that an initial investment of ${initial_investment} in the portfolio'\n",
    "      f' over the next 10 years will end within in the range of'\n",
    "      f' ${ci_lower_ten} and ${ci_upper_ten}')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "5a67df05-31cd-4bed-9566-5fd2c1a91b1e",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.12"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
