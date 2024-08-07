import requests
url = "https://www.api.exness.com"
headers = {
    "Authorization": "Bearer YOUR_ACCESS_TOKEN"
}

response = requests.get(url, headers=headers)
data = response.json()
buy_orders = sum(1 for trade in data if trade['side'] == 'buy')
sell_orders = sum(1 for trade in data if trade['side'] == 'sell')
total_orders = buy_orders + sell_orders

buy_percentage = (buy_orders / total_orders) * 100
sell_percentage = (sell_orders / total_orders) * 100

print(f"Buy: {buy_percentage}%, Sell: {sell_percentage}%")
