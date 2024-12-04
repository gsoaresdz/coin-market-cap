<h1 align="center">CoinMarketCap API Scraper</h1> <p align="center"> <img alt="Github top language" src="https://img.shields.io/github/languages/top/gsoaresdz/coin-market-cap?color=56BEB8"> <img alt="Github language count" src="https://img.shields.io/github/languages/count/gsoaresdz/coin-market-cap?color=56BEB8"> <img alt="Repository size" src="https://img.shields.io/github/repo-size/gsoaresdz/coin-market-cap?color=56BEB8"> <!--<img alt="License" src="https://img.shields.io/github/license/gsoaresdz/coin-market-cap?color=56BEB8">--> </p> <p align="center"> <a href="#dart-about">About</a> &#xa0; | &#xa0; <a href="#sparkles-features">Features</a> &#xa0; | &#xa0; <a href="#rocket-technologies">Technologies</a> &#xa0; | &#xa0; <a href="#white_check_mark-requirements">Requirements</a> &#xa0; | &#xa0; <a href="#checkered_flag-execution">Execution</a> &#xa0; | &#xa0; <a href="#memo-license">License</a> &#xa0; | &#xa0; <a href="https://github.com/gsoaresdz" target="_blank">Author</a> </p> <br>

## **:dart: About**

This project is a Python script that automates the retrieval of cryptocurrency prices from the web and stores the results in a DataFrame. The script utilizes the following libraries:

- **pandas:** for data manipulation.
- **beautifulsoup4:** for web scraping.
- **requests:** for making HTTP requests.

## **:memo: IDE and Python Version**

The script was developed using Jupyter Notebook with Python version 3.8.

## **:memo: Business Rules**

The script operates as follows:

1. Accesses the CoinMarketCap webpage.
2. Collects the prices of specified cryptocurrencies.
3. Stores the results in a DataFrame.

## **:memo: Steps Executed in the Code**

The code is divided into two main parts:

- Accessing the CoinMarketCap webpage
- Automating Price Retrieval

## **:memo: Accessing the CoinMarketCap Page**

The first part of the code accesses the CoinMarketCap webpage to retrieve cryptocurrency information. The following code shows how the page is accessed:

```python
import requests
from bs4 import BeautifulSoup

link = 'https://coinmarketcap.com/'
requisicao = requests.get(link)
site = BeautifulSoup(requisicao.text, 'html.parser')
```

## **:sparkles: Features**

The second part of the code automates the price retrieval for cryptocurrencies. The code operates as follows:

:heavy_check_mark: **Feature 1**: Accesses the CoinMarketCap page and collects data for listed cryptocurrencies.

:heavy_check_mark: **Feature 2**: Organizes the data into a pandas DataFrame.

The following code shows how the data is collected and organized:

```python
import re
import pandas as pd

tbody = site.find('tbody')
linhas = tbody.find_all('tr')

moedas = {}

for linha in linhas:
  try:
    nome = linha.find(class_='kKpPOn').text
    codigo = linha.find(class_='coin-item-symbol').text
    valores = linha.find_all(string=re.compile('\$'))
    preco = valores[0]
    percentuais = linha.find_all(string=re.compile('%'))

    for i, percentual in enumerate(percentuais):
      if 'bQjSqS' in percentual.parent["class"]:
        percentuais[i] = "-" + str(percentual)

    var_1h = percentuais[0]
    var_24h = percentuais[1]
    var_7d =  percentuais[2]

    market_cap = valores[2]
    volume = valores[3]
    dic = {"nome": nome, "codigo": codigo, "preco": preco, "var_1h": var_1h, "var_24h": var_24h, "var_7d": var_7d,"market_cap": market_cap, "volume": volume}
    moedas[nome] = dic
  except AttributeError:
    break

df = pd.DataFrame(moedas)
display(df)
```

## **:rocket: Technologies**

The following tools were used in this project:

- [Python](https://www.python.org/)
- [Jupyter](https://jupyter.org/)
- [BeautifulSoup](https://beautiful-soup-4.readthedocs.io/en/latest/)
- [Requests](https://pypi.org/project/requests/)
- [Pandas](https://pandas.pydata.org/)

## **:white_check_mark: Requirements**

Before starting :checkered_flag:, make sure you have [Git](https://git-scm.com/) and [Python](https://www.python.org/) installed.

## **:checkered_flag: Execution**

```bash
# Clone the project
$ git clone https://github.com/gsoaresdz/coin-market-cap.git

# Run the script
$ jupyter notebook main.ipynb
```

## **:memo: Notes**

- This script was developed for educational purposes. It is not recommended to use the script for commercial purposes without proper authorization from the websites.
- The script can be modified to meet different needs, such as changing the XPath selectors or adding new functionalities.

## **:memo: License**

This project is under the MIT license. For more details, see the [LICENSE](LICENSE) file.

Made with :heart: by <a href="https://github.com/gsoaresdz" target="_blank">gsoaresdz</a>

<a href="#top">Back to top</a>
