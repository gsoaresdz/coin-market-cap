<h1 align="center">CoinMarketCap API Scraper</h1><p align="center"><img alt="Github top language" src="https://img.shields.io/github/languages/top/gsoaresdz/coin-market-cap?color=56BEB8"><img alt="Github language count" src="https://img.shields.io/github/languages/count/gsoaresdz/coin-market-cap?color=56BEB8"><img alt="Repository size" src="https://img.shields.io/github/repo-size/gsoaresdz/coin-market-cap?color=56BEB8">
  <!--<img alt="License" src="https://img.shields.io/github/license/gsoaresdz/coin-market-cap?color=56BEB8">-->
</p><p align="center"><a href="#dart-sobre">Sobre</a> &#xa0; | &#xa0;
  <a href="#sparkles-features">Features</a> &#xa0; | &#xa0;
  <a href="#rocket-tecnologias">Tecnologias</a> &#xa0; | &#xa0;
  <a href="#white_check_mark-requerimentos">Requerimentos</a> &#xa0; | &#xa0;
  <a href="#checkered_flag-execução">Execução</a> &#xa0; | &#xa0;
  <a href="#memo-licença">Licença</a> &#xa0; | &#xa0;
  <a href="https://github.com/gsoaresdz" target="_blank">Autor</a></p><br>## 
  
## **:dart: Sobre**

Este projeto consiste em um script Python que automatiza a busca de preços de criptomoedas na web e armazena os resultados em um arquivo Excel. O script utiliza as seguintes bibliotecas:

- **pandas:** para manipulação de dados.
- **selenium:** para controlar o navegador e realizar buscas na web.
- **openpyxl:** para trabalhar com arquivos Excel.

## **:memo: IDE e versão do Python**

O script foi desenvolvido no Jupyter Notebook com a versão 3.8 do Python.

## **:memo: Regra de negócio**

O script funciona da seguinte forma:

1. Acessa a página da CoinMarketCap.
2. Coleta os preços das criptomoedas especificadas.
3. Armazena os resultados em um arquivo Excel.

## **:memo: Passos executados no código**

O código é dividido em duas partes principais:

- Acesso à página da CoinMarketCap
- Automação de Busca de Preços

## **:memo: Acesso à página da CoinMarketCap**

A primeira parte do código acessa a página da CoinMarketCap para buscar informações sobre criptomoedas. O código a seguir mostra como acessar a página:

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import pandas as pd

# Configurar o webdriver
navegador = webdriver.Chrome()
navegador.get('https://coinmarketcap.com/')
```

## **:sparkles: Features**

A segunda parte do código automatiza a busca de preços para as criptomoedas. O código funciona da seguinte forma:

:heavy_check_mark: **Feature 1**: Abre o navegador e acessa a página da CoinMarketCap.

:heavy_check_mark: **Feature 2**: Coleta os preços das criptomoedas listadas na página.

:heavy_check_mark: **Feature 3**: Armazena os resultados em um arquivo Excel.

O código a seguir mostra como realizar uma busca e coletar o preço:

```python
criptomoedas = []
precos = []

# Coletar as criptomoedas e seus preços
for i in range(1, 11):  # Coletar as 10 primeiras criptomoedas
    criptomoeda = navegador.find_element(By.XPATH, f'//*[@id="__next"]/div/div[1]/div[2]/div/div[1]/div/table/tbody/tr[{i}]/td[3]/div/a/div/div/p').text
    preco = navegador.find_element(By.XPATH, f'//*[@id="__next"]/div/div[1]/div[2]/div/div[1]/div/table/tbody/tr[{i}]/td[4]/div/a/span').text
    criptomoedas.append(criptomoeda)
    precos.append(preco)

# Criar DataFrame e salvar em Excel
df = pd.DataFrame({'Criptomoeda': criptomoedas, 'Preço': precos})
df.to_excel('Precos_Criptomoedas.xlsx', index=False)
```

## **:rocket: Tecnologias**

As seguintes ferramentas foram usadas neste projeto:

- [Python](https://www.python.org/)
- [Jupyter](https://jupyter.org/)
- [Selenium](https://www.selenium.dev/)
- [Pandas](https://pandas.pydata.org/)
- [Openpyxl](https://openpyxl.readthedocs.io/)

## **:white_check_mark: Requerimentos**

Antes de iniciar :checkered_flag:, você precisa ter [Git](https://git-scm.com/) e [Python](https://www.python.org/) instalados.

## **:checkered_flag: Execução**

```bash
bash
# Clone do projeto
$ git clone https://github.com/gsoaresdz/coin-market-cap.git

# Acesse o diretório do projeto
$ cd coin-market-cap

# Instale as dependências
$ pip install -r requirements.txt

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
