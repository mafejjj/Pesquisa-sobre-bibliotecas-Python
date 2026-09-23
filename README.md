# Bibliotecas Python para Banco de Dados

---

## 1. pyodbc

### 1. Qual o objetivo?

Permitir que aplicações Python se conectem a bancos de dados usando ODBC.

### 2. Quais bancos acessa?

Pode acessar vários bancos que possuem driver ODBC, como SQL Server, PostgreSQL, MySQL e Oracle.

### 3. Relacional ou não relacional?

É mais utilizada com bancos **relacionais**.

### 4. SQL ou ORM?

Trabalha com **SQL puro**.

### 5. Instalação

```bash
pip install pyodbc
```

### 6. Exemplo de conexão

```python
import pyodbc

conexao = pyodbc.connect(
    "DRIVER={ODBC Driver 18 for SQL Server};"
    "SERVER=localhost;"
    "DATABASE=meu_banco;"
    "UID=usuario;"
    "PWD=senha;"
    "TrustServerCertificate=yes;"
)

print("Conectado!")
```

### 7. SELECT

```python
cursor = conexao.cursor()

cursor.execute("SELECT * FROM clientes")

for linha in cursor.fetchall():
    print(linha)

conexao.close()
```

---

## 2. pymssql

### 1. Qual o objetivo?

Conectar aplicações Python ao Microsoft SQL Server.

### 2. Quais bancos acessa?

Principalmente o **Microsoft SQL Server**.

### 3. Relacional ou não relacional?

É utilizada com bancos **relacionais**.

### 4. SQL ou ORM?

Trabalha com **SQL puro**.

### 5. Instalação

```bash
pip install pymssql
```

### 6. Exemplo de conexão

```python
import pymssql

conexao = pymssql.connect(
    server="localhost",
    user="usuario",
    password="senha",
    database="meu_banco"
)

print("Conectado!")
```

### 7. SELECT

```python
cursor = conexao.cursor()

cursor.execute("SELECT * FROM clientes")

for linha in cursor.fetchall():
    print(linha)

conexao.close()
```

---

## 3. psycopg2

### 1. Qual o objetivo?

Permitir que aplicações Python se conectem ao PostgreSQL.

### 2. Quais bancos acessa?

**PostgreSQL**.

### 3. Relacional ou não relacional?

É utilizada com bancos **relacionais**.

### 4. SQL ou ORM?

Trabalha com **SQL puro**.

### 5. Instalação

```bash
pip install psycopg2-binary
```

### 6. Exemplo de conexão

```python
import psycopg2

conexao = psycopg2.connect(
    host="localhost",
    database="meu_banco",
    user="usuario",
    password="senha",
    port="5432"
)

print("Conectado!")
```

### 7. SELECT

```python
cursor = conexao.cursor()

cursor.execute("SELECT * FROM clientes")

for linha in cursor.fetchall():
    print(linha)

conexao.close()
```

---

## 4. SQLAlchemy

### 1. Qual o objetivo?

Facilitar o trabalho com bancos de dados e permitir o uso de **ORM**.

### 2. Quais bancos acessa?

Pode trabalhar com vários bancos, como:

* PostgreSQL
* MySQL
* SQL Server
* SQLite
* Oracle

### 3. Relacional ou não relacional?

É voltado para bancos **relacionais**.

### 4. SQL ou ORM?

Pode trabalhar com **SQL e ORM**.

### 5. Instalação

```bash
pip install sqlalchemy
```

### 6. Exemplo de conexão

Exemplo usando SQLite:

```python
from sqlalchemy import create_engine

engine = create_engine("sqlite:///meu_banco.db")

conexao = engine.connect()

print("Conectado!")
```

### 7. SELECT

```python
from sqlalchemy import text

resultado = conexao.execute(
    text("SELECT * FROM clientes")
)

for linha in resultado:
    print(linha)

conexao.close()
```

---

## 5. sqlite3

### 1. Qual o objetivo?

Permitir que aplicações Python utilizem bancos SQLite.

### 2. Quais bancos acessa?

**SQLite**.

### 3. Relacional ou não relacional?

É um banco **relacional**.

### 4. SQL ou ORM?

Trabalha com **SQL puro**.

### 5. Instalação

Não precisa instalar. O `sqlite3` já vem com o Python.

```python
import sqlite3
```

### 6. Exemplo de conexão

```python
import sqlite3

conexao = sqlite3.connect("meu_banco.db")

print("Conectado!")
```

### 7. SELECT

```python
cursor = conexao.cursor()

cursor.execute("SELECT * FROM clientes")

for linha in cursor.fetchall():
    print(linha)

conexao.close()
```

---

# Conclusão

As bibliotecas possuem diferentes finalidades. A `pyodbc` permite conexão com vários bancos através de ODBC, enquanto `pymssql` é voltada para SQL Server e `psycopg2` para PostgreSQL.

A `sqlite3` é uma opção simples para trabalhar com SQLite, pois já vem com o Python. Já o `SQLAlchemy` possui mais recursos e permite utilizar tanto SQL quanto ORM.

A escolha da biblioteca depende do banco utilizado e das necessidades do projeto.
