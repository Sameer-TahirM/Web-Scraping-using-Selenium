# Daraz Web Scraper using Selenium

## Description

This project provides a powerful web scraping tool designed to collect data from the e-commerce platform Daraz.pk. Using **Selenium**, it automates browser interactions to perform two main tasks:
1.  Scraping customer reviews for a specific product.
2.  Gathering detailed information about sellers and their products based on a keyword search.

The scraper handles dynamic web pages, navigates through multiple pages, and extracts structured data into a Pandas DataFrame. Additionally, it performs sentiment analysis on the scraped reviews using **NLTK's VADER** to classify them as positive, negative, or neutral.

## How It Works

The scraper operates in two primary modes:

1.  **Product Review Scraping**:
    - Takes a specific product URL as input.
    - Navigates to the product page and scrolls down to the reviews section.
    - Iteratively clicks the "next page" button to load and scrape up to three pages of reviews.
    - Extracts the reviewer's name and the review text, cleans the text, and performs sentiment analysis using VADER.

2.  **Seller Information Scraping by Keyword**:
    - Takes a search term (e.g., "mobile covers") as input.
    - Automates a search on the Daraz homepage.
    - For each product in the search results, it navigates to the product page and then to the seller's store page.
    - It extracts comprehensive data including seller name, seller rating, followers, country, and whether the store is part of Daraz Mall.
    - It handles pagination to collect data across multiple search result pages.

## Features

- **Dynamic Web Scraping**: Built with **Selenium** to handle JavaScript-rendered content and dynamic page elements.
- **Dual Scraping Modes**: Can scrape both detailed reviews from a single product page and high-level seller data from a keyword search.
- **Sentiment Analysis**: Integrates **NLTK's VADER** to analyze the sentiment of customer reviews automatically.
- **Multi-Page Navigation**: Capable of navigating from search results to product pages, seller pages, and back.
- **Automated Pagination**: Clicks through multiple pages of search results or reviews to gather extensive data.
- **Data Cleaning & Structuring**: Cleans scraped text (e.g., removing stop words, punctuation) and organizes all data neatly into Pandas DataFrames.
- **Structured Data Extraction**: Gathers key metrics like price, ratings, number of reviews, seller location, and Daraz Mall status.

## Getting Started

Follow these steps to set up the project locally.

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/your_username/your_repo_name.git
    cd your_repo_name
    ```
2.  **Install Dependencies**:
    
    Install the libararies given at the bottom
    
3.  **Setup ChromeDriver**:
    - This project uses Selenium with Google Chrome. You need to have `chromedriver` installed.
    - Download the version that matches your Chrome browser from the [Chrome for Testing availability dashboard](https://googlechromelabs.github.io/chrome-for-testing/).
    - Make sure to update the path to your `chromedriver.exe` in the notebook:
    ```python
    path = "C:\\path\\to\\your\\chromedriver.exe"
    driver = webdriver.Chrome(path)
    ```

## Usage

1.  **Open the Jupyter Notebook**:
    - The main script is located in `Web Scraping via Selenium.ipynb`.
    - Open it in a Jupyter environment (like Jupyter Lab or VS Code).

2.  **To Scrape Product Reviews**:
    - In the first section of the notebook, set the `url` variable to the Daraz product page you want to scrape.
    - Run the cells to initiate the scraping process. The results will be stored in the `Review_df` DataFrame.

3.  **To Scrape Seller Information**:
    - In the third section of the notebook, you will be prompted to enter a search query (e.g., "mobile covers") and the number of sellers to scrape.
    - Run the cells, and the script will begin the automated search and data collection. The results will be stored in the `Q3_df` DataFrame.

## Example Output

Here is a sample of the data collected by the seller information scraper for the query "mobile cover":

| Seller Name                                 | Daraz Mall/Private | Avg Price | Avg unit selling | Seller Ratings | Country  | Followers |
| :------------------------------------------ | :----------------: | :-------: | :--------------: | :------------: | :------: | :-------: |
| Hontinga                                    |     Daraz Mall     |    519    |      128.75      |       93       | Overseas |   30709   |
| Jizetin Official Store                      |     Daraz Mall     |    511    |      126.75      |       94       | Overseas |   4299    |
| Deal Box                                    |      Private       |    95     |      22.75       |       84       | Pakistan |   14179   |
| ABC MOBILE ACCESSORIES STORE (FAISALABAD)   |      Private       |    92     |      22.00       |       93       | Pakistan |   12020   |
| KD Accessories (Karachi)                    |      Private       |    115    |      27.75       |       87       | Pakistan |   5509    |

## Dependencies

The project relies on the following Python libraries. A `requirements.txt` file is included for easy installation.

- `pandas`
- `numpy`
- `selenium`
- `webdriver-manager`
- `nltk`
- `scikit-learn` (for metrics and text processing)
- `Pillow`
- `scikit-image`
- `easyocr`
- `opencv-python`
