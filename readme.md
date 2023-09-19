#Crypto-Search-Application

The CryptoView website is designed to provide users with up-to-date information on cryptocurrencies. It includes a homepage with a brief description of the platform, a navigation bar, and a section for displaying the top cryptocurrencies. Users can also access a search page for more detailed cryptocurrency information.


#index.html

1. **getCurrentConversionRate()**:
    - This function fetches the current conversion rate of Bitcoin (BTC) to Indian Rupees (INR) from the CoinGecko API.
    - It sends a GET request to the API endpoint `"https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=inr"`.
    - Once the data is fetched, it is converted to JSON format using `await data.json()`.
    - Finally, it calls the `loadTopCoins()` function and passes the fetched data as an argument.

2. **loadTopCoins(data)**:
    - This function takes the data containing the BTC to INR conversion rate as an argument.
    - It fetches a list of top trending cryptocurrencies from the CoinGecko API using a GET request to `"https://api.coingecko.com/api/v3/search/trending"`.
    - After fetching the trending coin data, it calls the `renderTopCoinsOnScreen()` function and passes both the BTC to INR conversion rate and the trending coin data.

3. **renderTopCoinsOnScreen(conversionRate, topCoins)**:
    - This function takes in the BTC to INR conversion rate and the trending coin data as arguments.
    - It iterates through the list of trending coins using a `for` loop.
    - For each coin, it extracts relevant data such as the coin's logo, name, and symbol.
    - It calculates the coin's price in INR based on its BTC price and the provided conversion rate.
    - Finally, it calls the `createCard()` function and passes the logo, name, and price.

4. **createCard(logo, name, price)**:
    - This function dynamically creates an HTML card element for each cryptocurrency.
    - It constructs the card using `document.createElement()` to create elements for the coin's logo, name, and price.
    - The logo is represented as an `<img>` element, and the name and price are placed in separate `<h2>` and `<p>` elements, respectively.
    - The card is then appended to the `TopCoinsDiv` element in the HTML, making it visible on the webpage.

5. **window.onload**:
    - This is an event listener that ensures the `getCurrentConversionRate()` function is called only after the entire HTML document has loaded.
    - When the webpage finishes loading, it triggers the `getCurrentConversionRate()` function, initiating the data fetching and rendering process.
