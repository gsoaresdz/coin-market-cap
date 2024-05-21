<h1 align="center">Automação de Busca de Preços de Criptomoedas</h1>
<p align="center">
  <img alt="Github top language" src="https://img.shields.io/github/languages/top/gsoaresdz/coin-market-cap?color=56BEB8">
  <img alt="Github language count" src="https://img.shields.io/github/languages/count/gsoaresdz/coin-market-cap?color=56BEB8">
  <img alt="Repository size" src="https://img.shields.io/github/repo-size/gsoaresdz/coin-market-cap?color=56BEB8">
  <!--<img alt="License" src="https://img.shields.io/github/license/gsoaresdz/coin-market-cap?color=56BEB8">-->
</p>
<p align="center">
  <a href="#dart-sobre">Sobre</a> &#xa0; | &#xa0; 
  <a href="#sparkles-features">Features</a> &#xa0; | &#xa0;
  <a href="#rocket-tecnologias">Tecnologias</a> &#xa0; | &#xa0;
  <a href="#white_check_mark-requerimentos">Requerimentos</a> &#xa0; | &#xa0;
  <a href="#checkered_flag-execução">Execução</a> &#xa0; | &#xa0;
  <a href="#memo-licença">Licença</a> &#xa0; | &#xa0;
  <a href="https://github.com/gsoaresdz" target="_blank">Autor</a>
</p>
<br>

## **:dart: Sobre**

Este projeto consiste em um script Python que automatiza a busca de preços de criptomoedas na web e armazena os resultados em um DataFrame. O script utiliza as seguintes bibliotecas:

- **pandas:** para manipulação de dados.
- **beautifulsoup4:** para fazer scraping das páginas web.
- **requests:** para realizar requisições HTTP.

## **:memo: IDE e versão do Python**

O script foi desenvolvido no Jupyter Notebook com a versão 3.8 do Python.

## **:memo: Regra de negócio**

O script funciona da seguinte forma:

1. Acessa a página da CoinMarketCap.
2. Coleta os preços das criptomoedas especificadas.
3. Armazena os resultados em um DataFrame.

## **:memo: Passos executados no código**

O código é dividido em duas partes principais:

- Acesso à página da CoinMarketCap
- Automação de Busca de Preços

## **:memo: Acesso à página da CoinMarketCap**

A primeira parte do código acessa a página da CoinMarketCap para buscar informações sobre criptomoedas. O código a seguir mostra como acessar a página:

```python
import requests
from bs4 import BeautifulSoup

link = 'https://coinmarketcap.com/'
requisicao = requests.get(link)
site = BeautifulSoup(requisicao.text, 'html.parser')
```

## **:sparkles: Features**

A segunda parte do código automatiza a busca de preços para as criptomoedas. O código funciona da seguinte forma:

:heavy_check_mark: **Feature 1**: Acessa a página da CoinMarketCap e coleta os dados das criptomoedas listadas.

:heavy_check_mark: **Feature 2**: Organiza os dados em um DataFrame pandas.

O código a seguir mostra como realizar a coleta e organizar os dados:

```python
pythonCopy code
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

## **:rocket: Tecnologias**

As seguintes ferramentas foram usadas neste projeto:

- [Python](https://www.python.org/)
- [Jupyter](https://jupyter.org/)
- [BeautifulSoup](https://beautiful-soup-4.readthedocs.io/en/latest/)
- [Requests](https://pypi.org/project/requests/)
- [Pandas](https://pandas.pydata.org/)

## **:white_check_mark: Requerimentos**

Antes de iniciar :checkered_flag:, você precisa ter [Git](https://git-scm.com/) e [Python](https://www.python.org/) instalados.

## **:checkered_flag: Execução**

```bash
bash
# Clone do projeto
$ git clone https://github.com/gsoaresdz/coin-market-cap.git

# Execute o script
$ jupyter notebook main.ipynb

```

## **:memo: Observações**

- O script foi desenvolvido para fins educacionais. Não é recomendado o uso do script para fins comerciais sem autorização dos sites.
- O script pode ser modificado para atender a diferentes necessidades. Por exemplo, é possível alterar os seletores de XPath ou incluir novas funcionalidades.

## **:memo: Licença**

Este projeto está sob licença do MIT. Para obter mais detalhes, consulte o arquivo [LICENSE](https://chatgpt.com/c/LICENSE).

Feito com :heart: by <a href="https://github.com/gsoaresdz" target="_blank">gsoaresdz</a>

<a href="#top">De volta ao topo</a>
