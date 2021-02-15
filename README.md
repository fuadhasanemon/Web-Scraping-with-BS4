# Web-Scraping-with-BS4
My favorite webscraping  tool ** Beautiful Soup**

Web Scraping with Python
There are a few libraries you will need, you can go to your command line and install them with conda install (if you are using anaconda distribution), or pip install for other python distributions.

` pip install requests
pip install lxml
pip install bs4 `

## Let's start very simple, we will grab the title of a page. Remember that this is the HTML block with the title tag. For this task we will use www.example.com which is a website specifically made to serve as an example domain. Let's go through the main steps:

` import requests `

## Step 1: Use the requests library to grab the page
## Note, this may fail if you have a firewall blocking Python/Jupyter 
## Note sometimes you need to run this twice if it fails the first time

`res = requests.get("http://www.example.com")`

## This object is a requests.models.Response object and it actually contains the information from the website, for example:


`type(res)`


` requests.models.Response `

`res.text`

## text will be unformated there to formate this we will use 

`import bs4`

`soup = bs4.BeautifulSoup(res.text,"lxml")`

`soup`

# Now let's use the .select() method to grab elements. We are looking for the 'title' tag, so we will pass in 'title'

`soup.select('title')`

`title_tag = soup.select('title')`

`title_tag[0]`

`type(title_tag[0])`

## Example Task 1 - Grabbing all elements of a class
Let's try to grab all the section headings of the Wikipedia Article on Grace Hopper from this URL: [wiki]("https://en.wikipedia.org/wiki/Grace_Hopper")

# First get the request
`res = requests.get('https://en.wikipedia.org/wiki/Grace_Hopper')`

# Create a soup from request
`soup = bs4.BeautifulSoup(res.text,"lxml")`

## Now its time to figure out what we are actually looking for. Inspect the element on the page to see that the section headers have the class "mw-headline". Because this is a class and not a straight tag, we need to adhere to some syntax for CSS. In this case

`Syntax to pass to the .select() method`

## Match Results

` soup.select('div') `

## All elements with the <div> tag

` soup.select('#some_id') `

## The HTML element containing the id attribute of some_id

` soup.select('.notice') `

## All the HTML elements with the CSS class named notice

` soup.select('div span') `

## Any elements named <span> that are within an element named <div>

` soup.select('div > span') `

## Any elements named <span> that are directly within an element named <div>, with no other element in between

# note depending on your IP Address, 
# this class may be called something different
`soup.select(".toctext")`

`for item in soup.select(".toctext"):
    print(item.text)`
