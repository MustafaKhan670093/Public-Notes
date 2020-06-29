# Learning How To Use Beautiful Soup

### Introduction

Beautiful Soup is a Python package for parsing HTML and XML documents. It creates a parse tree for parsed pages that can be used to extract data from HTML, which is useful for web scraping.

### Process

Follow this tutorial: https://www.youtube.com/watch?v=87Gx3U0BDlo below are the main lines of code that need to be understood.

1. **Imports**

```
import requests
from bs4 import BeautifulSoup
```

2. Using the **Requests Module**

The requests module allows you to send HTTP requests using Python. The HTTP request returns a Response Object with all the response data (content, encoding, status, etc). Using the requests module, we use the "get" function provided in order to access the webpage provided as an argument to this function.

result = requests.get("https://www.google.com")

src = result.content

soup = BeautifulSoup(src, 'lxml')

links = soup.find_all("a")

print(links)
print("\n")
```
I got the following error: FeatureNotFound: Couldn't find a tree builder with the features you requested: lxml. Do you need to install a parser library?

In order to get around this, I followed the instructions 
