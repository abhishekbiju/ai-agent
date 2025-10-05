# Firecrawl Service

This project provides a Python service class, `FirecrawlService`, to simplify interactions with the [Firecrawl API](https://firecrawl.dev/). It offers methods to search for web pages and scrape their content in Markdown format.

## Features

* **Search**: Find web pages based on a query (specifically tailored to find company pricing pages).
* **Scrape**: Extract the content of a specific URL in a clean, Markdown format.
* **Environment-based Configuration**: Securely loads the Firecrawl API key from environment variables.
* **Simple Error Handling**: Catches exceptions during API calls and prints them to the console.

## Requirements

* Python 3.x
* `firecrawl-py`
* `python-dotenv`

## Setup & Installation

1.  **Clone the repository or download the `firecrawl_service.py` file.**
2.  **Install the required dependencies:**
    ```bash
    pip install firecrawl-py python-dotenv
    ```
3.  **Create a `.env` file** in the root of your project directory and add your Firecrawl API key:
    ```
    FIRECRAWL_API_KEY="your_api_key_here"
    ```
    You can get an API key from the [Firecrawl website](https://firecrawl.dev/).

## Usage

Here's a basic example of how to use the `FirecrawlService` class.

```python
from firecrawl_service import FirecrawlService

# Initialize the service
# This will automatically load the API key from your .env file
firecrawl = FirecrawlService()

# 1. Search for companies
search_query = "CRM software"
search_results = firecrawl.search_companies(query=search_query, num_results=3)

if search_results and search_results.data:
    print(f"Found {len(search_results.data)} results for '{search_query}':")
    for result in search_results.data:
        # The actual content of the result object may vary based on the firecrawl-py library version
        print(f"- {result.get('title', 'No Title')}: {result.get('url')}")
        # print(result) # Uncomment to see the full result object

    # 2. Scrape one of the found pages
    if search_results.data:
        first_url = search_results.data[0].get('url')
        if first_url:
            print(f"\nScraping URL: {first_url}")
            scraped_content = firecrawl.scrape_company_pages(url=first_url)
            if scraped_content:
                # The 'markdown' key holds the scraped content
                print("\n--- Scraped Markdown Content ---")
                print(scraped_content.get('markdown', 'No markdown content found.'))
                print("------------------------------")
else:
    print("No search results found or an error occurred.")
```

## Source

This project is inspired by a project from Tech with Tim linked [here](https://youtu.be/xekw62yQu14?si=tXvaigf4cmm6zgVv)