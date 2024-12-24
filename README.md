# Blockchain_Assn; Live Cryptocurrency Data Analysis Project
Project Overview
This project aims to fetch and analyze live cryptocurrency data using Python and Excel. The data is continuously updated to provide real-time information on the top 50 cryptocurrencies by market capitalization. The analysis includes identifying the top 5 cryptocurrencies by market cap, calculating the average price of the top 50 cryptocurrencies, and analyzing the highest and lowest 24-hour percentage price changes.

Tools and Technologies Used

Python: Used for fetching and analyzing live data from the CoinGecko API.

Excel: Utilized for displaying and continuously updating the data.

xlwings: A Python library used to interact with Excel for live data updates.

CoinGecko API: Source of the live cryptocurrency data.

not i upload this file in mine github depostry saction now , its time to cover readme saction , so is this saction i think its right to explain about the project ,that i complete this python, excel to , so write a readme saction and explain brefly hows i cover this assinment
Sure, writing a README section is a great way to explain your project on GitHub. Here's a sample README that you can use for your project:

Live Cryptocurrency Data Analysis Project
Project Overview
This project aims to fetch and analyze live cryptocurrency data using Python and Excel. The data is continuously updated to provide real-time information on the top 50 cryptocurrencies by market capitalization. The analysis includes identifying the top 5 cryptocurrencies by market cap, calculating the average price of the top 50 cryptocurrencies, and analyzing the highest and lowest 24-hour percentage price changes.
................................................................................
Tools and Technologies Used
Python: Used for fetching and analyzing live data from the CoinGecko API.

Excel: Utilized for displaying and continuously updating the data.

xlwings: A Python library used to interact with Excel for live data updates.

CoinGecko API: Source of the live cryptocurrency data.

1. Fetch Live Data
API Used: CoinGecko API


Data Analysis part.............................................................
Identifying the Top 5 Cryptocurrencies by Market Cap:

Sorted the data by market capitalization and extracted the top 5 cryptocurrencies.

Calculating the Average Price:

Used Excel formulas to calculate the average price of the top 50 cryptocurrencies.

Analyzing 24-hour Percentage Price Change:

Determined the highest and lowest 24-hour percentage price changes among the top 50 cryptocurrencies.
................................................................................................................



Fetching Data c


import requests

# CoinGecko API URL
url = "https://api.coingecko.com/api/v3/coins/markets"

# Parameters for the API request
params = {
    'vs_currency': 'usd',
    'order': 'market_cap_desc',
    'per_page': 50,
    'page': 1,
    'sparkline': False
}

# Make the request to the API
response = requests.get(url, params=params)

# Check if the request was successful
if response.status_code == 200:
    data = response.json()

    # Display the required fields
    print(f"{'Name':<20} {'Symbol':<10} {'Price (USD)':<15} {'Market Cap':<20} {'24h Volume':<20} {'24h Change (%)':<15}")
    print("="*100)
    for coin in data:
        name = coin.get('name', 'N/A')
        symbol = coin.get('symbol', 'N/A')
        current_price = coin.get('current_price', 'N/A')
        market_cap = coin.get('market_cap', 'N/A')
        volume_24h = coin.get('total_volume', 'N/A')
        price_change_24h = coin.get('price_change_percentage_24h', 'N/A')

        print(f"{name:<20} {symbol:<10} {current_price:<15} {market_cap:<20} {volume_24h:<20} {price_change_24h:<15}")
else:
    print("Failed to fetch data from CoinGecko API.")




