# ***Top 100 Movies Web Scraping Project*** <hr/><br/>
## *Project Overview* </br>
```text
This project uses Python web scraping to extract the Top 100 Movies using beautiful soup list from an archived Empire Online webpage.
And saves the movie titles into a text file.
```
### *The Script Flow:*
``` text
                    Website URL
                       ↓
                    requests.get()
                       ↓
                    response
                       ↓
                    response.text
                       ↓
                    BeautifulSoup()
                       ↓
                    find_all()
                       ↓
                    getText()
                       ↓
                    reverse list
                       ↓
                    write to file
                       ↓
                    movies.txt created
```
### *Python Code*

```
import requests
from bs4 import BeautifulSoup

URL = "https://web.archive.org/web/20200518073855/https://www.empireonline.com/movies/features/best-movies-2/"

# 👇

response = requests.get(URL)
website_html = response.text

soup = BeautifulSoup(website_html, "html.parser")

all_movies = soup.find_all(name="h3", class_="title")

movie_titles = [movie.getText() for movie in all_movies]
movies = movie_titles[::-1]

with open(r"C:\Users\hp\Downloads\movies.txt", mode="w", encoding="utf-8") as file:
    for movie in movies:
        file.write(f"{movie}\n")
```

# *Break of Code to understand:*

```
- requests.get(): Means fetch data.
- URL: from where to fetch.
- response: Stores what the website sends back.
- Beautifulsoup: It takes messy HTML and converts it into a readable structure.
- find_all: Finds all movie titles from the webpage.
- gettext(): To take content from tag  into list.
- with open as file : To save text file in our local folder
```
### *Output File*
*movies.txt*

### *Project Outcome*

```text 
The script successfully stores all movie titles in a text file line by line, creating an automated movie list extraction project using web scraping.
```
