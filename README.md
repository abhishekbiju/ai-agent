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

## Source

This project is inspired by a project from Tech with Tim linked [here](https://youtu.be/xekw62yQu14?si=tXvaigf4cmm6zgVv)
