# Web Scraping Project

## About

This comprehensive Web Scraping project demonstrates advanced techniques to extract and organize data from websites when structured data sources are unavailable. It covers multiple web scraping tasks including extracting headings, paragraphs, lists, tables, product details, form information, hyperlinks, media links, and featured products.

This project highlights practical applications of Python's `requests` and `BeautifulSoup` libraries to gather and save data in CSV and JSON formats, showcasing my proficiency in web scraping for research, competitive analysis, and data collection.

---

## Features

- Extracts **headings (h1, h2)**, **paragraphs (p)**, and **list items (li)** and saves them into a CSV file (`Extracting.csv`).
- Scrapes all **table data** from the webpage and exports it to `Table.csv`.
- Collects detailed **product information** (title, price, stock availability, button text) and saves it as `Product_Information.json`.
- Extracts **form metadata** including form action, method, and input fields saved in `FormDetails.json`.
- Gathers all **hyperlinks** and embedded **video links (iframes)** into `LinksAndMedia.json`.
- Retrieves a list of **featured products** with their id, name, price, and colors into `Featured_Products.json`.

---

## Repository Contents

| Filename                 | Description                             |
|--------------------------|-----------------------------------------|
| `Extracting.csv`         | Extracted headings, paragraphs, lists  |
| `Table.csv`              | Extracted table data                    |
| `Product_Information.json` | Extracted product details               |
| `FormDetails.json`       | Extracted HTML form details             |
| `LinksAndMedia.json`     | Extracted hyperlinks and video links    |
| `Featured_Products.json` | Extracted featured products details     |

---

## How to Use

1. Clone the repository.
2. Run each Python script to perform specific scraping tasks. Each script scrapes different parts of the target website (`https://www.baraasallout.com/test.html`).
3. The data extracted will be saved into respective CSV or JSON files in the repository.

---

## Example of Scraping Headings, Paragraphs, and Lists (Excerpt)

```python
import requests
from bs4 import BeautifulSoup
import csv

url = "https://www.baraasallout.com/test.html"
response = requests.get(url)
website = BeautifulSoup(response.text,'html.parser')

headings = [h.get_text().strip() for h in website.find_all(['h1', 'h2'])]
paragraphs = [p.get_text().strip() for p in website.find_all('p')]
listeditems = [li.get_text().strip() for li in website.find_all('li')]

data = []
for heading in headings:
    data.append(['Heading', heading])
for paragraph in paragraphs:
    data.append(['Paragraph', paragraph])
for item in listeditems:
    data.append(['Listed items', item])

with open('Extracting.csv', 'w', newline='', encoding='utf-8') as file:
    writer = csv.writer(file)
    writer.writerow(['Type', 'Content'])
    writer.writerows(data)
```
## Skills Demonstrated
- Web scraping with Python (`requests`, `BeautifulSoup`)

- Data extraction and parsing from complex HTML structures

- Exporting scraped data to CSV and JSON formats

- Handling various HTML elements (headings, lists, tables, forms, links, media)

- Organizing and documenting code for clear, reusable workflows


## Notes
- The project focuses on scraping a sample site (https://www.baraasallout.com/test.html), but the approach is adaptable for other websites with similar structures.

##### All data files are included in the repository for review and testing.

---

If you want me to tailor it further (more concise, add instructions on how to run each part separately, or add badges etc.) just Contact me!



