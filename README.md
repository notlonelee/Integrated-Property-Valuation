# Integrated Property Valuation Project
This is a webscraper extracting property details from [Lamudi](https://www.lamudi.com.ph/), Philippine's #1 property listing website
This makes reference to the [Webscraper script](https://github.com/notlonelee/Integrated-Property-Valuation/blob/main/Webscraper)

## Usage
Install the BeautifulSoup library
```python
import requests
from bs4 import BeautifulSoup
```
BeautifulSoup is a Python library for pulling data out of HTML files. It works with parsers to navigate, search and modify parse trees. 

## Objective
1. A for loop is used to load all 100 pages of the Lamudi website. This serves as our search space where the input data is retrieved. 
```python
 for i in range(1,101): 
  each_data = {} 
  if i == 1: 
    URL = 'https://www.lamudi.com.ph/house/buy/' 
  elif i > 1: 
    URL = 'https://www.lamudi.com.ph/house/buy/?page={}'.format(i) 
 ```
2. Extract the class that displays each property listed on the website.  
```python
all = soup.find_all("div",attrs={"class":"row ListingCell-row ListingCell-agent-redesign"}) 
```
3. Use another for loop to extract the information from the class where all the propeorty listing details are embedded, for each individual property listing. 
```python
 for each in all: 
    all_details = each.find("div",attrs={"class":"ListingCell-AllInfo ListingUnit"}) 
```
4. Retrieve the listed variables. We use try and except to ensure that we extract data from all listings, even if it does not have inputs for certain variables. 
```python
    try:
      each_data["id"] = all_details['data-sku']
    except:
      pass
```
5. Append the data of each listing to a new list. This is the our output data. 
```python
    all_data = [] 
    all_data.append(each_data) 
```

## Input
The input data source is all the property listing details available from Lamudi website's main display from pages 1-100
The code presented currently only scrapes the Housing and Lots for sale

Consists of a total of 11 variables:
- Unique ID for each listing
- Listing price
- Housing category
- Housing sub-category
- Number of bedrooms
- Number of bathrooms
- Building size
- Land size
- Location sub-division name
- Data on furnishings
- Geolocation coordinates 


## Output
The output comprises a total of 3,000 property listing details and saved to Excel in a csv format 
