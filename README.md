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
### Conectar e interagir com bancos de dados em Python ####
from sqlalchemy import create_engine, inspect, text

itens_pedidos = pd.read_csv(url_itens_pedidos)
pedidos = pd.read_csv(url_pedidos)
produtos = pd.read_csv(url_produto)
vendedores = pd.read_csv(url_vendedores)

```

``` Create Data base Local
### Banco de dados local na máquina ###
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

### Day 2: Consult Dataframe
```
Using SQL to read Dataframe:

query = 'SELECT CONDICAO FROM produtos'
pd.read_sql(text(query),engine)

with engine.connect() as conexao:
  consulta = conexao.execute(text(query))
  dados = consulta.fetchall()
pd.DataFrame(dados,columns=consulta.keys())

```

```
transform a function:
def sql_df(query):
  with engine.connect() as conexao:
    consulta = conexao.execute(text(query))
    dados = consulta.fetchall()
  return pd.DataFrame(dados,columns=consulta.keys())
```

```
Groupby each condition :
query = '''SELECT CONDICAO, COUNT(*) AS 'Quantidade'
FROM PRODUTOS 
GROUP BY CONDICAO;'''
df_produtos = sql_df(query)
df_produtos

```
```
Create a plt Bar with these conditions:
plt.bar(df_produtos['Condicao'],df_produtos['Quantidade'] , color='#9353FF') 
plt.title('Contagem por tipo de condições dos produtos')
plt.show()
```
```
query = '''SELECT PRODUTOS.PRODUTO, SUM(ITENS_PEDIDOS.QUANTIDADE) AS Quantidade
FROM ITENS_PEDIDOS, PRODUTOS
WHERE ITENS_PEDIDOS.PRODUTO_ID = PRODUTOS.PRODUTO_ID
GROUP BY PRODUTOS.PRODUTO
LIMIT 5 ;
'''
sql_df(query)
```

```
Create a plt Bar to show TOP 5 sellers
df_prod_quantidade = df_prod_quantidade.sort_values(by='Quantidade', ascending=True)

plt.barh(df_prod_quantidade['produto'], df_prod_quantidade['Quantidade'], color='#9353FF')
plt.title('Produtos mais vendidos')
plt.xlabel('Quantidade vendida')
plt.show()
```

### Day 3: Group Values
```
Group for a specific year
query = '''
SELECT vendedor_id, COUNT(*) AS 'Quantidade'
FROM PEDIDOS
WHERE strftime('%Y',data_compra) = '2020'
GROUP BY vendedor_id
ORDER BY Quantidade DESC
LIMIT 5
'''
sql_df(query)

```
Conecting two databases and group values
query = '''SELECT VENDEDORES.NOME_VENDEDOR, AVG(PEDIDOS.TOTAL) AS 'Valor médio por vendas'
FROM PEDIDOS, VENDEDORES
WHERE strftime('%Y',data_compra) = '2020' AND VENDEDORES.VENDEDOR_ID = PEDIDOS.VENDEDOR_ID
GROUP BY VENDEDORES.NOME_VENDEDOR
ORDER BY AVG(PEDIDOS.TOTAL) DESC;
'''
sql_df(query)

```
````

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
