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
Before choosing our data sources, we had to identify and address several problems that ultimately led to the evolution of our project. The first problem that we encountered was the structure of the S&P 500 Index itself, where U.S.-listed equities within the Index change daily according to each corporations' market capitalization. This means that if the value of a corporation drops enough, they can be replaced with the next largest corporation by market capitalization. This poses a problem as there is simply too much volatility in the market, meaning that there is so much movement that it is extremely difficult to collect and analyze real-time data as the Index is dynamic. This led us to morph our project into creating a "snapshot" of the Index's performance over the a window of about 1.25 years (Jan. 1st 2022 to March 31st 2023). This snapshow would help us give the reader a sense of the *overall* health of the economy, rather than just one Index within the exchange. As many large corporations are driving the global economy, analyzing the health of these corporations could help give the reader a general sense of how the economy is shaping, as within big tech, we are now seeing a wave of mass-layoffs that haven't been seen since the 2008 global financial crisis. This 1.25 year snapshot will allow readers to see some of the events that have led up to the state of the global economy, whether it's interest rate hikes, inflation, or even corporations missing EPS (earnings per share) expectations, these variables will be accessible to the reader and help give some underlying context on the matter. The second major challenge we faced were the data sources, as we orignially planned on using Kaggle, a subsidiary of Google, however after researching the reliability of this resource, we decided to not use Kaggle as we wanted to provide readers with accurate and up-to-date information such as an accredited news source such as NYT. 

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
  
</details>

<details>
  <summary>Exploratory Data Analysis 🔭🔬📊</summary>
  
## *Exploratory Data Analysis 🔭🔬📊*
  
</details>
