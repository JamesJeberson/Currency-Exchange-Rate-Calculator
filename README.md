# Simple Currency Convertor


```python
# Importing the requireed libraries
import requests
import json

# Gathering the input parameters from the user
base = input("Convert from (currency code)")
curr = input("Convert to (currency code)")
quan = float(input("How much {} do you want to convert?".format(base)))

#Defining base URL
base_url = "https://cdn.jsdelivr.net/npm/@fawazahmed0/currency-api@latest"

#Constructing the URL based on the user paramenters and sending request to the server
url = base_url + "/" + "v1/currencies/" + base.lower() + ".json"
response = requests.get(url)

#Displaying error message if something went wrong
if(response.ok is False):
    print("\nError: {}".format(response.status_code))

#Displaying the result
else:
    data = response.json()
    rate = data[base.lower()][curr.lower()]
    result = quan*rate
    
    print("\n{0} {1} is equal to {2} {3}, based upon the exchange rates on {4} ".format(quan, base, result, curr, data['date']))
```
