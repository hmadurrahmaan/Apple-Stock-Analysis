# Stock Price Query Application

## Overview

This repository contains a Flask application designed to fetch, plot, and generate detailed descriptions of Apple's stock price over the last five years. The application leverages `yfinance` for data retrieval, `matplotlib` for plotting, and `LangChain` for generating detailed descriptions using the `Llama3` model.

## Features

- **Stock Data Retrieval**: Fetches historical stock data for Apple (AAPL) using `yfinance`.
- **Data Visualization**: Plots the stock price over the last five years using `matplotlib`.
- **Detailed Descriptions**: Generates a comprehensive description of the stock's performance using the `Llama3` model from `LangChain`.

## Getting Started

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/hmadurrahmaan/Apple-Stock-Analysis.git
    cd Apple-Stock-Analysis
    ```

2. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

### Setting Up Ollama

1. Download Ollama from the following link: [Ollama Download](https://ollama.com/)

2. Install the Llama3 model on your local system:
    ```bash
    ollama run llama3
    ```

### Running the Application

1. Start the Flask server:
    ```bash
    python app.py
    ```

2. Open your web browser and navigate to `http://localhost:5000`.

## Usage

1. Enter your query in the input field on the main page (e.g., "What is Apple’s stock price for the last 5 years").
2. Submit the query to view the stock price chart and a detailed description of the stock's performance.

## File Structure

- `app.py`: The main Flask application file that handles routes, data fetching, plotting, and description generation.
- `templates/index.html`: The homepage template with a query input form.
- `templates/result.html`: The results page template displaying the stock price chart and generated description.
- `static/`: Directory to store generated stock price charts.

## Code Explanation

### app.py

- **fetch_and_plot_stock_data(ticker_symbol)**:
  - Defines the time period for the last five years.
  - Fetches stock data using `yfinance`.
  - Plots the stock price and saves the plot as an image in the `static` directory.

- **summarize_stock_data(stock_data)**:
  - Prepares a summary of the stock data using descriptive statistics.

- **generate_description(summary_text, base_url, model)**:
  - Initializes the `Llama3` model from `LangChain`.
  - Generates a detailed description based on the stock summary.

- **index()**:
  - Handles the main route, processes the user query, fetches and plots stock data, summarizes it, and generates a description.

### index.html

- Contains a form to input the stock query.
- Displays an error message if the query is not recognized.

### result.html

- Displays the query result, including the stock price chart and the generated description.
