# Learning How To Use Beautiful Soup

### Introduction

Beautiful Soup is a Python package for parsing HTML and XML documents. It creates a parse tree for parsed pages that can be used to extract data from HTML, which is useful for web scraping.

### Process

Follow this tutorial: https://www.youtube.com/watch?v=87Gx3U0BDlo. Below are the main lines of code that need to be understood.

1. **Imports**

   ```
   import requests  
   from bs4 import BeautifulSoup  
   ```

2. Using the **Requests Module**

   The requests module allows you to send HTTP requests using Python. The HTTP request returns a Response Object with all the response data (content, encoding,     status, etc). Using the requests module, we use the "get" function in order to access the webpage as an argument to this function.

   ```
   result = requests.get("https://www.google.com")
   ```
   
   Note: To make sure that the website is accessible, check for a 200 OK response to indicate that the page is indeed present. Do this using: ``` print(result.status_code) ```
   
   For other potential status codes you may encounter consult the following
   Wikipedia page: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
   
   We can also check the HTTP header of the website to verify that we have 
   indeed accessed the correct page: ```print(result.headers)```
   
   For more information on HTTP headers and the information one can obtain from them,
   consult: https://en.wikipedia.org/wiki/List_of_HTTP_header_fields
   
   
3. Extracting the **Content** of the page (and storing it in a variable)

   ```src = result.content```
 
4. Using **Beautiful Soup** + creating a **soup** class to parse and process the source code

   ```soup = BeautifulSoup(src, 'lxml')```

   * ```links = soup.find_all("a")``` puts all the html 'a' tags on the page in a python list. This result can be viewed using ```print(links)```
   * To extract a link with text such as the "About" link on the webpage, use the built in "text" function to access the text between the <a> </a> tags.
     ```
     for link in links:
         if "About" in link.text:
            print(link)
            print(link.attrs['href'])    #This line would print the href attribute or link within the "About" 'a' tag.
     ```

**Testing Understanding Of First Few Steps:**

I will now obtain the links from the following website: https://www.whitehouse.gov/briefings-statements/. This is the white house's website and contains presidential briefings and statements. The goal of this test is to extract all of the links on the page that point to the briefings and statements. 

