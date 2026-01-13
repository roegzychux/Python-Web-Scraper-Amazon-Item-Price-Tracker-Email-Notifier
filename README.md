# Amazon Item Price Tracker & Email Notifier

## Overview
This project is an automated Python script designed to track the price of an Item, PS5 DualSense Wireless Controller on Amazon. It solves the problem of manually checking for price drops by scraping real-time data, logging it for analysis, and sending instant email alerts when the price falls within a desired budget.

## Key Features
* **Web Scraping:** Utilizes BeautifulSoup and Requests to parse live product data from Amazon.
* **Automated Price Calculation:** Extracts the item price and shipping fee, cleans the data, and calculates the total landed cost in NGN.
* **CSV Data Logging:** Automatically appends every price check to a CSV file (Amazon_store_PS5_price_update.csv) with timestamps, allowing for historical price tracking.
* **Email Alerts:** Uses smtplib to send an automated email notification via Gmail when the total price drops below a set target.
* **Continuous Monitoring:** The script runs on a loop (checking every 30 minutes) until a deal is found.

## Tech Stack
* **Language:** Python 3.12+
* **Libraries:**
    * BeautifulSoup4 (HTML Parsing)
    * Requests (HTTP Requests)
    * Pandas (Data Manipulation & Viewing)
    * smtplib (Email Automation)
    * datetime & time (Scheduling & Timestamping)

## Project Structure
* `AMAZON PS5 WEBSCRAPER PRICE UPDATE.ipynb`: Main script containing the logic.
* `Amazon_store_PS5_price_update.csv`: Generated data log.
* `Email Alert.png`: Screenshot of Price Alert Email.
* `README.md`: Project documentation.

## Configuration & Setup
To run this project on your local machine, follow these steps:

### 1. User-Agent Setup
Amazon blocks requests that look like bots. You must update the `headers` dictionary in the script with your own User-Agent.
1. Search for "what is my user agent" in your browser.
2. Copy the string.
3. Paste it into the `headers` section of the code.

### 2. Email Credentials
This script uses `smtplib` to send emails. For security:
1. If using Gmail, enable 2-Step Verification.
2. Generate an **App Password** (Google Account > Security > App Passwords).
3. Replace the credentials in the `send_email()` function:

    server.login('your_email@gmail.com', 'your_generated_app_password')

### 3. Set Target Price
Modify the `target_price` variable to your budget limit.

    target_price = 175000  # Script notifies you if price is below this

## Sample Output

### CSV Log Example
Every time the script runs, it updates the CSV file as shown below:

| Product | Item Price (NGN) | Shipping Fee (NGN) | Total Price (NGN) | Time | Date |
| :--- | :--- | :--- | :--- | :--- | :--- |
| PlayStation DualSense... | 104,146.00 | 68,164.43 | 172,310.43 | 02:38 | 2026-01-13 |
| PlayStation DualSense... | 104,146.00 | 68,164.43 | 172,310.43 | 03:08 | 2026-01-13 |

### Email Alert Example
**Subject:** PlayStation DualSense Wireless Controller Price Update

Dear User,
This is an automated alert to inform you that the price for your tracked item has dropped.

**Product:** PlayStation DualSense Wireless Controller
**New Price:** NGN 172,310.43

[Link to Amazon Product]

## Disclaimer
This tool is for educational purposes only. Web scraping logic relies on the specific HTML structure of the website, which may change over time. Always respect the website's robots.txt file and Terms of Service.
