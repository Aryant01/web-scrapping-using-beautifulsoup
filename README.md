# Web Scraping Project

## Overview
This project demonstrates web scraping using Python's BeautifulSoup and Requests libraries. The script fetches HTML content from a webpage, extracts specific elements like titles, links, and tables, and processes the data accordingly.

## Features
- Fetches webpage content using the Requests library.
- Parses HTML using BeautifulSoup.
- Extracts elements such as titles, links, and tables.
- Demonstrates finding elements by tag, class, and attributes.
- Iterates through multiple elements to extract structured information.

## Technologies Used
### 1. **BeautifulSoup**
BeautifulSoup is a Python library used for parsing HTML and XML documents. It creates a parse tree that makes data extraction easy.
- `find()`: Retrieves the first occurrence of an element.
- `find_all()`: Retrieves all occurrences of an element.
- `get_text()`: Extracts text content from an element.
- `['attribute']`: Fetches attribute values (e.g., `href`, `class`).

### 2. **Requests**
Requests is a Python library for making HTTP requests, which allows fetching webpage content.
- `requests.get(url)`: Retrieves HTML content from a URL.

## Installation
Before running the script, ensure you have the necessary libraries installed:
```bash
pip install requests beautifulsoup4
```

## How It Works
1. **Fetching the Webpage**
   ```python
   import requests
   from bs4 import BeautifulSoup
   
   url = "https://getpython.wordpress.com/"
   source = requests.get(url)
   soup = BeautifulSoup(source.text, 'html.parser')
   ```
   This fetches the HTML content of the given URL and parses it using BeautifulSoup.

2. **Extracting the Title**
   ```python
   title = soup.find('title')
   print("Title with HTML tags:", title)
   print("Title without HTML tags:", title.text)
   ```
   - `find('title')` extracts the `<title>` tag content.
   - `.text` retrieves only the text without HTML tags.

3. **Extracting Links**
   ```python
   links = soup.find_all('a')
   print("Total links:", len(links))
   for link in links[:6]:
       print(link, "\n")
   ```
   - `find_all('a')` retrieves all anchor (`<a>`) tags.
   - `len(links)` gives the count of links.
   - A loop iterates through links and prints them.

4. **Extracting Attributes (href, class, etc.)**
   ```python
   second_link = links[1]
   print("Href:", second_link['href'])
   print("Class:", second_link['class'])
   ```
   - Extracts specific attributes like `href` and `class`.

5. **Scraping Wikipedia Page**
   ```python
   wiki = requests.get("https://en.wikipedia.org/wiki/World_War_II")
   soup = BeautifulSoup(wiki.text, 'html.parser')
   print(soup.find('title'))
   ```
   This fetches and extracts the title of a Wikipedia page.

6. **Extracting a Table from Wikipedia**
   ```python
   overview = soup.find_all('table', class_='infobox vevent')
   for table in overview:
       print(table.text)
   ```
   - Extracts all `<table>` elements with the specified class and prints their contents.

## Use Cases
- **Data extraction** for research and analysis.
- **Automated monitoring** of website changes.
- **Collecting information** for machine learning and AI models.

## Legal Considerations
Before scraping a website, always check its `robots.txt` file and ensure compliance with legal and ethical guidelines.

## Conclusion
This project provides a fundamental approach to web scraping using Python. With further enhancements, you can apply it to extract structured data, automate workflows, and analyze content efficiently.

