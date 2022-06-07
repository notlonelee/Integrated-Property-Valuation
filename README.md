# Integrated Property Valuation Project
This is a webscraper extracting property details from [Lamudi](https://www.lamudi.com.ph/), Philippine's #1 property listing website

## Usage
Install the BeautifulSoup library
```python
import requests
from bs4 import BeautifulSoup
```
BeautifulSoup is a Python library for pulling data out of HTML files. It works with parsers to navigate, search and modify parse trees. 

##Input
The input data source is all the property listing details available from Lamudi website's main display from pages 1-100
Code presented currently only scrapes the Housing and Lots for sale

Consists of a total of 11 variables:
- Unique ID for each listing
- Listing price
- Housing category
- Housing sub-category
- # of bedrooms
- # of bathrooms
- Building size
- Land size
- Location sub-division name
- Data on furnishings
- Geolocation coordinates 

##Output
The output comprises a total of 3,000 property listing details and saved to Excel in a csv format 
