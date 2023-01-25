# Exploring the Makeup and Performance of the S&P 500 Index

<details>
  <summary>Focus Problem 🚩</summary>

<img width="1274" alt="Screen Shot 2023-01-25 at 2 43 16 PM" src="https://user-images.githubusercontent.com/118006806/214593322-df7b3887-898c-4ef2-b270-2be5f929ea04.png">

*How could we provide readers with a way to filter thousands of articles that only pertain to the equities listed within the S&P 500 Index and inform less-experienced investors about the makeup of the index?*

</details>

<details>
  <summary>The S&P 500 Index Explained</summary>

## *The S&P 500 Index Explained*
The Standard and Poor's 500 Index is market-capitalization-weighted index of the 500 largest publicly traded U.S. companies. In essence, this weighting system measures companies through multiplying the equity price with shares outstanding. This weighting system is able to provide a "valuation" of these companies, thus putting the 500 most valuable publicly traded companies within the Index. Additionally, the Index is dynamic - meaning it's composition is  *always* changing alongside the market. Some companies may lose enough value to fall out of the index while others may increase their value enough to make their way in. However, it is widely believed within the financial sector that this index is one of the best gauges of the health of the economy due to it's depth and weighting. Because of it's ability to gauge the health of the economy, we found the S&P 500 index to be an important resource to investors and economists when determining the state of the economy. 

</details>

<details>
  <summary>Motivation 📈🚀</summary>

## *Motivation* 📈🚀
The financial sector is an integral part of the economy and it is what drives the global capital markets. Having such an influence on the economy of not just individual countries, but the world collectively, the financial sector is what brings together most countries regardless of politics, beliefs, or background. In order to better understand why the economy is the way it is, we wanted to look deeper into some of the factors that are driving the world markets. Through analyzing the Standard and Poor's 500 (S&P 500) Index, we would be able to give a snapshot of the current market as this index provides the top 500 U.S.-listed equities by market capitalization. Given these large-scale corporations, we will be able to provide our audience with a summary of the overall health of the economy and financial sector. Especially as of now, this is extremely relevant as many large financial institutions and global economies are bracing for what could be the next possible "large-scale" recession. This information could help our readers understand why the market is performing the way it is and potentially what to expect in the coming months. By providing readers with this information, we could help mitigate bad investment practices and potentially provide resources that could help investors decide upon investment opportunities within the market. 
  
</details>

<details>
  <summary>Justification ⚖️</summary>
  
Our project is relevant to both economists, investors, and everyday citizens, as the possibility of a recession is able to impact people on all levels throughout the economy. By giving readers a central hub where articles are able to be drawn while also providing real-time data on the composition and perfomance of the index, we will be able to provide resources to our readers in which the events leading up to either a recession or slow-down will be observable and understood. When trying to understand why the economy is performing the way it is, economists are interested in geopolitical variables and monetary/fiscal policy changes, which are provided through the NYT Articles API. Additionally, both economists and investors will be interested in the perfomance of the S&P 500 Index, as this index provides a reliable gauge on the health of the economy. 
  
</details>


<details>
  <summary>Data 📊</summary>

## *Data* 📊
By using the New York Times API, we will be able to provide readers with both quantitative and qualitative resources to complement each other. Through using New York Times' "Market Overview" section, readers will be able to observe the quantitiative side of the market, observing the perfomance of the various sectors and individual equities within the S&P 500 Index. Through the use of the New York Times Articles API, readers will be provided with an assortment of articles between January 1st, 2022 and March 31st, 2023 (end of Q1), in order to gain a general understanding of why the market is where it's at in terms of perfomance and overall economic health. As a recession looms, many people who are not necessarily up to date on the markets will be able to obtain a brief understanding of the events leading up to the state of the global economy now. 

### *Preliminary Challenges* 🏃
Before choosing our data sources, we had to identify and address several problems that ultimately led to the evolution of our project. The first problem that we encountered was the structure of the S&P 500 Index itself, where U.S.-listed equities within the Index change daily according to each corporations' market capitalization. This means that if the value of a corporation drops enough, they can be replaced with the next largest corporation by market capitalization. This poses a problem as there is simply too much volatility in the market, meaning that there is so much movement that it is extremely difficult to collect and analyze real-time data as the Index is dynamic. This led us to morph our project into creating a "snapshot" of the Index's performance over the a window of about 1.25 years (Jan. 1st 2022 to March 31st 2023). This snapshow would help us give the reader a sense of the *overall* health of the economy, rather than just one Index within the exchange. As many large corporations are driving the global economy, analyzing the health of these corporations could help give the reader a general sense of how the economy is shaping, as within big tech, we are now seeing a wave of mass-layoffs that haven't been seen since the 2008 global financial crisis. This 1.25 year snapshot will allow readers to see some of the events that have led up to the state of the global economy, whether it's interest rate hikes, inflation, or even corporations missing EPS (earnings per share) expectations, these variables will be accessible to the reader and help give some underlying context on the matter. The second major challenge we faced were the data sources, as we orignially planned on using Kaggle, a subsidiary of Google, however after researching the reliability of this resource, we decided to not use Kaggle as we wanted to provide readers with accurate and up-to-date information such as an accredited news source such as NYT and SlickCharts, who provide real times data on these sources. In addition to SlickCharts, in order to obtain information on the various sectors that make up the S&P 500 Index, we will be using Wikipedia, as they provide real-time data on the index with sector information about each equity that will be useful when analyzing the makeup of the index.

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
  
  ![S P Bar Graph Python](https://user-images.githubusercontent.com/118006806/214340026-4fbbc2f0-e094-45e7-84d1-74b7d371ea03.png)

  
Alternatively, we can show the proportion of the equities that makeup the S&P 500 Index by using Madplotlib, specifially their pie chart 🥧📊 feature, in which we write the following code within the terminal: 
  
  ```js
  import matplotlib.pyplot as plt

plt.pie(sector_count, labels=sector_count.index, autopct='%1.1f%%')
plt.title('Percentage of Firms per Sector')
plt.show()
   ```
By using Madpoltlib we are able to output a pie chart that represents our data that looks like this:
  
  ![S P Pie Chart Python](https://user-images.githubusercontent.com/118006806/214339815-86e2a215-ccaa-4dca-a356-fa6470ee7d49.png)

After seeing the proportion of equities that makeup the various sectors within the index, it is now clear that five sectors dominate the market, which are: technology, industrials, financials, healthcare, and consumer discretionary. This gives us a new persepctive when understanding the market, as due to having more equtiies with higher market capitalization within these five sectors, it is clear that the current macroeconomic environment is allowing for these sectors to grow. Now, with this information, when seeing a specific ticker associated with the S&P 500 Index within the NYT Articles that were webscraped, there can be an understanding of the current market share that the equity is within. 

### *Analyzing the Top 10 Firms*

Now that we understand the general makeup of the S&P 500 Index, we want to be able to show all relevant information pertaining to the top 10 equities in order to fully understand if there is a general trend showing that there is in fact, a top performing sector. To do so, we will examine the top 10 equities within the index (the firms with the largest market capitalization). 

By using the existing dataframe we formed using Pandas 🐼, we will now look for *only* the top 10 equities within the index. To do so, we will type the following within the terminal:

```js
#Change the Price and Change values from an object to a numeric datatype
df['Price'] = pd.to_numeric(df['Price'], errors='coerce')
df['Chg'] = pd.to_numeric(df['Chg'], errors='coerce')

#Remove the Percentage Symbol and Brackets from the percentage change column
df['% Chg'] = df['% Chg'].str.replace('%', '')
df['% Chg'] = df['% Chg'].str.replace('(', '')
df['% Chg'] = df['% Chg'].str.replace(')', '')

#Sort the firms by price in descending order
df.sort_values("Price", ascending=False, inplace=True)

#Print the data for the top 10 firms
print(df.head(10))

#Create a new dataframe with the data for just the top 10 firms
df_10 = df.head(10)

print(df_10)

#checking for missing values with new dataframe
df_10.isna().sum()
```

By running the following code, we are able to convert the data from the previous dataframe into numeric data and sort the firms by price in descending order in order to give us a new dataframe containing just the top 10 firms. This new dataframe will allow us to look even further into the top performing firms and hopefully draw connections to which sectors may be outperforming others. 

#### *Changes in Prices from the Top Firms*

In order to gauge the health of the economy, analyzing the discrepencies in prices is vital to be able to understand how volatile the market is and if there are a significant amount of firms exhibiting decreases in value, there is some indication that the market is eithe underperfomring for that day, or if it extends for a brief period, a recession may be looming. 

To observe this, we must find the current prices of the top 10 firms and be able to visualize this data through graphs. To do so, we will once again be using Madplotlib to visually display our findings and type the following within the terminal: 

```js
# Create a list from the price and symbol column in the DataFrame
column_name = 'Price'
column_list_price = df_10[column_name].tolist()
top_firm_price = column_list_price[:10]
print(top_firm_price)
[799.2, 740.18, 734.3, 716.68, 695.73, 581.2, 574.26, 567.53, 502.62, 502.12]
column_name = 'Symbol'
column_list_symbol = df_10[column_name].tolist()
top_firm_symbol = column_list_symbol[:10]
print(top_firm_symbol)
['ORLY', 'REGN', 'BLK', 'EQIX', 'TDG', 'AVGO', 'TMO', 'GWW', 'HUM', 'MSCI']
#Invert the list, so prices are in ascending order
top_price = top_firm_price[::-1]
#Invert the firm's symbols to match their prices
top_firms = top_firm_symbol[::-1]
# Create a bar chart displaying the prices for the Top Firms
plt.bar(top_firms,top_price, color='red')
plt.xlabel('Firms')
plt.ylabel('Price')
plt.title('Prices of the shares of the Top Firms')
```

By using Madplotlib, we are able to create a bar graph displaying the prices of the top 10 firms which looks like:

![Prices of the Shares of the Top Firms](https://user-images.githubusercontent.com/118006806/214691598-03a24748-7372-483a-89a9-0b662cbbbc57.png)

Now that we know the top 10 firms within the index as well as their prices, we now want to be able to observe any price discrepencies these equities may have experienced, as with this information we will be able to see whether or not these firms are underperforming even as the top performers. 
  
To structure this data into a chart, we will type the following into the terminal: 
  
```js
  #Create a list from the price change column
column_name = 'Chg'
column_list_chg = df_10[column_name].tolist()
top_firm_chg = (column_list_chg[:10])[::-1]
print(top_firm_chg)
[-17.72, 2.27, -3.31, -6.46, -3.83, 1.48, -2.94, -17.77, 12.71, 0.11]
#Make a bar chart showing the price change for each firm
plt.bar(top_firms,top_firm_chg)
plt.xlabel('Firms')
plt.ylabel('Price Change')
plt.title('Price Changes of the shares of the Top Firms')
  ```

By changing the axis labels and analyzing the price changes, we are able to see any discrepencies in prices with these firms, which looks like:
  
  ![Price change of firm](https://user-images.githubusercontent.com/118006806/214693008-9c395078-bb6f-448c-93d4-3a14e7e28f17.png)

Although we may be able to see price changes, percent changes will be able to effectively display these discrepencies relative to the equities' existing prior price point. This will help us gauge the extent to which the proportion of it's value has either *fallen* or *risen*. 
  
To find this, we will once again use Madplotlib to create a bar chart by writing the following within the terminal:
  
  ```js
 #Make a list using the percentage change column
column_name = '% Chg'
column_list_chg = df_10[column_name].tolist()
top_firm_per_chg = (column_list_chg[:10])[::-1]
print(top_firm_per_chg)
['-3.41', '0.45', '-0.58', '-1.11', '-0.66', '0.21', '-0.41', '-2.36', '1.75', '0.01']
#Make a bar chart for the percentage change in the price of each firm
plt.bar(top_firms,top_firm_chg,color='green')
plt.xlabel('Firms')
plt.ylabel('Percentage Change')
plt.title('Percentage Change in the Price of the shares of the Top Firms')
  ```
  
Which outputs: 
  
  ![Price change of firm %](https://user-images.githubusercontent.com/118006806/214695086-87e6a5e2-ac6b-4907-8723-48a17643c983.png)

From this we can now be able to effectively show the discrepencies in prices relative to the firms prior price. Through this visualization, it is clear that there is some slowdown or even decrease in growth, as the majority of these firms are exhibiting negative movements in prices. 
  
#### *Sector Composition of the Top 10 Firms*
  
For investors and economists, understanding the perfomance of different sectors is crucial to understanding why the economy and markets are behaving how they are. For example, the price of industrial equities may be performing well at the end of the COVID-19 Pandemic due to the supply chain issues, thus driving prices up. Additionally, the war in Ukraine may be putting pressure on the energy sector as there is a very limited supply of natural gasses, thus increasing the prices of equities within the energy sector. To be able to observe similar effects within the market, we will be looking at the composition of the top 10 equities within the S&P 500, as we may be able to draw the same conclusions with the sectors within this dataset. 
  
</details>
