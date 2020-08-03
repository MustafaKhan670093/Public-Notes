# Learning How To Use Beautiful Soup

### Introduction

Beautiful Soup is a Python package for parsing HTML and XML documents. It creates a parse tree for parsed pages that can be used to extract data from HTML, which is useful for web scraping.

### Process

Follow this tutorial: https://www.youtube.com/watch?v=87Gx3U0BDlo. An alternative tutorial that has been helpful is this: https://www.youtube.com/watch?v=ng2o98k983k. Below are the main lines of code that need to be understood.

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
   
   Quick side note: ```print(soup.prettify())``` returns the html source code in a formmated way.

   * ```links = soup.find_all("a")``` puts all the html 'a' tags on the page in a python list. This result can be viewed using ```print(links)``` . Alternatively, one could use the ```soup.a``` or ```soup.find('a')``` in order to find the first a tag on the webpage.
   * To extract a link with text such as the "About" link on the webpage, use the built in "text" function to access the text between the <a> </a> tags.
     ```
     for link in links:
         if "About" in link.text:
            print(link)
            print(link.attrs['href'])    #This line would print the href attribute or link within the "About" 'a' tag.
     ```

**Testing Understanding Of First Few Steps:**

I will now obtain the links from the following website: https://www.whitehouse.gov/briefings-statements/. This is the white house's website and contains presidential briefings and statements. The goal of this test is to extract all of the links on the page that point to the briefings and statements. 

```
import requests
from bs4 import BeautifulSoup

result = requests.get("https://www.whitehouse.gov/briefings-statements/")
src = result.content
soup = BeautifulSoup(src, "lxml")

urls = []
#After using inspect element on the website we notice the links to the briefings are in <a> tags stored in between <h2> tags. Thus:
for h2_tag in soup.find_all("h2"):
   a_tag = h2_tag.find("a")
   urls.append(a_tag.attrs['href'])
   
print(urls)  #To check if everything is working.
```

5. **Altering source code** using Beautiful Soup
   ```
   tag = soup.a
   print(tag)
   ```
   This results in: ```<a> ... </a>```
   
   ```
   tag.name = "blockquote"
   print(tag)
   ```
   Which results in: ```<blockquote> ... </blockquote>```
   
   Another thing that can be done is delete ID's in tags. For instance, if this were our line of code ```<a id=1> ... </a>```, then ```del tag['id']``` would result in ```<a> ... </a>```.
   
6. Getting **String Content** from websites

   In the following lines of code, ```tag.string``` returns the text in between an html tag.
   ```
   tag = soup.find_all('b')[3]
   print(tag.string)
   ```
   
   Another thing that can be done is use the replace with function to replace the content of the string with something else using:
   ```
   tag.string.replace_with("This is another string")
   ```

**Another Example Project**

I am working on writing a program that takes in a movie name as an input and returns the IMDB rating of that movie. This is the code I have worked on so far:

   ```
   import requests
   from bs4 import BeautifulSoup

   print("This program takes in a movie name and returns it's IMDB rating as the output.")

   #Taking in Movie Name as input
   input = input(str("Which movie's rating would you like to know about? : "))

   print("Please wait while I search for your input on the web...")

   #If there are spaces in the name of the movie, a proper URL won't be formed
   #so we add '+'s where there are spaces: ' '.
   movie = input.replace(' ', "+")

   #Adjusting the query to include the movie name and the words IMDB rating
   query = str(movie) + "+IMDB+Rating"

   #Forming the URL using the .format(query) function. This step produces the url for a google search.
   url = 'https://www.google.com/search?client=ubuntu&channel=fs&q={}&ie=utf-8&oe=utf-8'.format(query)

   #Performing the google search using the url and the requests library
   result = requests.get(url)

   #Getting all the html/src code from the search result
   src = result.content

   #Turning that src code into a beautiful soup object so that it can be parsed
   soup = BeautifulSoup(src, 'lxml')

   # TODO: Getting all the movie names, links and ratings that come up in the search result
   ```
   


