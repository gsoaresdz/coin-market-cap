# **CoinMarketCap API Scraper**

Este projeto é um scraper simples para o site CoinMarketCap, criado para extrair dados sobre diferentes criptomoedas. Os dados são extraídos utilizando BeautifulSoup e requests em Python, e finalmente organizados em um DataFrame do pandas para fácil visualização e análise.

## **Pré-requisitos**

Este projeto requer Python e as seguintes bibliotecas Python instaladas:

- **[BeautifulSoup](https://pypi.org/project/beautifulsoup4/)**
- **[requests](https://pypi.org/project/requests/)**
- **[pandas](https://pypi.org/project/pandas/)**
- **[re](https://docs.python.org/3/library/re.html)**

## **Como executar**

Na sua linha de comando, execute:

```
bashCopy code
python nome_do_arquivo.py

```

## **Código**

Este script de Python extrai os seguintes dados para cada moeda listada no CoinMarketCap:

- Nome
- Código
- Preço atual
- Variação percentual na última hora
- Variação percentual nas últimas 24 horas
- Variação percentual nos últimos 7 dias
- Market Cap
- Volume

## **Problemas conhecidos**

Este script pode falhar se o layout do site CoinMarketCap mudar, já que ele depende da estrutura atual da página para localizar e extrair os dados corretamente. Além disso, ele não tem manejo para lidar com possíveis problemas de conexão ou disponibilidade do site.

## **Contribuições**

Contribuições são bem-vindas! Para contribuir, por favor:

1. Faça um Fork deste repositório.
2. Crie uma Branch para suas modificações (**`git checkout -b feature/AmazingFeature`**).
3. Faça o Commit de suas mudanças (**`git commit -m 'Add some AmazingFeature'`**).
4. Faça o Push para a Branch (**`git push origin feature/AmazingFeature`**).
5. Abra uma Pull Request.
