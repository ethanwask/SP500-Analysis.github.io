# DS105-project-test

<details>
  <summary>Motivation 📈🚀</summary>

## *Motivation* 📈🚀
The financial sector is an integral part of the economy and it is what drives the global capital markets. Having such an influence on the economy of not just individual countries, but the world collectively, the financial sector is what brings together most countries regardless of politics, beliefs, or background. In order to better understand why the economy is the way it is, we wanted to look deeper into some of the factors that are driving the world markets. Through analyzing the Standard and Poor's 500 (S&P 500) Index, we would be able to give a snapshot of the current market as this index provides the top 500 U.S.-listed equities by market capitalization. Given these large-scale corporations, we will be able to provide our audience with a summary of the overall health of the economy and financial sector. Especially as of now, this is extremely relevant as many large financial institutions and global economies are bracing for what could be the next possible "large-scale" recession. This information could help our readers understand why the market is performing the way it is and potentially what to expect in the coming months.
  
</details>

<details>
  <summary>Data 📊</summary>

## *Data* 📊
By using the New York Times API, we will be able to provide readers with both quantitative and qualitative resources to complement each other. Through using New York Times' "Market Overview" section, readers will be able to observe the quantitiative side of the market, observing the perfomance of the various sectors and individual equities within the S&P 500 Index. Through the use of the New York Times Articles API, readers will be provided with an assortment of articles between January 1st, 2022 and March 31st, 2023 (end of Q1), in order to gain a general understanding of why the market is where it's at in terms of perfomance and overall economic health. As a recession looms, many people who are not necessarily up to date on the markets will be able to obtain a brief understanding of the events leading up to the state of the global economy now. 

### *Preliminary Challenges* 🏃
Before choosing our data sources, we had to identify and address several problems that ultimately led to the evolution of our project. The first problem that we encountered was the structure of the S&P 500 Index itself, where U.S.-listed equities within the Index change daily according to each corporations' market capitalization. This means that if the value of a corporation drops enough, they can be replaced with the next largest corporation by market capitalization. This poses a problem as there is simply too much volatility in the market, meaning that there is so much movement that it is extremely difficult to collect and analyze real-time data as the Index is dynamic. This led us to morph our project into creating a "snapshot" of the Index's performance over the a window of about 1.25 years (Jan. 1st 2022 to March 31st 2023). This snapshow would help us give the reader a sense of the *overall* health of the economy, rather than just one Index within the exchange. As many large corporations are driving the global economy, analyzing the health of these corporations could help give the reader a general sense of how the economy is shaping, as within big tech, we are now seeing a wave of mass-layoffs that haven't been seen since the 2008 global financial crisis. This 1.25 year snapshot will allow readers to see some of the events that have led up to the state of the global economy, whether it's interest rate hikes, inflation, or even corporations missing EPS (earnings per share) expectations, these variables will be accessible to the reader and help give some underlying context on the matter. The second major challenge we faced were the data sources, as we orignially planned on using Kaggle, a subsidiary of Google, however after researching the reliability of this resource, we decided to not use Kaggle as we wanted to provide readers with accurate and up-to-date information such as an accredited news source such as NYT and SlickCharts, who provide real times data on these sources. 

### *Snippets of Code Used to Search API For Articles Containing S&P 500* 👨‍💻
 
  ```js
  import requests
import json

### GET ARTICLES MATCHING OUR QUERY ###
def get_url(q, begin_date, end_date):
    url = ("https://api.nytimes.com/svc/search/v2/articlesearch.json?q={0}&begin_date={1}&end_date={2}&api-key=GAgkTBB83AC0GwrrTCDTbUxv8R09Dq41".format(q, begin_date, end_date))
    return url

print("Querying NYTimes API...")
r = requests.get(get_url('S&P500', 20220101, 20230331))
print("Status Code returned {0}".format(r.status_code))
print("Data returned: ")
print(r.json()['response']['docs'])
  
  ```
By using the New York Times API, we can search for articles from January 1st to the end of Quarter 1 2023 in order to effectively gain a glimpse into the major news headlines that show the health of the market and the financial sector. The next step to present our data is to begin to parse and clean this data in order to give readers a cleaner, structured, and more organized compisition of articles. The next step will require the use of "Pandas" in order to clean up this data and present an appropriate format to our readers, as the response generated a mass of various text that will need to be parsed.
  
### *Using "Pandas" 🐼 to Structure and Clean our Data* 
  
By using the New York Times API, we can parse information to *only* provide articles on the **S&P 500 Index** as well as various other supporting articles that effect the perfomance of either the index or the market as a whole. Other queries include **markets, economy, and central banking** in which we are able to analyze some of the factors that can effect the perfomance of the market. Many equities can be affected by not only internal factors but also external ones, requiring the use of these queries. By parsing information for these queries, we are able to provide the readers with a more broader macroeconomic context, as policies from all over the world can affect the economy as a whole. The overall theme here is that the market has **many** variables that can affect perfomance **daily**.
  
 ```js
  import pandas as pd
df = pd.json_normalize(r.json()['response']['docs'])
  df
  
  ```
  
By using "Pandas" 🐼, we are able to display the data into a chart, allowing for a more cleaner and accesible method to viewing the articles pulled that match our query. Now that the article are more organized, we must now convert this data into a CSV file, which will allow us to save our data into a table structured format.
  
### *Using Visual Studio Code to Convert Data into a .CSV File*
  
  *insert code and images for VSCode*
  
### *Webscraping SlickCharts 📊 for S&P 500 Index Performance 🏋️*

Now that relevant articles are pulled from the NYT API, we must now find the relevant data containing company name, ticker symbol, weight (market capitalization), current price, change in price from day prior, and finally the percentage change in price. To do so, we will be webscraping SlickCharts for data on the S&P 500 Index. To do so, we will need to use a combination of BeautifulSoup 🥣 (which parses the data we want), Pandas 🐼 (which structures and organizes this data to be more streamline), and also Cloudscraper ☁️ (in order to bypass cloudfare's "anti-bot" page). By utilizing these three components, we are able to present this data within a table, organized for our readers to examine.

While writing the code, we ran into an issue in which SlickChart's was detecting our webscraping as a bot. In order to bypass Cloudfare's bot detection, I used a tool called Cloudscraper ☁️, in which it bypasses this bot detection and is able to run the script and pull the relevant data ot be analyzed. By opening up the terminal and typing:

```js
pip install cloudscraper

 ```
Once Cloudscraper ☁️ is installed, we are ready to pull data!

```js
from bs4 import BeautifulSoup
import pandas as pd
import cloudscraper

url = 'https://www.slickcharts.com/sp500'
scraper = cloudscraper.create_scraper(browser = 'chrome') # you can try 'firefox' here too?
page = scraper.get(url).text  # get the raw html text
soup = BeautifulSoup(page, 'html.parser') # convert html text to BeautifulSoup object

table1 = soup.find('table', class_='table-borderless') # get the first table
table1_head = table1.find_all('th') # isolate the head since this has the column headers we want
table1_body = table1.find('tbody') # isolate table body since this has the data aka "guts"

# Get headers of table (i.e., #, Company, Symbol, etc)
headers = []
for i in table1_head:
    # extract just the value using .string (i.e., Company, Symbol, etc) and clean it up
    headers.append(i.string.text.strip())

# Get the "guts" aka all data 
all_data = []  # set up a list where we'll store our final data
rows = table1_body.find_all('tr') # get all the rows first, in each row there will be data
for row in rows:  # loop through each row
    cols = row.find_all('td') # in the given row, find the data we'll need
    cols = [ele.text.strip() for ele in cols] # extract the data for the given row and clean it up
    all_data.append([ele for ele in cols]) # add the current data to our python list called "all_data"

# Print everything out
print(headers)
for item in all_data[:10]: # [:10] means go through the first 10 items in the list, can change to 20, etc
    print(item)
    
   ```
By combining these elements, we are able to pull all relevant data from the website in order to give our readers a "snapshot" of the health of the market, as the S&P 500 Index holds a large foothold and influence over the global markets. Typically when the S&P 500 Index underperforms, the market as a whole tends to follow the same trends, as most of the financial markets are driven by behavior (either bullish or bearish). 

</details>

<details>
  <summary>Exploratory Data Analysis 🔭🔬📊</summary>
  
## *Exploratory Data Analysis 🔭🔬📊*
  
### *Further Analysis of the S&P 500 Index*
  
Now that we have a general understanding of the equities that make up the S&P 500 Index, we wanted to show our readers the various sectors this index covers in order to provide them with an additional understanding of the sectors that are performing well and those that are beginning to falter. By providing information regarding the sectors, we are able to show how some of the supplemental articles regarding geo-political events may influence the markets, more specifically these sectors. In order to find the sectors that makeup the index, we must once again webscrape, however this time we will be using Wikipedia, as the other resources provided fail to state the sectors that form the S&P 500 Index. We are abel to pull this ionformation by opening the terminal and typing:
  
```js
  
  # import the required libraries
import requests
from bs4 import BeautifulSoup
url = 'https://en.wikipedia.org/wiki/List_of_S%26P_500_companies'
# sending a request to the site
page = requests.get(url)
# parsing the content
soup = BeautifulSoup(page.content, 'html.parser')
table = soup.find('table', {'class': 'wikitable sortable'})
  
  ```
  
Now that we pulled the required information, we need to create a DataFrame by utilizing Pandas 🐼, in which we will type into the terminal:
  
  ```js
  
  import pandas as pd
# Extract data from wikipedia 
rows = table.find_all('tr')
data_list = []
for row in rows:
    data = row.find_all('td')
    try:
        company = data[0].find('a').get_text()
        sector = data[3].get_text()
        data_list.append([company, sector])
    except:
        pass

# Create DataFrame
df = pd.DataFrame(data_list, columns=['Company', 'Sector'])
print(df)

   ```
  
  Once we input and run the code, a DataFrame is produced in which each individual equity's sector is defined and structured within a table. Now, we want to find the various sector names that makeup the S&P, rather than search the entire index for this information. We will do so by typing the following within the terminal:
  
   ```js
  df['Sector'].unique()
   ```
Now we are able to see the individual sectors that makeup the index, rather than searching through all of the equities. Knowing the individual sectors is important to us, as we want to be able to examine how different macroeconomic variables within the news may affect the health of not just the economy as a whole, but potentially even just sectors. For example, new healthcare regulations may affect the health sector or growing anti-trust laws may affect big tech. This information is vital for us in order to give our readers resources to determine the overall state of the economy/sectors. 
  
Next, we want to be able to identify the number of equities within each sector, as this will help us determine top perfomring sectors (those with the highest nuber of equities in the index) or the lowest perfroming sectors (those with the least number of equities in the index). We will do so by typing the following code in the terminal:
  
   ```js
  # Group data by sector and count the number of firms in each sector
sector_count = df.groupby('Sector').size()
# Convert this dataframe to a dictionary
sector_count = sector_count.to_dict()
#Counting the number of firms per sector
sector_count = df['Sector'].value_counts()
sector_count
  ```
  
This code will give us the amount of equities within the exchange in each individual sector, which will help us find what we were looking for in the paragraph above. 
  
 ### *Structuring Data Visualizations Using Madplotlib* 📊
 
Although we have all relevant information, we still need to provide our readers with visualizations that will display this infomation. Visualizations are crucial to our data analysis as they provide an avenue to analyze data in a clean and concise manner that is able to quickly show patterns or correlations between variables. In order to provide our readers with these visualizations, we will utilize Madplotlib, a plotting library used to analyze data extracted using Python 🐍. First, we will be creating a bar chart using Madplotlib, in which we will write the following code within the terminal:
  
  ```js
  import matplotlib.pyplot as plt
sector_count.plot(kind='bar')
plt.xlabel('Sector')
plt.ylabel('Number of Firms')
plt.title('Number of Firms per Sector')
plt.show()
   ```
  
By utilizing this code, we are able to output a bar chart that looks like this:
  
  *insert picture of table*
  
Alternatively, we can show the proportion of the equities that makeup the S&P 500 Index by using Madplotlib, specifially their pie chart 🥧📊 feature, in which we write the following code within the terminal: 
  
  ```js
  import matplotlib.pyplot as plt

plt.pie(sector_count, labels=sector_count.index, autopct='%1.1f%%')
plt.title('Percentage of Firms per Sector')
plt.show()
   ```
By using Madpoltlib we are able to output a pie chart that represents our data that looks like this:
  
  *insert pie chart*
  

  
</details>
