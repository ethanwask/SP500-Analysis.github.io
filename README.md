# DS105-project-test

<details>
  <summary>Motivation 📈🚀</summary>

## *Motivation* 📈🚀
The financial sector is an integral part of the economy and it is what drives the global capital markets. Having such an influence on the economy of not just individual countries, but the world collectively, the financial sector is what brings together most countries regardless of politics, beliefs, or background. In order to better understand why the economy is the way it is, we wanted to look deeper into some of the factors that are driving the world markets. Through analyzing the Standard and Poor's 500 (S&P 500) Index, we would be able to give a snapshot of the current market as this index provides the top 500 U.S. listed equities by market capitalization. Given these large-scale corporations, we will be able to provide our audience with a summary of the overall health of the economy and financial sector. Especially as of now, this is extremely relevant as many large financial institutions and global economies are bracing for what could be the next possible "large-scale" recession. This information could help our readers understand why the market is performing the way it is and potentially what to expect in the coming months.
  
</details>

<details>
  <summary>Data 📊</summary>

## *Data* 📊
By using the New York Times API and Yahoo Finance, we will be able to provide readers with both quantitative and qualitative resources to complement each other. Through using Yahoo Finance, readers will be able to observe the quantitiative side of the market, observing the perfomance of the various sectors and individual equities within the S&P 500 Index. Through the use of the New York Times API, readers will be provided with an assortment of articles between January 1st, 2022 and March 31st, 2023 (end of Q1), in order to gain a general understanding of why the market is where it's at in terms of perfomance and overall economic health. As a recession looms, many people who are not necessarily up to date on the markets will be able to obtain a brief understanding of the events leading up to the state of the global economy now. 

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
By using the New York Times API, we can search for articles from January 1st to the end of Quarter 1 2023 in order to effectively gain a glimpse into the major news headlines that show the health of the market and the financial sector. The next step to present our data is to begin to parse and clean this data in order to give readers a cleaner, structured, and more organized compisition of articles. The next step will require the use of "Pandas" in order to clean up this data and present an appropriate format to our readers.
  
  
  
By using the New York Times API, we can parse information to *only* provide articles on the **S&P 500 Index** as well as various other supporting articles that effect the perfomance of either the index or the market as a whole. Other queries include **markets, economy, and central banking** in which we are able to analyze some of the factors that can effect the perfomance of the market. Many equities can be affected by not only internal factors but also external ones, requiring the use of these queries. By parsing information for these queries, we are able to provide the readers with a more broader macroeconomic context, as policies from all over the world can affect the economy as a whole. The overall theme here is that the market has **many** variables that can affect perfomance **daily**.
  
</details>
