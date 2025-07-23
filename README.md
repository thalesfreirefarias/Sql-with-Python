# SQL and Python


# DailyStudy

![GitHub repo size](https://img.shields.io/github/repo-size/iuricode/README-template?style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/iuricode/README-template?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/iuricode/README-template?style=for-the-badge)
![Bitbucket open issues](https://img.shields.io/bitbucket/issues/iuricode/README-template?style=for-the-badge)
![Bitbucket open pull requests](https://img.shields.io/bitbucket/pr-raw/iuricode/README-template?style=for-the-badge)

### Day 1: import SQL in Python

``` Import Data Base
import matplotlib.pyplot as plt
import pandas as pd
###Conectar e interagir com bancos de dados em Python####
from sqlalchemy import create_engine, inspect, text

itens_pedidos = pd.read_csv(url_itens_pedidos)
pedidos = pd.read_csv(url_pedidos)
produtos = pd.read_csv(url_produto)
vendedores = pd.read_csv(url_vendedores)

```

``` Create Data base Local
###Banco de dados local na máquina ###
engine = create_engine('sqlite:///:memory:')

produtos.to_sql('produtos',engine,index=False)
itens_pedidos.to_sql('itens_pedidos',engine,index=False)
pedidos.to_sql('pedidos',engine,index=False)
vendedores.to_sql('vendedores',engine,index=False)
```

```Inspect
inspector = inspect(engine)
print(inspector.get_table_names())
```




### Adjustments and improvements.

The project is still under development, and the upcoming updates will focus on the following tasks:

- [x] Advanced courses about Phyton

The following tools were used in the construction of the project:

- [Python](<https://www.python.org/doc//>)
- [SQL](<https://www.postgresql.org/docs/current/sql.html>)


## 🤝 Creator

<table>
  <tr>
    <td align="center">
      <a href="#" title="Thales Farias">
        <img src="grecia.jpg" width="100" alt="Foto do Thales Farias no GitHub"/><br>
        <sub>
          <b><a href="https://www.linkedin.com/in/thalesfreirefarias/" target="_blank">Thales Farias</b>
        </sub>
      </a>
    </td>
  </tr>
</table>
