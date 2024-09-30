# Monitor your stock of choice

## Overview
This Python script monitors the stock price of a company (in this case, Tesla Inc.) and sends news updates to a specified phone number via Twilio when the stock's closing price changes significantly. It fetches stock data from Alpha Vantage's API, retrieves news articles related to the company from the News API, and then sends the relevant information using the Twilio API.

## Prerequisites
Before running the script, ensure you have the following:
- A valid Alpha Vantage API key for accessing stock data.
- A valid News API key for retrieving relevant news articles.
- Twilio account credentials (Twilio SID and Auth Token) to send SMS messages.
  
## Setup
1. Install the required libraries
```bash
pip install opencv-python mediapipe numpy playsound
```
2. Insert your API keys and Twilio credentials:
- STOCK_API_KEY: Your Alpha Vantage API key.
- NEWS_API_KEY: Your News API key.
- TWILIO_SID: Your Twilio Account SID.
- TWILIO_AUTH_TOKEN: Your Twilio Authentication Token.
- Phone numbers (from_ and to) for sending and receiving messages.
  
## Functionality
1. **Stock Data Retrieval:**
   - Fetches the daily stock prices of Tesla Inc. (TSLA) from Alpha Vantage.
   - Retrieves the closing stock prices for the last two days (yesterday and the day before).
2. **Stock Price Comparison:**
   - Computes the difference and percentage change between the two closing prices.
   - Depending on the magnitude of the percentage change, it decides whether to fetch and send news updates.
3. **News Retrieval**
   - If there is any significant price change, the script retrieves three latest news articles related to Tesla Inc. from News API.
4. **Sending SMS via Twilio:**
   - The script formats and sends the news headlines along with a brief description via Twilio SMS to a designated phone number.

## Code Sections
- **Stock Data:** Fetches stock prices from Alpha Vantage and calculates the percentage difference.
- **News Fetching:** Retrieves Tesla news from the News API if the stock price change exceeds a certain threshold.
- **Twilio SMS:** Sends formatted news articles as SMS messages using Twilio.
  
## How to Run
1. Set up your API keys and Twilio Credentials in the script.
2. Run the script
```bash
python stock_news_alert.py
```
3. Upon execution, if the stock price difference is significant, you will receive SMS notifications with Tesla-related news.

## Future Enhancements
- Add functionality to monitor other stocks dynamically.
- Implement a more customizable threshold for stock price changes.
- Schedule the script to run daily using cron jobs or task schedulers.
