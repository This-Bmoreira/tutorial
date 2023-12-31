# índice

- [Criar um container MySQL](#criar-um-container-mysql)
- [SQL Básico](#sql-básico)
  - [SQL SELECT Statement](#sql-select-statement)
  - [SQL SELECT DISTINCT Statement](#sql-select-distinct-statement)
    - [Count Distinct](#count-distinct)
  - [SQL WHERE Clause](#sql-where-clause)
  - [SQL ORDER BY](#sql-order-by)
    - [DESC](#desc)
    - [Order Alphabetically](#order-alphabetically)
    - [Alphabetically DESC](#alphabetically-desc)
    - [ORDER BY Several Columns](#order-by-several-columns)
    - [Using Both ASC and DESC](#using-both-asc-and-desc)
- [Operadores Lógicos](#operadores-lógicos)
  - [SQL AND Operator](#sql-and-operator)
  - [SQL OR Operator](#sql-or-operator)
  - [NOT Operator](#not-operator)
- [Manipulação de Dados](#manipulação-de-dados)
  - [SQL INSERT INTO Statement](#sql-insert-into-statement)
  - [NULL](#null)
  - [SQL UPDATE Statement](#sql-update-statement)
  - [SQL DELETE Statement](#sql-delete-statement)
- [Consultas Avançadas](#consultas-avançadas)
  - [SQL SELECT TOP Clause](#sql-select-top-clause)
    - [LIMIT](#limit)
    - [ADD a WHERE CLAUSE](#add-a-where-clause)
    - [ADD the ORDER BY Keyword](#add-the-order-by-keyword)
  - [SQL MIN() and MAX() Functions](#sql-min-and-max-functions)
    - [ADD a WHERE CLAUSE](#add-a-where-clause)
    - [Ignore Duplicates](#add-the-order-by-keyword)
  - [SQL COUNT() Function](#sql-count-function)
  - [SQL SUM() Function](#sql-sum-function)
  - [SQL AVG() Function](#sql-avg-function)
- [Operadores de Comparação](#operadores-de-comparação)
  - [SQL LIKE Operator](#sql-like-operator)
  - [SQL Wildcard Characters](#sql-wildcard-characters)
  - [SQL IN Operator](#sql-in-operator)
  - [SQL BETWEEN Operator](#sql-between-operator)
- [Tabelas e Joins](#tabelas-e-joins)
  - [SQL Aliases](#sql-aliases)
  - [SQL JOIN](#sql-join)
  - [INNER JOIN](#inner-join)
  - [SQL LEFT JOIN Keyword](#sql-left-join-keyword)
  - [SQL RIGHT JOIN Keyword](#sql-right-join-keyword)
  - [FULL OUTER JOIN Syntax](#FULL-OUTER-JOIN-Syntax)
  - [SQL Self Join](#sql-self-join)
  - [SQL FULL OUTER JOIN Keyword](#sql-full-outer-join-keyword)
- [Agrupamento e Funções Avançadas](#agrupamento-e-funções-avançadas)
  - [SQL UNION Operator](#sql-union-operator)
  - [SQL GROUP BY Statement](#sql-group-by-statement)
  - [SQL HAVING Clause](#sql-having-clause)
  - [SQL EXISTS Operator](#sql-exists-operator)
  - [SQL ANY and ALL Operators](#sql-any-and-all-operators)
  - [SQL SELECT INTO Statement](#sql-select-into-statement)
  - [SQL INSERT INTO SELECT Statement](#sql-insert-into-select-statement)
  - [SQL CASE Expression](#sql-case-expression)
  - [SQL IFNULL(), ISNULL(), COALESCE(), and NVL() Functions](#sql-ifnull-isnull-coalesce-and-nvl-functions)
- [SQL Database](#sql-database)
  - [SQL CREATE DB](#sql-create-db)
  - [SQL SHOW DATABASES](#sql-show-databases)
  - [SQL DROP DB](#sql-drop-db)
  - [SQL USE](#sql-use)
  - [SQL CREATE TABLE](#sql-create-table)
  - [SQL DROP TABLE](#sql-drop-table)
    - [TRUNCATE](#truncate)
  - [SQL ALTER TABLE](#sql-alter-table)
    - [SQL ADD Column](#sql-add-column)
    - [SQL DROP Column](#sql-drop-column)
    - [SQL DROP Column](#sql-drop-column)
    - [SQL RENAME Column](#sql-rename-column)
    - [SQL ALTER DATATYPE](#sql-alter-datatype)
  - [SQL Create Constraints](#sql-create-constraints)
    - [NOT NULL Constraint](#not-null-constraint)
      - [SQL NOT NULL on ALTER TABLE](#sql-not-null-on-alter-table)
    - [UNIQUE Constraint](#unique-constraint)
      - [SQL UNIQUE Constraint on ALTER TABLE](#sql-unique-constraint-on-alter-table)
      - [DROP a UNIQUE Constraint](#drop-a-unique-constraint)
    - [PRIMARY KEY Constraint](#primary-key-constraint)
      - [PRIMARY KEY on ALTER TABLE](#primary-key-on-alter-table)
      - [DROP a PRIMARY KEY Constraint](#drop-a-primary-key-constraint)
    - [FOREIGN KEY Constraint](#foreign-key-constraint)
      - [FOREIGN KEY on ALTER TABLE](#foreign-key-on-alter-table)
      - [DROP a FOREIGN KEY Constraint](#drop-a-foreign-key-constraint)
    - [CHECK Constraint](#check-constraint)
      - [CHECK on ALTER TABLE](#check-on-alter-table)
      - [DROP a CHECK Constraint](#drop-a-check-constraint)
    - [DEFAULT Constraint](#default-constraint)
      - [DEFAULT on ALTER TABLE](#default-on-alter-table)
      - [DROP a DEFAULT Constraint](#drop-a-default-constraint)
  - [SQL CREATE INDEX Statement](#sql-create-index-statement)
    - [DROP INDEX Statement](#drop-index-statement)
  - [SQL Date Data Types](#sql-date-data-types)
  - [SQL CREATE VIEW Statement](#sql-create-view-statement)
    - [SQL Updating a View](#sql-updating-a-view)
    - [SQL Dropping a View](#sql-dropping-a-view)

## Criar um container MySQL

```bash
docker run -d \
  --name meu-mysql-container \
  -e MYSQL_ROOT_PASSWORD=sua_senha_root \
  -e MYSQL_USER=seu_usuario \
  -e MYSQL_PASSWORD=sua_senha \
  -v /caminho/para/seu/volume:/var/lib/mysql \
  -p 3306:3306 \
  mysql:latest
```

Aguarde alguns segundos para o container iniciar completamente

```bash
docker exec -it meu-mysql-container mysql -h 127.0.0.1 -u root -p
```

Quando solicitado, digite sua senha

```bash
password: sua_senha_root
```

**[:arrow_up: back to top](#índice)**

## SQL Básico

### SQL SELECT Statement

A instrução SELECT é usada para selecionar dados de um banco de dados.

Criando a tabela Products (apenas para fins de exemplo, você pode já ter uma tabela semelhante)

```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(255),
    Category VARCHAR(50),
    Price DECIMAL(10, 2),
    StockQuantity INT
);
```

outlook:

```bash
Query OK, 0 rows affected (0.54 sec)
```

```sql
DESCRIBE Products;
```

```bash
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
| ProductID     | int           | NO   | PRI | NULL    |       |
| ProductName   | varchar(255)  | YES  |     | NULL    |       |
| Category      | varchar(50)   | YES  |     | NULL    |       |
| Price         | decimal(10,2) | YES  |     | NULL    |       |
| StockQuantity | int           | YES  |     | NULL    |       |
+---------------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela Products

```sql
INSERT INTO Products (ProductID, ProductName, Category, Price, StockQuantity)
VALUES
    (1, 'Laptop', 'Electronics', 1200.00, 50),
    (2, 'Smartphone', 'Electronics', 800.00, 100),
    (3, 'Desk Chair', 'Furniture', 150.00, 30),
    (4, 'Coffee Maker', 'Appliances', 50.00, 75),
    (5, 'Running Shoes', 'Sports', 80.00, 200);
```

```bash
Query OK, 5 rows affected (0.13 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionando o nome e o preço dos produtos da categoria 'Electronics'

```sql
SELECT ProductName, Price
FROM Products
WHERE Category = 'Electronics';
```

```bash
+-------------+---------+
| ProductName | Price   |
+-------------+---------+
| Laptop      | 1200.00 |
| Smartphone  |  800.00 |
+-------------+---------+
2 rows in set (0.00 sec)
```

Selecionando todas as colunas da tabela Products

```sql
SELECT *
FROM Products;
```

```bash
+-----------+---------------+-------------+---------+---------------+
| ProductID | ProductName   | Category    | Price   | StockQuantity |
+-----------+---------------+-------------+---------+---------------+
|         1 | Laptop        | Electronics | 1200.00 |            50 |
|         2 | Smartphone    | Electronics |  800.00 |           100 |
|         3 | Desk Chair    | Furniture   |  150.00 |            30 |
|         4 | Coffee Maker  | Appliances  |   50.00 |            75 |
|         5 | Running Shoes | Sports      |   80.00 |           200 |
+-----------+---------------+-------------+---------+---------------+
5 rows in set (0.00 sec)
```

```sql
DROP TABLE Products;
```

```bash
Query OK, 0 rows affected (0.37 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL SELECT DISTINCT Statement

A instrução SELECT DISTINCT é usada para retornar apenas valores distintos (diferentes).

Criando a tabela Customers

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(255),
    ContactName VARCHAR(255),
    Address VARCHAR(255),
    City VARCHAR(100),
    PostalCode VARCHAR(20),
    Country VARCHAR(50)
);
```

```bash
Query OK, 0 rows affected (0.47 sec)
```

```sql
DESCRIBE Customers;
```

```bash
+--------------+--------------+------+-----+---------+-------+
| Field        | Type         | Null | Key | Default | Extra |
+--------------+--------------+------+-----+---------+-------+
| CustomerID   | int          | NO   | PRI | NULL    |       |
| CustomerName | varchar(255) | YES  |     | NULL    |       |
| ContactName  | varchar(255) | YES  |     | NULL    |       |
| Address      | varchar(255) | YES  |     | NULL    |       |
| City         | varchar(100) | YES  |     | NULL    |       |
| PostalCode   | varchar(20)  | YES  |     | NULL    |       |
| Country      | varchar(50)  | YES  |     | NULL    |       |
+--------------+--------------+------+-----+---------+-------+
7 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela Customers

```sql
INSERT INTO Customers (CustomerID, CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES
  (1, 'Alfreds Futterkiste', 'Maria Anders', 'Obere Str. 57', 'Berlin', '12209', 'Germany'),
  (2, 'Ana Trujillo Emparedados y helados', 'Ana Trujillo', 'Avda. de la Constitución 2222', 'México D.F.', '05021', 'Mexico'),
  (3, 'Antonio Moreno Taquería', 'Antonio Moreno', 'Mataderos 2312', 'México D.F.', '05023', 'Mexico'),
  (4, 'Around the Horn', 'Thomas Hardy', '120 Hanover Sq.', 'London', 'WA1 1DP', 'UK'),
  (5, 'Berglunds snabbköp', 'Christina Berglund', 'Berguvsvägen 8', 'Luleå', 'S-958 22', 'Sweden');
```

```bash
Query OK, 5 rows affected (0.13 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

```sql
SELECT DISTINCT Country
FROM Customers;
```

```bash
+---------+
| Country |
+---------+
| Germany |
| Mexico  |
| UK      |
| Sweden  |
+---------+
4 rows in set (0.00 sec)
```

Excluindo a tabela Customers

```sql
DROP TABLE Customers;
```

```bash
Query OK, 0 rows affected (0.37 sec)
```

**[:arrow_up: back to top](#índice)**

#### Count Distinct

Criando a tabela Orders

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATE,
    ShipCountry VARCHAR(50)
);
```

```bash
Query OK, 0 rows affected (1.03 sec)
```

```sql
DESCRIBE Orders;
```

```bash
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| OrderID     | int         | NO   | PRI | NULL    |       |
| CustomerID  | int         | YES  |     | NULL    |       |
| OrderDate   | date        | YES  |     | NULL    |       |
| ShipCountry | varchar(50) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela Orders

```sql
INSERT INTO Orders (OrderID, CustomerID, OrderDate, ShipCountry)
VALUES
    (1, 1, '2023-01-15', 'Germany'),
    (2, 2, '2023-02-20', 'Mexico'),
    (3, 3, '2023-03-25', 'Mexico'),
    (4, 4, '2023-04-10', 'UK'),
    (5, 5, '2023-05-05', 'Sweden'),
    (6, 1, '2023-06-15', 'Germany'),
    (7, 2, '2023-07-20', 'Mexico');
```

```bash
Query OK, 7 rows affected (0.07 sec)
Records: 7  Duplicates: 0  Warnings: 0
```

Contando o número de países distintos na tabela Orders
Esta consulta é compatível com a maioria dos bancos de dados, incluindo MS Access

```sql
SELECT COUNT(DISTINCT ShipCountry) AS DistinctCountries
FROM Orders;
```

```bash
+-------------------+
| DistinctCountries |
+-------------------+
|                 4 |
+-------------------+
1 row in set (0.00 sec)
```

Excluindo a tabela Orders (apenas para fins de exemplo)

```sql
DROP TABLE Orders;
```

```bash
Query OK, 0 rows affected (0.73 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL WHERE Clause

A cláusula WHERE é usada para filtrar registros. É usado para extrair apenas os registros que atendem a uma condição especificada.

Criando a tabela User

```sql
CREATE TABLE User (
    ID INT PRIMARY KEY,
    Nome VARCHAR(50),
    Idade INT,
    Salario DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.52 sec)
```

```sql
DESCRIBE User;
```

output

```bash
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| ID      | int           | NO   | PRI | NULL    |       |
| Nome    | varchar(50)   | YES  |     | NULL    |       |
| Idade   | int           | YES  |     | NULL    |       |
| Salario | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela

```sql
INSERT INTO User (ID, Nome, Idade, Salario) VALUES
(1, 'Alice', 25, 50000.00),
(2, 'Bob', 35, 75000.00),
(3, 'Charlie', 28, 60000.00),
(4, 'David', 40, 90000.00),
(5, 'Eva', 22, 45000.00),
(6, 'Frank', 30, 70000.00);
```

output

```bash
Query OK, 6 rows affected (0.12 sec)
Records: 6  Duplicates: 0  Warnings: 0
```

Selecionando Pessoas com Idade Superior a 30:

```sql
SELECT * FROM User
WHERE Idade > 30;
```

output

```bash
+----+-------+-------+----------+
| ID | Nome  | Idade | Salario  |
+----+-------+-------+----------+
|  2 | Bob   |    35 | 75000.00 |
|  4 | David |    40 | 90000.00 |
+----+-------+-------+----------+
2 rows in set (0.00 sec)
```

Selecionando Pessoas com Salário Menor ou Igual a 60000:

```sql
SELECT * FROM User
WHERE Salario <= 60000;
```

output

```bash
+----+---------+-------+----------+
| ID | Nome    | Idade | Salario  |
+----+---------+-------+----------+
|  1 | Alice   |    25 | 50000.00 |
|  3 | Charlie |    28 | 60000.00 |
|  5 | Eva     |    22 | 45000.00 |
+----+---------+-------+----------+
3 rows in set (0.00 sec)
```

Selecionando Pessoas com Nomes que Não São "Eva":

```sql
SELECT * FROM User
WHERE Nome <> 'Eva';
```

output

```bash
+----+---------+-------+----------+
| ID | Nome    | Idade | Salario  |
+----+---------+-------+----------+
|  1 | Alice   |    25 | 50000.00 |
|  2 | Bob     |    35 | 75000.00 |
|  3 | Charlie |    28 | 60000.00 |
|  4 | David   |    40 | 90000.00 |
|  6 | Frank   |    30 | 70000.00 |
+----+---------+-------+----------+
5 rows in set (0.00 sec)
```

Selecionando Pessoas com Idades Entre 25 e 35:

```sql
SELECT * FROM User
WHERE Idade BETWEEN 25 AND 35;
```

output

```bash
+----+---------+-------+----------+
| ID | Nome    | Idade | Salario  |
+----+---------+-------+----------+
|  1 | Alice   |    25 | 50000.00 |
|  2 | Bob     |    35 | 75000.00 |
|  3 | Charlie |    28 | 60000.00 |
|  6 | Frank   |    30 | 70000.00 |
+----+---------+-------+----------+
4 rows in set (0.00 sec)
```

Selecionando Pessoas com Nomes que Começam com "A":

```sql
SELECT * FROM User
WHERE Nome LIKE 'A%';
```

output

```bash
+----+-------+-------+----------+
| ID | Nome  | Idade | Salario  |
+----+-------+-------+----------+
|  1 | Alice |    25 | 50000.00 |
+----+-------+-------+----------+
1 row in set (0.00 sec)
```

Selecionando Pessoas com IDs 1, 3 e 5:

```sql
SELECT * FROM User
WHERE ID IN (1, 3, 5);
```

output

```bash
+----+---------+-------+----------+
| ID | Nome    | Idade | Salario  |
+----+---------+-------+----------+
|  1 | Alice   |    25 | 50000.00 |
|  3 | Charlie |    28 | 60000.00 |
|  5 | Eva     |    22 | 45000.00 |
+----+---------+-------+----------+
3 rows in set (0.00 sec)
```

```sql
DROP TABLE User;
```

output

```bash
Query OK, 0 rows affected (1.33 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL ORDER BY

A palavra-chave ORDER BY é usada para classificar o conjunto de resultados em ordem crescente ou decrescente.

Criando a tabela Products

```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    Price DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.47 sec)
```

```sql
DESCRIBE Products;
```

output

```bash
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| ProductID   | int           | NO   | PRI | NULL    |       |
| ProductName | varchar(50)   | YES  |     | NULL    |       |
| Price       | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela Products

```sql
INSERT INTO Products (ProductID, ProductName, Price)
VALUES
    (1, 'Product A', 19.99),
    (2, 'Product B', 29.99),
    (3, 'Product C', 14.99),
    (4, 'Product D', 39.99),
    (5, 'Product E', 9.99);
```

output

```bash
Query OK, 5 rows affected (0.10 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Criando a tabela Orders

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATE,
    ShipCountry VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (0.72 sec)
```

```sql
DESCRIBE Orders;
```

output

```bash
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| OrderID     | int         | NO   | PRI | NULL    |       |
| CustomerID  | int         | YES  |     | NULL    |       |
| OrderDate   | date        | YES  |     | NULL    |       |
| ShipCountry | varchar(50) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Adicionando a coluna ProductID à tabela Orders

```sql
ALTER TABLE Orders
ADD ProductID INT;
```

output

```bash
Query OK, 0 rows affected (0.34 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Inserindo alguns dados na tabela Orders

```sql
INSERT INTO Orders (OrderID, CustomerID, OrderDate, ShipCountry, ProductID)
VALUES
    (1, 1, '2023-01-15', 'Germany', 2),
    (2, 2, '2023-02-20', 'Mexico', 4),
    (3, 3, '2023-03-25', 'Mexico', 1),
    (4, 4, '2023-04-10', 'UK', 3),
    (5, 5, '2023-05-05', 'Sweden', 5),
    (6, 1, '2023-06-15', 'Germany', 2),
    (7, 2, '2023-07-20', 'Mexico', 4);
```

output

```bash
Query OK, 7 rows affected (0.15 sec)
Records: 7  Duplicates: 0  Warnings: 0
```

Selecionando os pedidos ordenados por OrderDate

```sql
SELECT *
FROM Orders
ORDER BY OrderDate;
```

output

```bash
+---------+------------+------------+-------------+-----------+
| OrderID | CustomerID | OrderDate  | ShipCountry | ProductID |
+---------+------------+------------+-------------+-----------+
|       1 |          1 | 2023-01-15 | Germany     |         2 |
|       2 |          2 | 2023-02-20 | Mexico      |         4 |
|       3 |          3 | 2023-03-25 | Mexico      |         1 |
|       4 |          4 | 2023-04-10 | UK          |         3 |
|       5 |          5 | 2023-05-05 | Sweden      |         5 |
|       6 |          1 | 2023-06-15 | Germany     |         2 |
|       7 |          2 | 2023-07-20 | Mexico      |         4 |
+---------+------------+------------+-------------+-----------+
7 rows in set (0.00 sec)
```

```sql
DROP TABLE Orders;
DROP TABLE Products;
```

output

```bash
Query OK, 0 rows affected (0.50 sec)
```

#### DESC

Criando a tabela Products

```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    Price DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.60 sec)
```

```sql
DESCRIBE Products;
```

output

```bash
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| ProductID   | int           | NO   | PRI | NULL    |       |
| ProductName | varchar(50)   | YES  |     | NULL    |       |
| Price       | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela Products

```sql
INSERT INTO Products (ProductID, ProductName, Price)
VALUES
    (1, 'Product A', 19.99),
    (2, 'Product B', 29.99),
    (3, 'Product C', 14.99),
    (4, 'Product D', 39.99),
    (5, 'Product E', 9.99);
```

output

```bash
Query OK, 5 rows affected (0.12 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionando os produtos ordenados por preço do mais alto para o mais baixo

```sql
SELECT *
FROM Products
ORDER BY Price DESC;
```

output

```bash
+-----------+-------------+-------+
| ProductID | ProductName | Price |
+-----------+-------------+-------+
|         4 | Product D   | 39.99 |
|         2 | Product B   | 29.99 |
|         1 | Product A   | 19.99 |
|         3 | Product C   | 14.99 |
|         5 | Product E   |  9.99 |
+-----------+-------------+-------+
5 rows in set (0.00 sec)
```

```sql
DROP TABLE Products;
```

output

```bash
Query OK, 0 rows affected (0.43 sec)
```

**[:arrow_up: back to top](#índice)**

#### Order Alphabetically

Para valores de string, a palavra-chave ORDER BY será ordenada em ordem alfabética:.

Criando a tabela Products

```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    Price DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.64 sec)
```

```sql
DESCRIBE Products;
```

output

```bash
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| ProductID   | int           | NO   | PRI | NULL    |       |
| ProductName | varchar(50)   | YES  |     | NULL    |       |
| Price       | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela Products

```sql
INSERT INTO Products (ProductID, ProductName, Price)
VALUES
    (1, 'Product A', 19.99),
    (2, 'Product B', 29.99),
    (3, 'Product C', 14.99),
    (4, 'Product D', 39.99),
    (5, 'Product E', 9.99);
```

output

```bash
Query OK, 5 rows affected (0.10 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionando os produtos ordenados alfabeticamente por nome

```sql
SELECT *
FROM Products
ORDER BY ProductName;
```

output

```bash
+-----------+-------------+-------+
| ProductID | ProductName | Price |
+-----------+-------------+-------+
|         1 | Product A   | 19.99 |
|         2 | Product B   | 29.99 |
|         3 | Product C   | 14.99 |
|         4 | Product D   | 39.99 |
|         5 | Product E   |  9.99 |
+-----------+-------------+-------+
5 rows in set (0.00 sec)
```

```sql
DROP TABLE Products;
```

output

```bash
Query OK, 0 rows affected (0.43 sec)
```

**[:arrow_up: back to top](#índice)**

#### Alphabetically DESC

Criando a tabela Products

```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    Price DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (1.33 sec)
```

```sql
DESCRIBE Products;
```

output

```bash
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| ProductID   | int           | NO   | PRI | NULL    |       |
| ProductName | varchar(50)   | YES  |     | NULL    |       |
| Price       | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela Products

```sql
INSERT INTO Products (ProductID, ProductName, Price)
VALUES
    (1, 'Product C', 19.99),
    (2, 'Product A', 29.99),
    (3, 'Product E', 14.99),
    (4, 'Product B', 39.99),
    (5, 'Product D', 9.99);
```

output

```bash
Query OK, 5 rows affected (0.14 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionando os produtos ordenados alfabeticamente pelo nome em ordem reversa

```sql
SELECT *
FROM Products
ORDER BY ProductName DESC;
```

output

```bash
+-----------+-------------+-------+
| ProductID | ProductName | Price |
+-----------+-------------+-------+
|         3 | Product E   | 14.99 |
|         5 | Product D   |  9.99 |
|         1 | Product C   | 19.99 |
|         4 | Product B   | 39.99 |
|         2 | Product A   | 29.99 |
+-----------+-------------+-------+
5 rows in set (0.00 sec)
```

```sql
DROP TABLE Products;
```

output

```bash
Query OK, 0 rows affected (0.67 sec)
```

**[:arrow_up: back to top](#índice)**

#### ORDER BY Several Columns

Criando a tabela Customers

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    Country VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (0.99 sec)
```

```SQL
DESCRIBE Customers;
```

output

```bash
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| CustomerID   | int         | NO   | PRI | NULL    |       |
| CustomerName | varchar(50) | YES  |     | NULL    |       |
| Country      | varchar(50) | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela Customers

```sql
INSERT INTO Customers (CustomerID, CustomerName, Country)
VALUES
    (1, 'Customer C', 'Brazil'),
    (2, 'Customer A', 'USA'),
    (3, 'Customer E', 'Canada'),
    (4, 'Customer B', 'USA'),
    (5, 'Customer D', 'Brazil');
```

output

```bash
Query OK, 5 rows affected (0.16 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionando os clientes ordenados alfabeticamente pelo nome em ordem reversa e, em caso de empate, pelo país

```sql
SELECT *
FROM Customers
ORDER BY CustomerName DESC, Country DESC;
```

output

```bash
+------------+--------------+---------+
| CustomerID | CustomerName | Country |
+------------+--------------+---------+
|          3 | Customer E   | Canada  |
|          5 | Customer D   | Brazil  |
|          1 | Customer C   | Brazil  |
|          4 | Customer B   | USA     |
|          2 | Customer A   | USA     |
+------------+--------------+---------+
5 rows in set (0.00 sec)
```

```sql
DROP TABLE Customers;
```

output

```bash
Query OK, 0 rows affected (0.32 sec)
```

**[:arrow_up: back to top](#índice)**

#### Using Both ASC and DESC

Criando a tabela Customers

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    Country VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (0.76 sec)
```

```SQL
DESCRIBE Customers;
```

output

```bash
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| CustomerID   | int         | NO   | PRI | NULL    |       |
| CustomerName | varchar(50) | YES  |     | NULL    |       |
| Country      | varchar(50) | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela Customers

```sql
INSERT INTO Customers (CustomerID, CustomerName, Country)
VALUES
    (1, 'Customer C', 'Brazil'),
    (2, 'Customer A', 'USA'),
    (3, 'Customer E', 'Canada'),
    (4, 'Customer B', 'USA'),
    (5, 'Customer D', 'Brazil');
```

output

```bash
Query OK, 5 rows affected (0.08 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionando os clientes ordenados pelo país em ordem ascendente e, em caso de empate, pelo nome do cliente em ordem descendente

```sql
SELECT *
FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

output

```bash
+------------+--------------+---------+
| CustomerID | CustomerName | Country |
+------------+--------------+---------+
|          5 | Customer D   | Brazil  |
|          1 | Customer C   | Brazil  |
|          3 | Customer E   | Canada  |
|          4 | Customer B   | USA     |
|          2 | Customer A   | USA     |
+------------+--------------+---------+
5 rows in set (0.00 sec)
```

```sql
DROP TABLE Customers;
```

output

```bash
Query OK, 0 rows affected (0.69 sec)
```

**[:arrow_up: back to top](#índice)**

## Operadores Lógicos

**[:arrow_up: back to top](#índice)**

### SQL AND Operator

O operador AND é usado para filtrar registros com base em mais de uma condição, como se você desejasse retornar todos os clientes da Espanha que começam com a letra 'G':

```sql
CREATE TABLE Customers (
    IDCliente INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    Country VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (0.88 sec)
```

```SQL
DESCRIBE Customers;
```

output

```bash
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| IDCliente    | int         | NO   | PRI | NULL    |       |
| CustomerName | varchar(50) | YES  |     | NULL    |       |
| Country      | varchar(50) | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

```sql
INSERT INTO Customers (IDCliente, CustomerName, Country)
VALUES
(1, 'Gustavo', 'Spain'),
(2, 'Ana', 'Spain'),
(3, 'George', 'Germany'),
(4, 'Gabriel', 'Spain'),
(5, 'Grace', 'Italy');
```

output

```bash
Query OK, 5 rows affected (0.20 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

```sql
SELECT *
FROM Customers
WHERE Country = 'Spain' AND CustomerName LIKE 'G%';
```

output

```bash
+-----------+--------------+---------+
| IDCliente | CustomerName | Country |
+-----------+--------------+---------+
|         1 | Gustavo      | Spain   |
|         4 | Gabriel      | Spain   |
+-----------+--------------+---------+
2 rows in set (0.00 sec)
```

```sql
DROP TABLE Customers;
```

output

```bash
Query OK, 0 rows affected (0.70 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL OR Operator

O operador OR é usado para filtrar registros com base em mais de uma condição, como se você deseja retornar todos os clientes da Alemanha, mas também os da Espanha:

Criando uma tabela de Produtos

```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    Category VARCHAR(50),
    Price DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.93 sec)
```

```SQL
DESCRIBE Products;
```

output

```bash
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| ProductID   | int           | NO   | PRI | NULL    |       |
| ProductName | varchar(50)   | YES  |     | NULL    |       |
| Category    | varchar(50)   | YES  |     | NULL    |       |
| Price       | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
4 rows in set (0.01 sec)
```

Inserindo alguns dados na tabela de Produtos

```sql
INSERT INTO Products (ProductID, ProductName, Category, Price)
VALUES
(1, 'Laptop', 'Electronics', 1200.00),
(2, 'Desk Chair', 'Furniture', 150.00),
(3, 'Coffee Maker', 'Appliances', 50.00),
(4, 'Running Shoes', 'Sports', 80.00),
(5, 'Desk Lamp', 'Furniture', 30.00);
```

output

```bash
Query OK, 5 rows affected (0.21 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Consulta para selecionar produtos da categoria 'Electronics' com preço superior a $100 ou produtos da categoria 'Furniture'

```sql
SELECT *
FROM Products
WHERE (Category = 'Electronics' AND Price > 100.00) OR Category = 'Furniture';
```

output

```bash
+-----------+-------------+-------------+---------+
| ProductID | ProductName | Category    | Price   |
+-----------+-------------+-------------+---------+
|         1 | Laptop      | Electronics | 1200.00 |
|         2 | Desk Chair  | Furniture   |  150.00 |
|         5 | Desk Lamp   | Furniture   |   30.00 |
+-----------+-------------+-------------+---------+
3 rows in set (0.00 sec)
```

Excluindo a tabela de Produtos após a conclusão da consulta

```sql
DROP TABLE Products;
```

output

```bash
Query OK, 0 rows affected (0.71 sec)
```

**[:arrow_up: back to top](#índice)**

### NOT Operator

O operador NOT é usado em combinação com outros operadores para fornecer o resultado oposto, também chamado de resultado negativo.

Criando uma tabela de Funcionários

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(50),
    Department VARCHAR(50),
    Salary DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.67 sec)
```

```sql
DESCRIBE Employees;
```

output

```bash
+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| EmployeeID   | int           | NO   | PRI | NULL    |       |
| EmployeeName | varchar(50)   | YES  |     | NULL    |       |
| Department   | varchar(50)   | YES  |     | NULL    |       |
| Salary       | decimal(10,2) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela de Funcionários

```sql
INSERT INTO Employees (EmployeeID, EmployeeName, Department, Salary)
VALUES
(1, 'Alice', 'HR', 50000.00),
(2, 'Bob', 'IT', 60000.00),
(3, 'Charlie', 'Finance', 70000.00),
(4, 'David', 'Marketing', 55000.00),
(5, 'Eva', 'IT', 62000.00);
```

output

```bash
Query OK, 5 rows affected (0.25 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Exemplo com NOT LIKE: Selecionar funcionários cujo nome não começa com a letra 'A'

```sql
SELECT *
FROM Employees
WHERE EmployeeName NOT LIKE 'A%';
```

output

```bash
+------------+--------------+------------+----------+
| EmployeeID | EmployeeName | Department | Salary   |
+------------+--------------+------------+----------+
|          2 | Bob          | IT         | 60000.00 |
|          3 | Charlie      | Finance    | 70000.00 |
|          4 | David        | Marketing  | 55000.00 |
|          5 | Eva          | IT         | 62000.00 |
+------------+--------------+------------+----------+
4 rows in set (0.00 sec)
```

Exemplo com NOT BETWEEN: Selecionar funcionários cujo ID não está entre 2 e 4

```sql
SELECT *
FROM Employees
WHERE EmployeeID NOT BETWEEN 2 AND 4;
```

output

```bash
+------------+--------------+------------+----------+
| EmployeeID | EmployeeName | Department | Salary   |
+------------+--------------+------------+----------+
|          1 | Alice        | HR         | 50000.00 |
|          5 | Eva          | IT         | 62000.00 |
+------------+--------------+------------+----------+
2 rows in set (0.00 sec)
```

Exemplo com NOT IN: Selecionar funcionários que não são do departamento 'IT' ou 'HR'

```sql
SELECT *
FROM Employees
WHERE Department NOT IN ('IT', 'HR');
```

output

```bash
+------------+--------------+------------+----------+
| EmployeeID | EmployeeName | Department | Salary   |
+------------+--------------+------------+----------+
|          3 | Charlie      | Finance    | 70000.00 |
|          4 | David        | Marketing  | 55000.00 |
+------------+--------------+------------+----------+
2 rows in set (0.00 sec)
```

Exemplo com NOT Greater Than: Selecionar funcionários com salário não superior a $60000

```sql
SELECT *
FROM Employees
WHERE NOT Salary > 60000.00;
-- Ou usando a notação !>
-- SELECT *
-- FROM Employees
-- WHERE Salary !> 60000.00;
```

output

```bash
+------------+--------------+------------+----------+
| EmployeeID | EmployeeName | Department | Salary   |
+------------+--------------+------------+----------+
|          1 | Alice        | HR         | 50000.00 |
|          2 | Bob          | IT         | 60000.00 |
|          4 | David        | Marketing  | 55000.00 |
+------------+--------------+------------+----------+
3 rows in set (0.00 sec)
```

Exemplo com NOT Less Than: Selecionar funcionários com salário não inferior a $60000

```sql
SELECT *
FROM Employees
WHERE NOT Salary < 60000.00;
-- Ou usando a notação !<
-- SELECT *
-- FROM Employees
-- WHERE Salary !< 60000.00;
```

output

```bash
+------------+--------------+------------+----------+
| EmployeeID | EmployeeName | Department | Salary   |
+------------+--------------+------------+----------+
|          2 | Bob          | IT         | 60000.00 |
|          3 | Charlie      | Finance    | 70000.00 |
|          5 | Eva          | IT         | 62000.00 |
+------------+--------------+------------+----------+
3 rows in set (0.00 sec)
```

Excluindo a tabela de Funcionários após a conclusão dos exemplos

```sql
DROP TABLE Employees;
```

output

```bash
Query OK, 0 rows affected (0.33 sec)
```

**[:arrow_up: back to top](#índice)**

## Manipulação de Dados

### SQL INSERT INTO Statement

A instrução INSERT INTO é usada para inserir novos registros em uma tabela.

Criando uma tabela de Produtos

```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    Category VARCHAR(50),
    Price DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.48 sec)
```

```sql
DESCRIBE Products;
```

output

```bash
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| ProductID   | int           | NO   | PRI | NULL    |       |
| ProductName | varchar(50)   | YES  |     | NULL    |       |
| Category    | varchar(50)   | YES  |     | NULL    |       |
| Price       | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Exemplo de INSERT INTO especificando nomes de colunas e valores

```sql
INSERT INTO Products (ProductID, ProductName, Category, Price)
VALUES (1, 'Laptop', 'Electronics', 1200.00);
```

output

```bash
Query OK, 1 row affected (0.10 sec)
```

Ou, usando a segunda forma, inserindo valores para todas as colunas sem especificar os nomes das colunas

```sql
INSERT INTO Products
VALUES (2, 'Desk Chair', 'Furniture', 150.00);
```

output

```bash
Query OK, 1 row affected (0.15 sec)
```

```sql
DROP TABLE Products;
```

output

```bash
Query OK, 0 rows affected (0.75 sec)
```

**[:arrow_up: back to top](#índice)**

### NULL

Um campo com valor NULL é um campo sem valor.

Se um campo de uma tabela for opcional, é possível inserir um novo registro ou atualizar um registro sem adicionar um valor a este campo. Então, o campo será salvo com valor NULL.

Criando uma tabela de Pedidos

```SQL
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    OrderDate DATE,
    TotalAmount DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (1.04 sec)
```

```SQL
DESCRIBE Orders;
```

output

```bash
+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| OrderID      | int           | NO   | PRI | NULL    |       |
| CustomerName | varchar(50)   | YES  |     | NULL    |       |
| OrderDate    | date          | YES  |     | NULL    |       |
| TotalAmount  | decimal(10,2) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela de Pedidos, incluindo valores NULL

```SQL
INSERT INTO Orders (OrderID, CustomerName, OrderDate, TotalAmount)
VALUES
(1, 'Alice', '2023-01-15', 100.00),
(2, 'Bob', NULL, 150.00),
(3, 'Charlie', '2023-02-20', NULL),
(4, 'David', '2023-03-10', 200.00),
(5, 'Eva', NULL, NULL);
```

output

```bash
Query OK, 5 rows affected (0.08 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Exemplo de como testar valores NULL usando IS NULL
Seleciona pedidos onde a data do pedido é desconhecida (NULL)

```SQL
SELECT *
FROM Orders
WHERE OrderDate IS NULL;
```

output

```bash
+---------+--------------+-----------+-------------+
| OrderID | CustomerName | OrderDate | TotalAmount |
+---------+--------------+-----------+-------------+
|       2 | Bob          | NULL      |      150.00 |
|       5 | Eva          | NULL      |        NULL |
+---------+--------------+-----------+-------------+
2 rows in set (0.00 sec)
```

Exemplo de como testar valores NÃO NULL usando IS NOT NULL
Seleciona pedidos onde o valor total do pedido é conhecido (NÃO NULL)

```SQL
SELECT *
FROM Orders
WHERE TotalAmount IS NOT NULL;
```

output

```bash
+---------+--------------+------------+-------------+
| OrderID | CustomerName | OrderDate  | TotalAmount |
+---------+--------------+------------+-------------+
|       1 | Alice        | 2023-01-15 |      100.00 |
|       2 | Bob          | NULL       |      150.00 |
|       4 | David        | 2023-03-10 |      200.00 |
+---------+--------------+------------+-------------+
3 rows in set (0.00 sec)
```

```SQL
DROP TABLE Orders;
```

output

```bash
Query OK, 0 rows affected (0.39 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL UPDATE Statement

A instrução UPDATE é usada para modificar os registros existentes em uma tabela.

Criando uma tabela de Estoque

```sql
CREATE TABLE Inventory (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    QuantityInStock INT
);
```

output

```bash
Query OK, 0 rows affected (0.50 sec)
```

```sql
DESCRIBE Inventory;
```

output

```bash
+-----------------+-------------+------+-----+---------+-------+
| Field           | Type        | Null | Key | Default | Extra |
+-----------------+-------------+------+-----+---------+-------+
| ProductID       | int         | NO   | PRI | NULL    |       |
| ProductName     | varchar(50) | YES  |     | NULL    |       |
| QuantityInStock | int         | YES  |     | NULL    |       |
+-----------------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela de Estoque

```sql
INSERT INTO Inventory (ProductID, ProductName, QuantityInStock)
VALUES
(1, 'Laptop', 50),
(2, 'Desk Chair', 30),
(3, 'Coffee Maker', 20),
(4, 'Running Shoes', 40),
(5, 'Desk Lamp', 25);
```

output

```bash
Query OK, 5 rows affected (0.18 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Exemplo de como atualizar a quantidade em estoque para um produto específico

```sql
UPDATE Inventory
SET QuantityInStock = 60
WHERE ProductName = 'Laptop';
```

output

```bash
Query OK, 1 row affected (0.08 sec)
Rows matched: 1  Changed: 1  Warnings: 0
```

Exemplo de como decrementar a quantidade em estoque para produtos com quantidade superior a 30

```sql
UPDATE Inventory
SET QuantityInStock = QuantityInStock - 10
WHERE QuantityInStock > 30;
```

output

```bash
Query OK, 2 rows affected (0.07 sec)
Rows matched: 2  Changed: 2  Warnings: 0
```

```sql
DROP TABLE Inventory;
```

output

```bash
Query OK, 0 rows affected (0.34 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL DELETE Statement

A instrução DELETE é usada para excluir registros existentes em uma tabela.

Criando uma tabela de Clientes

```SQL
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    Country VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (1.11 sec)
```

Inserindo alguns dados na tabela de Clientes

```SQL
INSERT INTO Customers (CustomerID, CustomerName, Country)
VALUES
(1, 'Alice', 'USA'),
(2, 'Bob', 'Canada'),
(3, 'Charlie', 'UK'),
(4, 'David', 'Australia'),
(5, 'Eva', 'Germany');
```

output

```bash
Query OK, 5 rows affected (0.22 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Exemplo de como excluir um cliente específico da tabela

```SQL
DELETE FROM Customers
WHERE CustomerID = 2;
```

output

```bash
Query OK, 1 row affected (0.11 sec)
```

Exemplo de como excluir todos os clientes de um país específico da tabela

```SQL
DELETE FROM Customers
WHERE Country = 'UK';
```

output

```bash
Query OK, 1 row affected (0.10 sec)
```

```SQL
select * from Customers;
```

```bash
+------------+--------------+-----------+
| CustomerID | CustomerName | Country   |
+------------+--------------+-----------+
|          1 | Alice        | USA       |
|          4 | David        | Australia |
|          5 | Eva          | Germany   |
+------------+--------------+-----------+
3 rows in set (0.00 sec)
```

```SQL
DROP TABLE Customers;
```

output

```bash
Query OK, 0 rows affected (0.46 sec)
```

**[:arrow_up: back to top](#índice)**

## Consultas Avançadas

### SQL SELECT TOP Clause

A cláusula SELECT TOP é usada para especificar o número de registros a serem retornados.

A cláusula SELECT TOP é útil em tabelas grandes com milhares de registros. O retorno de um grande número de registros pode afetar o desempenho.

Criar uma tabela fictícia de pedidos

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATE,
    ProductName VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (0.60 sec)
```

```sql
DESCRIBE Orders;
```

output

```bash
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| OrderID     | int         | NO   | PRI | NULL    |       |
| CustomerID  | int         | YES  |     | NULL    |       |
| OrderDate   | date        | YES  |     | NULL    |       |
| ProductName | varchar(50) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserir alguns dados fictícios

```sql
INSERT INTO Orders (OrderID, CustomerID, OrderDate, ProductName)
VALUES
    (1, 101, '2023-11-01', 'Product A'),
    (2, 102, '2023-11-02', 'Product B'),
    (3, 103, '2023-11-03', 'Product C'),
    (4, 104, '2023-11-04', 'Product D'),
    (5, 105, '2023-11-05', 'Product E');
```

output

```bash
Query OK, 5 rows affected (0.10 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionar os três pedidos mais recentes

```sql
SELECT * FROM Orders
ORDER BY OrderDate DESC
LIMIT 3;
```

output

```bash
+---------+------------+------------+-------------+
| OrderID | CustomerID | OrderDate  | ProductName |
+---------+------------+------------+-------------+
|       5 |        105 | 2023-11-05 | Product E   |
|       4 |        104 | 2023-11-04 | Product D   |
|       3 |        103 | 2023-11-03 | Product C   |
+---------+------------+------------+-------------+
3 rows in set (0.00 sec)
```

```SQL
DROP TABLE Orders;
```

output

```bash
Query OK, 0 rows affected (0.46 sec)
```

**[:arrow_up: back to top](#índice)**

#### LIMIT

Criar uma tabela fictícia de clientes

```SQL
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100)
);
```

output

```bash
Query OK, 0 rows affected (0.60 sec)
```

```sql
DESCRIBE Customers;
```

output

```bash
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| CustomerID | int          | NO   | PRI | NULL    |       |
| FirstName  | varchar(50)  | YES  |     | NULL    |       |
| LastName   | varchar(50)  | YES  |     | NULL    |       |
| Email      | varchar(100) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserir alguns dados fictícios

```SQL
INSERT INTO Customers (CustomerID, FirstName, LastName, Email)
VALUES
    (1, 'John', 'Doe', 'john.doe@example.com'),
    (2, 'Jane', 'Smith', 'jane.smith@example.com'),
    (3, 'Bob', 'Johnson', 'bob.johnson@example.com'),
    (4, 'Alice', 'Williams', 'alice.williams@example.com'),
    (5, 'Charlie', 'Brown', 'charlie.brown@example.com');
```

output

```bash
Query OK, 5 rows affected (0.12 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionar os três primeiros clientes

```SQL
SELECT * FROM Customers
LIMIT 3;
```

output

```bash
+------------+-----------+----------+-------------------------+
| CustomerID | FirstName | LastName | Email                   |
+------------+-----------+----------+-------------------------+
|          1 | John      | Doe      | john.doe@example.com    |
|          2 | Jane      | Smith    | jane.smith@example.com  |
|          3 | Bob       | Johnson  | bob.johnson@example.com |
+------------+-----------+----------+-------------------------+
3 rows in set (0.00 sec)
```

```SQL
DROP TABLE Customers;
```

output

```bash
Query OK, 0 rows affected (0.42 sec)
```

**[:arrow_up: back to top](#índice)**

#### ADD a WHERE CLAUSE

Criar uma tabela fictícia de clientes

```SQL
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100),
    Country VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (1.45 sec)
```

```sql
DESCRIBE Customers;
```

output

```bash
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| CustomerID | int          | NO   | PRI | NULL    |       |
| FirstName  | varchar(50)  | YES  |     | NULL    |       |
| LastName   | varchar(50)  | YES  |     | NULL    |       |
| Email      | varchar(100) | YES  |     | NULL    |       |
| Country    | varchar(50)  | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Inserir alguns dados fictícios

```SQL
INSERT INTO Customers (CustomerID, FirstName, LastName, Email, Country)
VALUES
    (1, 'Hans', 'Müller', 'hans.mueller@example.com', 'Germany'),
    (2, 'Maria', 'Schmidt', 'maria.schmidt@example.com', 'Austria'),
    (3, 'Günther', 'Fischer', 'guenther.fischer@example.com', 'Germany'),
    (4, 'Sophie', 'Weber', 'sophie.weber@example.com', 'Germany'),
    (5, 'Matthias', 'Koch', 'matthias.koch@example.com', 'Switzerland');
```

output

```bash
Query OK, 5 rows affected (0.11 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionar os três primeiros clientes da Alemanha

```SQL
SELECT * FROM Customers
WHERE Country = 'Germany'
LIMIT 3;
```

output

```bash
+------------+-----------+----------+------------------------------+---------+
| CustomerID | FirstName | LastName | Email                        | Country |
+------------+-----------+----------+------------------------------+---------+
|          1 | Hans      | Mller    | hans.mueller@example.com     | Germany |
|          3 | Gnther    | Fischer  | guenther.fischer@example.com | Germany |
|          4 | Sophie    | Weber    | sophie.weber@example.com     | Germany |
+------------+-----------+----------+------------------------------+---------+
3 rows in set (0.00 sec)
```

```sql
DROP TABLE Customers;
```

output

```bash
Query OK, 0 rows affected (0.41 sec)
```

**[:arrow_up: back to top](#índice)**

#### ADD the ORDER BY Keyword

Criar uma tabela fictícia de clientes

```SQL
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(100),
    Email VARCHAR(100),
    Country VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (0.58 sec)
```

```sql
DESCRIBE Customers;
```

output

```bash
+--------------+--------------+------+-----+---------+-------+
| Field        | Type         | Null | Key | Default | Extra |
+--------------+--------------+------+-----+---------+-------+
| CustomerID   | int          | NO   | PRI | NULL    |       |
| CustomerName | varchar(100) | YES  |     | NULL    |       |
| Email        | varchar(100) | YES  |     | NULL    |       |
| Country      | varchar(50)  | YES  |     | NULL    |       |
+--------------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserir alguns dados fictícios

```SQL
INSERT INTO Customers (CustomerID, CustomerName, Email, Country)
VALUES
    (1, 'John Doe', 'john.doe@example.com', 'USA'),
    (2, 'Jane Smith', 'jane.smith@example.com', 'Canada'),
    (3, 'Bob Johnson', 'bob.johnson@example.com', 'UK'),
    (4, 'Alice Williams', 'alice.williams@example.com', 'Australia'),
    (5, 'Charlie Brown', 'charlie.brown@example.com', 'Germany');
```

output

```bash
Query OK, 5 rows affected (0.15 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionar os três clientes mais recentes

```SQL
SELECT * FROM Customers
ORDER BY CustomerID DESC
LIMIT 3;
```

output

```bash
+------------+----------------+----------------------------+-----------+
| CustomerID | CustomerName   | Email                      | Country   |
+------------+----------------+----------------------------+-----------+
|          5 | Charlie Brown  | charlie.brown@example.com  | Germany   |
|          4 | Alice Williams | alice.williams@example.com | Australia |
|          3 | Bob Johnson    | bob.johnson@example.com    | UK        |
+------------+----------------+----------------------------+-----------+
3 rows in set (0.00 sec)
```

```sql
DROP TABLE Customers;
```

output

```bash
Query OK, 0 rows affected (0.42 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL MIN() and MAX() Functions

A função MIN() retorna o menor valor da coluna selecionada.
A função MAX() retorna o maior valor da coluna selecionada.

Criar uma tabela fictícia de produtos

```SQL
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    Price DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (1.03 sec)
```

```sql
DESCRIBE Products;
```

output

```bash
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| ProductID   | int           | NO   | PRI | NULL    |       |
| ProductName | varchar(50)   | YES  |     | NULL    |       |
| Price       | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserir alguns dados fictícios

```SQL
INSERT INTO Products (ProductID, ProductName, Price)
VALUES
    (1, 'Product A', 19.99),
    (2, 'Product B', 29.99),
    (3, 'Product C', 14.99),
    (4, 'Product D', 39.99),
    (5, 'Product E', 24.99);
```

output

```bash
Query OK, 5 rows affected (0.20 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Encontrar o menor preço

```SQL
SELECT MIN(Price) AS LowestPrice
FROM Products;
```

output

```bash
+-------------+
| LowestPrice |
+-------------+
|       14.99 |
+-------------+
1 row in set (0.01 sec)
```

Encontrar o maior preço

```SQL
SELECT MAX(Price) AS HighestPrice
FROM Products;
```

output

```bash
+--------------+
| HighestPrice |
+--------------+
|        39.99 |
+--------------+
1 row in set (0.00 sec)
```

```SQL
DROP TABLE Products;
```

output

```bash
Query OK, 0 rows affected (0.56 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL COUNT() Function

A função COUNT() retorna o número de linhas que correspondem a um critério especificado.

Crie uma tabela de exemplo chamada Produtos

```sql
CREATE TABLE Produtos (
    IDProduto INT PRIMARY KEY,
    NomeProduto VARCHAR(255),
    Preco DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.59 sec)
```

```sql
DESCRIBE Produtos;
```

output

```bash
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| IDProduto   | int           | NO   | PRI | NULL    |       |
| NomeProduto | varchar(255)  | YES  |     | NULL    |       |
| Preco       | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
3 rows in set (0.01 sec)
```

Insira alguns dados de exemplo

```sql
INSERT INTO Produtos (IDProduto, NomeProduto, Preco)
VALUES
    (1, 'Produto A', 15.99),
    (2, 'Produto B', 25.50),
    (3, 'Produto C', 19.99),
    (4, 'Produto D', 25.50),
    (5, 'Produto E', 30.00);
```

output

```bash
Query OK, 5 rows affected (0.11 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Encontre o número total de produtos na tabela Produtos

```sql
SELECT COUNT(*) AS TotalProdutos
FROM Produtos;
```

output

```bash
+---------------+
| TotalProdutos |
+---------------+
|             5 |
+---------------+
1 row in set (0.00 sec)
```

Encontre o número de produtos onde o preço é maior que 20

```sql
SELECT COUNT(IDProduto) AS ProdutosCaros
FROM Produtos
WHERE Preco > 20;
```

output

```bash
+---------------+
| ProdutosCaros |
+---------------+
|             3 |
+---------------+
1 row in set (0.00 sec)
```

Quantos preços diferentes existem na tabela Produtos

```sql
SELECT COUNT(DISTINCT Preco) AS PrecosUnicos
FROM Produtos;
```

output

```bash
+--------------+
| PrecosUnicos |
+--------------+
|            4 |
+--------------+
1 row in set (0.00 sec)
```

```SQL
DROP TABLE Produtos;
```

output

```bash
Query OK, 0 rows affected (0.52 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL SUM() Function

A função SUM() retorna a soma total de uma coluna numérica.
Tabela de preços dos OrderDetails

```sql
CREATE TABLE OrderDetails (
    OrderID INT,
    ProductName VARCHAR(50),
    Quantity INT
);
```

output

```bash
Query OK, 0 rows affected (0.68 sec)
```

```sql
DESCRIBE OrderDetails;
```

output

```bash
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| OrderID     | int         | YES  |     | NULL    |       |
| ProductName | varchar(50) | YES  |     | NULL    |       |
| Quantity    | int         | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserir alguns dados de exemplo

```sql
INSERT INTO OrderDetails (OrderID, ProductName, Quantity)
VALUES 
    (1, 'ProductA', 10),
    (1, 'ProductB', 5),
    (2, 'ProductA', 8),
    (2, 'ProductC', 12),
    (3, 'ProductB', 7);
```

output

```bash
Query OK, 5 rows affected (0.15 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Retornar a soma de todas as quantidades na tabela OrderDetails

```sql
SELECT SUM(Quantity) AS TotalQuantity
FROM OrderDetails;
```

output

```bash
+---------------+
| TotalQuantity |
+---------------+
|            42 |
+---------------+
1 row in set (0.00 sec)
```

```sql
drop table OrderDetails;
```

output

```bash
Query OK, 0 rows affected (0.66 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL AVG() Function

A função AVG() retorna o valor médio de uma coluna numérica.

Criar uma tabela Products

```sql
CREATE TABLE Products (
    ProductID INT,
    ProductName VARCHAR(255),
    SupplierID INT,
    CategoryID INT,
    Unit VARCHAR(255),
    Price DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.63 sec)
```

Inserir dados de exemplo na tabela Products

```sql
INSERT INTO Products (ProductID, ProductName, SupplierID, CategoryID, Unit, Price)
VALUES
    (1, 'Chais', 1, 1, '10 caixas x 20 sacos', 18),
    (2, 'Chang', 1, 1, '24 - garrafas de 12 oz', 19),
    (3, 'Aniseed Syrup', 1, 2, '12 - garrafas de 550 ml', 10),
    (4, 'Chef Anton\'s Cajun Seasoning', 2, 2, '48 - frascos de 6 oz', 22),
    (5, 'Chef Anton\'s Gumbo Mix', 2, 2, '36 caixas', 21.35);
```

output

```bash
Query OK, 5 rows affected (0.15 sec)
Records: 5  Duplicates: 0  Warnings: 0

```

Exemplo: Encontrar o preço médio de todos os produtos

```sql
SELECT AVG(Price) AS preco_medio
FROM Products;
```

output

```bash
+-------------+
| preco_medio |
+-------------+
|   18.070000 |
+-------------+
1 row in set (0.00 sec)
```

Exemplo: Retornar o preço médio dos produtos na categoria 1

```sql
SELECT AVG(Price) AS preco_medio
FROM Products
WHERE CategoryID = 1;
```

output

```bash
+-------------+
| preco_medio |
+-------------+
|   18.500000 |
+-------------+
1 row in set (0.00 sec)
```

Retornar todos os produtos com preço superior ao preço médio

```sql
SELECT *
FROM Products
WHERE Price > (SELECT AVG(Price) FROM Products);
```

output

```bash
+-----------+------------------------------+------------+------------+------------------------+-------+
| ProductID | ProductName                  | SupplierID | CategoryID | Unit                   | Price |
+-----------+------------------------------+------------+------------+------------------------+-------+
|         2 | Chang                        |          1 |          1 | 24 - garrafas de 12 oz | 19.00 |
|         4 | Chef Anton's Cajun Seasoning |          2 |          2 | 48 - frascos de 6 oz   | 22.00 |
|         5 | Chef Anton's Gumbo Mix       |          2 |          2 | 36 caixas              | 21.35 |
+-----------+------------------------------+------------+------------+------------------------+-------+
3 rows in set (0.01 sec)
```

```sql
DROP TABLE Products;
```

output

```bash
Query OK, 0 rows affected (0.94 sec)
```

**[:arrow_up: back to top](#índice)**

## Operadores de Comparação

### SQL BETWEEN Operator

O operador BETWEEN seleciona valores dentro de um determinado intervalo. Os valores podem ser números, texto ou datas.

Criação de uma tabela de exemplo chamada Products

```sql
CREATE TABLE Products (
    ProductID INT,
    ProductName VARCHAR(255),
    SupplierID INT,
    CategoryID INT,
    Unit VARCHAR(255),
    Price DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.78 sec)
```

Inserção de dados de exemplo na tabela Products

```sql
INSERT INTO Products VALUES
    (1, 'Chais', 1, 1, '10 caixas x 20 sacos', 18),
    (2, 'Chang', 1, 1, '24 garrafas de 12 oz', 19),
    (3, 'Aniseed Syrup', 1, 2, '12 garrafas de 550 ml', 10),
    (4, 'Chef Anton''s Cajun Seasoning', 2, 2, '48 frascos de 6 oz', 22),
    (5, 'Chef Anton''s Gumbo Mix', 2, 2, '36 caixas', 21.35);
```

output

```bash
Query OK, 5 rows affected (0.15 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

Selecionar produtos com preço entre 10 e 20

```sql
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;
```

output

```bash
+-----------+---------------+------------+------------+-----------------------+-------+
| ProductID | ProductName   | SupplierID | CategoryID | Unit                  | Price |
+-----------+---------------+------------+------------+-----------------------+-------+
|         1 | Chais         |          1 |          1 | 10 caixas x 20 sacos  | 18.00 |
|         2 | Chang         |          1 |          1 | 24 garrafas de 12 oz  | 19.00 |
|         3 | Aniseed Syrup |          1 |          2 | 12 garrafas de 550 ml | 10.00 |
+-----------+---------------+------------+------------+-----------------------+-------+
3 rows in set (0.00 sec)
```

Selecionar produtos com preço NÃO entre 10 e 20

```sql
SELECT * FROM Products
WHERE Price NOT BETWEEN 10 AND 20;
```

output

```bash
+-----------+------------------------------+------------+------------+--------------------+-------+
| ProductID | ProductName                  | SupplierID | CategoryID | Unit               | Price |
+-----------+------------------------------+------------+------------+--------------------+-------+
|         4 | Chef Anton's Cajun Seasoning |          2 |          2 | 48 frascos de 6 oz | 22.00 |
|         5 | Chef Anton's Gumbo Mix       |          2 |          2 | 36 caixas          | 21.35 |
+-----------+------------------------------+------------+------------+--------------------+-------+
2 rows in set (0.00 sec)
```

Selecionar produtos com preço entre 10 e 20 e CategoryID em (1, 2, 3)

```sql
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20
AND CategoryID IN (1, 2, 3);
```

output

```bash
+-----------+---------------+------------+------------+-----------------------+-------+
| ProductID | ProductName   | SupplierID | CategoryID | Unit                  | Price |
+-----------+---------------+------------+------------+-----------------------+-------+
|         1 | Chais         |          1 |          1 | 10 caixas x 20 sacos  | 18.00 |
|         2 | Chang         |          1 |          1 | 24 garrafas de 12 oz  | 19.00 |
|         3 | Aniseed Syrup |          1 |          2 | 12 garrafas de 550 ml | 10.00 |
+-----------+---------------+------------+------------+-----------------------+-------+
3 rows in set (0.00 sec)
```

Selecionar produtos com ProductName entre 'Carnarvon Tigers' e 'Mozzarella di Giovanni'

```sql
-- (Ordenar por ProductName)
SELECT * FROM Products
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```

output

```bash
+-----------+------------------------------+------------+------------+----------------------+-------+
| ProductID | ProductName                  | SupplierID | CategoryID | Unit                 | Price |
+-----------+------------------------------+------------+------------+----------------------+-------+
|         1 | Chais                        |          1 |          1 | 10 caixas x 20 sacos | 18.00 |
|         2 | Chang                        |          1 |          1 | 24 garrafas de 12 oz | 19.00 |
|         4 | Chef Anton's Cajun Seasoning |          2 |          2 | 48 frascos de 6 oz   | 22.00 |
|         5 | Chef Anton's Gumbo Mix       |          2 |          2 | 36 caixas            | 21.35 |
+-----------+------------------------------+------------+------------+----------------------+-------+
4 rows in set (0.00 sec)
```

Selecionar produtos com ProductName entre 'Carnarvon Tigers' e 'Chef Anton''s Cajun Seasoning'

```sql
SELECT * FROM Products
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Chef Anton''s Cajun Seasoning'
ORDER BY ProductName;
```

output

```bash
+-----------+------------------------------+------------+------------+----------------------+-------+
| ProductID | ProductName                  | SupplierID | CategoryID | Unit                 | Price |
+-----------+------------------------------+------------+------------+----------------------+-------+
|         1 | Chais                        |          1 |          1 | 10 caixas x 20 sacos | 18.00 |
|         2 | Chang                        |          1 |          1 | 24 garrafas de 12 oz | 19.00 |
|         4 | Chef Anton's Cajun Seasoning |          2 |          2 | 48 frascos de 6 oz   | 22.00 |
+-----------+------------------------------+------------+------------+----------------------+-------+
```

Selecionar produtos com ProductName NÃO entre 'Carnarvon Tigers' e 'Mozzarella di Giovanni'

```sql
SELECT * FROM Products
WHERE ProductName NOT BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```

output

```bash
+-----------+---------------+------------+------------+-----------------------+-------+
| ProductID | ProductName   | SupplierID | CategoryID | Unit                  | Price |
+-----------+---------------+------------+------------+-----------------------+-------+
|         3 | Aniseed Syrup |          1 |          2 | 12 garrafas de 550 ml | 10.00 |
+-----------+---------------+------------+------------+-----------------------+-------+
1 row in set (0.00 sec)
```

Remova a tabela de exemplo quando terminar

```sql
DROP TABLE Products;
```

output

```bash
Query OK, 0 rows affected (0.90 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL LIKE Operator

O operador LIKE é usado em uma cláusula WHERE para procurar um padrão especificado em uma coluna.

Existem dois curingas frequentemente usados em conjunto com o operador LIKE:

O sinal de porcentagem% representa zero, um ou vários caracteres
O sinal de sublinhado _ representa um único caractere

```sql
CREATE TABLE Produtos (
    ProdutoID INT PRIMARY KEY,
    NomeProduto VARCHAR(100),
    Categoria VARCHAR(50),
    Preco DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.57 sec)
```

```sql
INSERT INTO Produtos VALUES
(1, 'Abacaxi', 'Frutas', 2.50),
(2, 'Banana', 'Frutas', 1.75),
(3, 'Maçã', 'Frutas', 3.00),
(4, 'Laranja', 'Frutas', 2.80),
(5, 'Leite', 'Laticínios', 3.50),
(6, 'Queijo', 'Laticínios', 5.75),
(7, 'Arroz', 'Grãos', 4.20),
(8, 'Feijão', 'Grãos', 3.80),
(9, 'Chocolate', 'Doces', 6.50),
(10, 'Bolacha', 'Doces', 2.25);
```

output

```bash
Query OK, 10 rows affected (0.16 sec)
Records: 10  Duplicates: 0  Warnings: 0
```

Produtos que começam com 'A':

```sql
SELECT * FROM Produtos
WHERE NomeProduto LIKE 'A%';
```

output

```bash
+-----------+-------------+-----------+-------+
| ProdutoID | NomeProduto | Categoria | Preco |
+-----------+-------------+-----------+-------+
|         1 | Abacaxi     | Frutas    |  2.50 |
|         7 | Arroz       | Gros      |  4.20 |
+-----------+-------------+-----------+-------+
2 rows in set (0.00 sec)
```

Produtos que terminam com 'o':

```sql
SELECT * FROM Produtos
WHERE NomeProduto LIKE '%o';
```

output

```bash
+-----------+-------------+-----------+-------+
| ProdutoID | NomeProduto | Categoria | Preco |
+-----------+-------------+-----------+-------+
|         6 | Queijo      | Laticnios |  5.75 |
|         8 | Feijo       | Gros      |  3.80 |
+-----------+-------------+-----------+-------+
2 rows in set (0.00 sec)
```

Produtos que contêm a letra 'e':

```sql
SELECT * FROM Produtos
WHERE NomeProduto LIKE '%e%';
```

output

```bash
+-----------+-------------+-----------+-------+
| ProdutoID | NomeProduto | Categoria | Preco |
+-----------+-------------+-----------+-------+
|         5 | Leite       | Laticnios |  3.50 |
|         6 | Queijo      | Laticnios |  5.75 |
|         8 | Feijo       | Gros      |  3.80 |
|         9 | Chocolate   | Doces     |  6.50 |
+-----------+-------------+-----------+-------+
4 rows in set (0.00 sec)
```

Produtos na categoria 'Doces':

```sql
SELECT * FROM Produtos
WHERE Categoria LIKE 'Doces';
```

output

```bash
+-----------+-------------+-----------+-------+
| ProdutoID | NomeProduto | Categoria | Preco |
+-----------+-------------+-----------+-------+
|         9 | Chocolate   | Doces     |  6.50 |
|        10 | Bolacha     | Doces     |  2.25 |
+-----------+-------------+-----------+-------+
2 rows in set (0.00 sec)
```

Produtos que começam com 'Fr' e têm pelo menos 4 caracteres:

```sql
SELECT * FROM Produtos
WHERE Categoria LIKE 'Fr%' AND LENGTH(NomeProduto) >= 4;
```

output

```bash
+-----------+-------------+-----------+-------+
| ProdutoID | NomeProduto | Categoria | Preco |
+-----------+-------------+-----------+-------+
|         1 | Abacaxi     | Frutas    |  2.50 |
|         2 | Banana      | Frutas    |  1.75 |
|         4 | Laranja     | Frutas    |  2.80 |
+-----------+-------------+-----------+-------+
3 rows in set (0.01 sec)
```

Produtos que têm 'a' como segunda letra no nome:

```sql
SELECT * FROM Produtos
WHERE NomeProduto LIKE '_a%';
```

output

```bash
+-----------+-------------+-----------+-------+
| ProdutoID | NomeProduto | Categoria | Preco |
+-----------+-------------+-----------+-------+
|         2 | Banana      | Frutas    |  1.75 |
|         3 | Ma          | Frutas    |  3.00 |
|         4 | Laranja     | Frutas    |  2.80 |
+-----------+-------------+-----------+-------+
3 rows in set (0.00 sec)
```

```sql
DROP TABLE Produtos;
```

output

```bash
Query OK, 0 rows affected (0.46 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL Wildcard Characters

Um caractere curinga é usado para substituir um ou mais caracteres em uma string.

Caracteres curinga são usados com o operador LIKE.
O operador LIKE é usado em uma cláusula WHERE para procurar um padrão especificado em uma coluna.

```sql
CREATE TABLE Produtos (
    ProdutoID INT PRIMARY KEY,
    NomeProduto VARCHAR(100),
    Categoria VARCHAR(50),
    Preco DECIMAL(10, 2)
);
```

output

```bash
Query OK, 0 rows affected (0.52 sec)
```

Inserindo dados na tabela Produtos

```sql
INSERT INTO Produtos VALUES
(1, 'Notebook', 'Eletrônicos', 1200.00),
(2, 'Fone de Ouvido', 'Acessórios', 50.00),
(3, 'Mesa de Jantar', 'Móveis', 300.00),
(4, 'Tênis Esportivo', 'Calçados', 80.00),
(5, 'Panela de Pressão', 'Utensílios de Cozinha', 40.00),
(6, 'Câmera Digital', 'Eletrônicos', 800.00),
(7, 'Cadeira de Escritório', 'Móveis', 150.00),
(8, 'Camiseta Casual', 'Vestuário', 25.00),
(9, 'Liquidificador', 'Utensílios de Cozinha', 60.00),
(10, 'Sapato Social', 'Calçados', 70.00);
```

output

```bash
Query OK, 10 rows affected (0.19 sec)
Records: 10  Duplicates: 0  Warnings: 0
```

Selecionando produtos cujo NomeProduto termina com 'o'

```sql
SELECT * FROM Produtos
WHERE NomeProduto LIKE '%o';
```

output

```bash
+-----------+----------------------+----------------------+--------+
| ProdutoID | NomeProduto          | Categoria            | Preco  |
+-----------+----------------------+----------------------+--------+
|         2 | Fone de Ouvido       | Acessrios            |  50.00 |
|         4 | Tnis Esportivo       | Calados              |  80.00 |
|         5 | Panela de Presso     | Utenslios de Cozinha |  40.00 |
|         7 | Cadeira de Escritrio | Mveis                | 150.00 |
+-----------+----------------------+----------------------+--------+
4 rows in set (0.00 sec)
```

Selecionando produtos cujo NomeProduto contém 'ca'

```sql
SELECT * FROM Produtos
WHERE NomeProduto LIKE '%ca%';
```

output

```bash
+-----------+----------------------+----------------------+--------+
| ProdutoID | NomeProduto          | Categoria            | Preco  |
+-----------+----------------------+----------------------+--------+
|         7 | Cadeira de Escritrio | Mveis                | 150.00 |
|         8 | Camiseta Casual      | Vesturio             |  25.00 |
|         9 | Liquidificador       | Utenslios de Cozinha |  60.00 |
+-----------+----------------------+----------------------+--------+
3 rows in set (0.00 sec)
```

Selecionando produtos cuja Categoria começa com 'E' e tem mais de 8 caracteres

```sql
SELECT * FROM Produtos
WHERE Categoria LIKE 'E%' AND LENGTH(NomeProduto) > 8;
```

output

```bash
+-----------+---------------+------------+--------+
| ProdutoID | NomeProduto   | Categoria  | Preco  |
+-----------+---------------+------------+--------+
|         6 | Cmera Digital | Eletrnicos | 800.00 |
+-----------+---------------+------------+--------+
1 row in set (0.00 sec)
```

Selecionando produtos cuja Categoria é 'Móveis' ou 'Vestuário'

```sql
SELECT * FROM Produtos
WHERE Categoria IN ('Móveis', 'Vestuário');
```

output

```bash
+-----------+----------------------+-----------+--------+
| ProdutoID | NomeProduto          | Categoria | Preco  |
+-----------+----------------------+-----------+--------+
|         3 | Mesa de Jantar       | Mveis     | 300.00 |
|         7 | Cadeira de Escritrio | Mveis     | 150.00 |
|         8 | Camiseta Casual      | Vesturio  |  25.00 |
+-----------+----------------------+-----------+--------+
3 rows in set (0.00 sec)
```

```sql
DROP TABLE Produtos;
```

output

```bash
Query OK, 0 rows affected (0.85 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL IN Operator

O operador IN permite especificar vários valores em uma cláusula WHERE.

```sql
CREATE TABLE Clientes (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(100),
    ContactName VARCHAR(50),
    Address VARCHAR(150),
    City VARCHAR(50),
    PostalCode VARCHAR(10),
    Country VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (0.57 sec)
```

```sql
CREATE TABLE Pedidos (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATE,
    TotalAmount DECIMAL(10, 2),
    FOREIGN KEY (CustomerID) REFERENCES Clientes(CustomerID)
);
```

output

```bash
Query OK, 0 rows affected (1.48 sec)
```

```sql
INSERT INTO Clientes VALUES
(1, 'Alfreds Futterkiste', 'Maria Anders', 'Obere Str. 57', 'Berlin', '12209', 'Germany'),
(2, 'Ana Trujillo Emparedados y helados', 'Ana Trujillo', 'Avda. de la Constitución 2222', 'México D.F.', '05021', 'Mexico'),
(3, 'Antonio Moreno Taquería', 'Antonio Moreno', 'Mataderos 2312', 'México D.F.', '05023', 'Mexico'),
(4, 'Around the Horn', 'Thomas Hardy', '120 Hanover Sq.', 'London', 'WA1 1DP', 'UK'),
(5, 'Berglunds snabbköp', 'Christina Berglund', 'Berguvsvägen 8', 'Luleå', 'S-958 22', 'Sweden');
```

output

```bash
Query OK, 5 rows affected (0.13 sec)
Records: 5  Duplicates: 0  Warnings: 0
```

```sql
INSERT INTO Pedidos VALUES
(1, 1, '2023-01-10', 150.00),
(2, 2, '2023-02-15', 200.50),
(3, 3, '2023-03-20', 75.80),
(4, 4, '2023-04-25', 300.25);
```

output

```bash
Query OK, 4 rows affected (0.10 sec)
Records: 4  Duplicates: 0  Warnings: 0
```

```sql
SELECT * FROM Clientes
WHERE Country IN ('Germany', 'France', 'UK');
```

output

```bash
+------------+---------------------+--------------+-----------------+--------+------------+---------+
| CustomerID | CustomerName        | ContactName  | Address         | City   | PostalCode | Country |
+------------+---------------------+--------------+-----------------+--------+------------+---------+
|          1 | Alfreds Futterkiste | Maria Anders | Obere Str. 57   | Berlin | 12209      | Germany |
|          4 | Around the Horn     | Thomas Hardy | 120 Hanover Sq. | London | WA1 1DP    | UK      |
+------------+---------------------+--------------+-----------------+--------+------------+---------+
2 rows in set (0.00 sec)
```

```sql
SELECT * FROM Clientes
WHERE Country NOT IN ('Germany', 'France', 'UK');
```

output

```bash
+------------+------------------------------------+--------------------+------------------------------+------------+------------+---------+
| CustomerID | CustomerName                       | ContactName        | Address                      | City       | PostalCode | Country |
+------------+------------------------------------+--------------------+------------------------------+------------+------------+---------+
|          2 | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitucin 2222 | Mxico D.F. | 05021      | Mexico  |
|          3 | Antonio Moreno Taquera             | Antonio Moreno     | Mataderos 2312               | Mxico D.F. | 05023      | Mexico  |
|          5 | Berglunds snabbkp                  | Christina Berglund | Berguvsvgen 8                | Lule       | S-958 22   | Sweden  |
+------------+------------------------------------+--------------------+------------------------------+------------+------------+---------+
3 rows in set (0.00 sec)
```

```sql
SELECT * FROM Clientes
WHERE CustomerID IN (SELECT CustomerID FROM Pedidos);
```

output

```bash
+------------+------------------------------------+----------------+------------------------------+------------+------------+---------+
| CustomerID | CustomerName                       | ContactName    | Address                      | City       | PostalCode | Country |
+------------+------------------------------------+----------------+------------------------------+------------+------------+---------+
|          1 | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                | Berlin     | 12209      | Germany |
|          2 | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitucin 2222 | Mxico D.F. | 05021      | Mexico  |
|          3 | Antonio Moreno Taquera             | Antonio Moreno | Mataderos 2312               | Mxico D.F. | 05023      | Mexico  |
|          4 | Around the Horn                    | Thomas Hardy   | 120 Hanover Sq.              | London     | WA1 1DP    | UK      |
+------------+------------------------------------+----------------+------------------------------+------------+------------+---------+
4 rows in set (0.01 sec)
```

```sql
SELECT * FROM Clientes
WHERE CustomerID NOT IN (SELECT CustomerID FROM Pedidos);
```

output

```bash
+------------+-------------------+--------------------+---------------+------+------------+---------+
| CustomerID | CustomerName      | ContactName        | Address       | City | PostalCode | Country |
+------------+-------------------+--------------------+---------------+------+------------+---------+
|          5 | Berglunds snabbkp | Christina Berglund | Berguvsvgen 8 | Lule | S-958 22   | Sweden  |
+------------+-------------------+--------------------+---------------+------+------------+---------+
1 row in set (0.00 sec)
```

```sql
DROP TABLE Pedidos;
DROP TABLE Clientes;
```

output

```bash
Query OK, 0 rows affected (0.49 sec)
```

**[:arrow_up: back to top](#índice)**

## Tabelas e Joins

**[:arrow_up: back to top](#índice)**

### SQL Aliases

**[:arrow_up: back to top](#índice)**

### SQL JOIN

**[:arrow_up: back to top](#índice)**

### INNER JOIN

**[:arrow_up: back to top](#índice)**

### SQL LEFT JOIN Keyword

**[:arrow_up: back to top](#índice)**

### SQL RIGHT JOIN Keyword

**[:arrow_up: back to top](#índice)**

### SQL Self Join

**[:arrow_up: back to top](#índice)**

### SQL FULL OUTER JOIN Keyword

**[:arrow_up: back to top](#índice)**

## Agrupamento e Funções Avançadas

**[:arrow_up: back to top](#índice)**

### SQL UNION Operator

**[:arrow_up: back to top](#índice)**

### SQL GROUP BY Statement

**[:arrow_up: back to top](#índice)**

### SQL HAVING Clause

**[:arrow_up: back to top](#índice)**

### SQL EXISTS Operator

**[:arrow_up: back to top](#índice)**

### SQL ANY Operator

**[:arrow_up: back to top](#índice)**

### SQL ANY and ALL Operators

**[:arrow_up: back to top](#índice)**

### SQL SELECT INTO Statement

**[:arrow_up: back to top](#índice)**

### SQL INSERT INTO SELECT Statement

**[:arrow_up: back to top](#índice)**

### SQL CASE Expression

**[:arrow_up: back to top](#índice)**

### SQL IFNULL(), ISNULL(), COALESCE(), and NVL() Functions

**[:arrow_up: back to top](#índice)**

## SQL Database

### SQL CREATE DB

A instrução CREATE DATABASE é usada para criar um novo banco de dados SQL.

```sql
CREATE DATABASE TUTORIAL;
```

output:

```BASH
Query OK, 1 row affected (0.10 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL SHOW DATABASES

Exibe os bancos de dados existentes no sistema.

```sql
SHOW DATABASES;
```

output:

```bash
+--------------------+
| Database           |
+--------------------+
| 'TUTORIAL'         |
| information_schema |
| mysql              |
| performance_schema |
| seu_banco_de_dados |
| sys                |
| testDB             |
+--------------------+
7 rows in set (0.00 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL DROP DB

A instrução DROP DATABASE é usada para eliminar um banco de dados SQL existente.

```sql
DROP DATABASE TUTORIAL;
```

output:

```bash
Query OK, 0 rows affected (0.24 sec)
```

```sql
SHOW DATABASES;
```

```bash
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| seu_banco_de_dados |
| sys                |
| testDB             |
+--------------------+
7 rows in set (0.00 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL USE

```sql
CREATE DATABASE TUTORIAL;
```

output:

```bash
Query OK, 1 rows affected (0.24 sec)
```

A instrução USE especifica o banco de dados que será usado para executar os comandos SQL.

```sql
USE TUTORIAL;
```

output:

```bash
Database changed
```

**[:arrow_up: back to top](#índice)**

### SQL CREATE TABLE

A instrução CREATE TABLE é usada para criar uma nova tabela em um banco de dados.

```sql
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);
```

output:

```bash
Query OK, 0 rows affected (0.55 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Persons;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| PersonID  | int          | YES  |     | NULL    |       |
| LastName  | varchar(255) | YES  |     | NULL    |       |
| FirstName | varchar(255) | YES  |     | NULL    |       |
| Address   | varchar(255) | YES  |     | NULL    |       |
| City      | varchar(255) | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Inserindo dados na tabela

```sql
INSERT INTO Persons (PersonID, LastName, FirstName, Address, City)
VALUES
    (1, 'Doe', 'John', '123 Main St', 'YourCity'),
    (2, 'Smith', 'Jane', '456 Oak St', 'AnotherCity'),
    (3, 'Johnson', 'Bob', '789 Pine St', 'YourCity');
```

output:

```bash
Query OK, 3 rows affected (0.11 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Consultando os dados na tabela

```sql
SELECT * FROM Persons;
```

output:

```bash
+----------+----------+-----------+-------------+-------------+
| PersonID | LastName | FirstName | Address     | City        |
+----------+----------+-----------+-------------+-------------+
|        1 | Doe      | John      | 123 Main St | YourCity    |
|        2 | Smith    | Jane      | 456 Oak St  | AnotherCity |
|        3 | Johnson  | Bob       | 789 Pine St | YourCity    |
+----------+----------+-----------+-------------+-------------+
3 rows in set (0.00 sec)
```

> Vamos criar uma nova tabela chamada Employees usando a estrutura da tabela existente Persons e selecionando apenas algumas colunas. Suponha que você queira criar uma tabela que contenha apenas as informações sobre funcionários, baseadas na tabela Persons. Aqui está como você pode fazer isso:

```sql
CREATE TABLE Employees AS
    SELECT PersonID, LastName, FirstName, City
    FROM Persons
    WHERE City = 'YourCity';
```

output:

```bash
Query OK, 2 rows affected (0.63 sec)
Records: 2  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Employees;
```

output:

```bash
mysql> DESCRIBE Employees;
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| PersonID  | int          | YES  |     | NULL    |       |
| LastName  | varchar(255) | YES  |     | NULL    |       |
| FirstName | varchar(255) | YES  |     | NULL    |       |
| City      | varchar(255) | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Consultando os dados na tabela

```sql
SELECT * FROM Employees;
```

output:

```bash
+----------+----------+-----------+----------+
| PersonID | LastName | FirstName | City     |
+----------+----------+-----------+----------+
|        1 | Doe      | John      | YourCity |
|        3 | Johnson  | Bob       | YourCity |
+----------+----------+-----------+----------+
2 rows in set (0.00 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL DROP TABLE

A instrução DROP TABLE é utilizada para excluir uma tabela existente em um banco de dados.

```sql
DROP TABLE Employees;
DROP TABLE Persons;
```

output

```bash
Query OK, 0 rows affected (0.88 sec)
```

**[:arrow_up: back to top](#índice)**

#### TRUNCATE

Criando a tabela de Produtos

```sql
CREATE TABLE Produtos (
    ID INT PRIMARY KEY,
    Nome VARCHAR(100),
    Categoria VARCHAR(50),
    Preco DECIMAL(10, 2)
);
```

```output
Query OK, 0 rows affected (0.69 sec)
```

Obtendo informações sobre a estrutura da tabela

```sql
DESCRIBE Produtos;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| ID        | int           | NO   | PRI | NULL    |       |
| Nome      | varchar(100)  | YES  |     | NULL    |       |
| Categoria | varchar(50)   | YES  |     | NULL    |       |
| Preco     | decimal(10,2) | YES  |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela de Produtos

```sql
INSERT INTO Produtos (ID, Nome, Categoria, Preco) VALUES
(101, 'Smartphone', 'Eletrônicos', 1200.00),
(102, 'Notebook', 'Eletrônicos', 2500.00),
(103, 'Camisa Polo', 'Roupas', 50.00),
(104, 'Tênis Esportivo', 'Calçados', 120.00);
```

output

```bash
Query OK, 4 rows affected (0.10 sec)
Records: 4  Duplicates: 0  Warnings: 0
```

Consultando os dados na tabela de Produtos

```sql
SELECT * FROM Produtos;
```

output:

```bash
+-----+----------------+------------+---------+
| ID  | Nome           | Categoria  | Preco   |
+-----+----------------+------------+---------+
| 101 | Smartphone     | Eletrnicos | 1200.00 |
| 102 | Notebook       | Eletrnicos | 2500.00 |
| 103 | Camisa Polo    | Roupas     |   50.00 |
| 104 | Tnis Esportivo | Calados    |  120.00 |
+-----+----------------+------------+---------+
4 rows in set (0.00 sec)
```

**Truncando** a tabela (exclui apenas os dados, não a estrutura da tabela)

```sql
TRUNCATE TABLE Produtos;
```

output:

```bash
Query OK, 0 rows affected (1.05 sec)
```

Após truncar a tabela: A consulta retornará uma tabela vazia, mas a estrutura da tabela ainda existe

```sql
SELECT * FROM Produtos; 
```

output:

```bash
Empty set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
```

output:

```bash
Query OK, 0 rows affected (0.40 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL ALTER TABLE

#### SQL ADD Column

Criar a tabela "Customers" com alguns dados iniciais

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    City VARCHAR(50)
);
```

output:

```bash
Query OK, 0 rows affected (0.71 sec)
```

Obtendo informações sobre a estrutura da tabela

```sql
DESCRIBE Customers;
```

output

```bash
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| CustomerID | int         | NO   | PRI | NULL    |       |
| FirstName  | varchar(50) | YES  |     | NULL    |       |
| LastName   | varchar(50) | YES  |     | NULL    |       |
| City       | varchar(50) | YES  |     | NULL    |       |
+------------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserir alguns dados na tabela

```sql
INSERT INTO Customers (CustomerID, FirstName, LastName, City)
VALUES
    (1, 'John', 'Doe', 'New York'),
    (2, 'Jane', 'Smith', 'Los Angeles'),
    (3, 'Bob', 'Johnson', 'Chicago');
```

output:

```bash
Query OK, 3 rows affected (0.16 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibir os dados da tabela antes da alteração

```sql
SELECT * FROM Customers;
```

output:

```bash
+------------+-----------+----------+-------------+
| CustomerID | FirstName | LastName | City        |
+------------+-----------+----------+-------------+
|          1 | John      | Doe      | New York    |
|          2 | Jane      | Smith    | Los Angeles |
|          3 | Bob       | Johnson  | Chicago     |
+------------+-----------+----------+-------------+
3 rows in set (0.00 sec)
```

Adicionar a coluna "Email" à tabela "Customers"

```sql
ALTER TABLE Customers
ADD Email VARCHAR(255);
```

output:

```bash
Query OK, 0 rows affected (0.55 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibir os dados da tabela depois da alteração

```sql
SELECT * FROM Customers;
```

output:

```bash
+------------+-----------+----------+-------------+---------+
| CustomerID | FirstName | LastName | City        | 'Email' |
+------------+-----------+----------+-------------+---------+
|          1 | John      | Doe      | New York    | 'NULL'  |
|          2 | Jane      | Smith    | Los Angeles | 'NULL'  |
|          3 | Bob       | Johnson  | Chicago     | 'NULL'  |
+------------+-----------+----------+-------------+---------+
3 rows in set (0.00 sec)
```

Atualizar alguns dados com informações de e-mail

```sql
UPDATE Customers
SET Email = 'john.doe@example.com'
WHERE CustomerID = 1;
```

```sql
UPDATE Customers
SET Email = 'jane.smith@example.com'
WHERE CustomerID = 2;
```

output:

```bash
Query OK, 1 row affected (0.09 sec)
Rows matched: 1  Changed: 1  Warnings: 0
```

Exibir os dados da tabela após a alteração

```sql
SELECT * FROM Customers;
```

```bash
+------------+-----------+----------+-------------+--------------------------+
| CustomerID | FirstName | LastName | City        | Email                    |
+------------+-----------+----------+-------------+--------------------------+
|          1 | John      | Doe      | New York    | 'john.doe@example.com'   |
|          2 | Jane      | Smith    | Los Angeles | 'jane.smith@example.com' |
|          3 | Bob       | Johnson  | Chicago     | NULL                     |
+------------+-----------+----------+-------------+--------------------------+
3 rows in set (0.00 sec)
```

apagar a tabela

```sql
DROP TABLE Customers;
```

output

```bash
Query OK, 0 rows affected (0.51 sec)
```

**[:arrow_up: back to top](#índice)**

#### SQL DROP Column

Criação inicial da tabela de Produtos

```sql
CREATE TABLE Produtos (
    ProdutoID INT PRIMARY KEY,
    NomeProduto VARCHAR(255),
    Preco DECIMAL(10, 2),
    QuantidadeDisponivel INT,
    Categoria VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (1.14 sec)
```

Exibindo a estrutura da tabela antes da remoção da coluna

```sql
DESCRIBE Produtos;
```

output

```bash
+------------------------+---------------+------+-----+---------+-------+
| Field                  | Type          | Null | Key | Default | Extra |
+------------------------+---------------+------+-----+---------+-------+
| ProdutoID              | int           | NO   | PRI | NULL    |       |
| NomeProduto            | varchar(255)  | YES  |     | NULL    |       |
| Preco                  | decimal(10,2) | YES  |     | NULL    |       |
| 'QuantidadeDisponivel' | int           | YES  |     | NULL    |       |
| Categoria              | varchar(50)   | YES  |     | NULL    |       |
+------------------------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Removendo a coluna "QuantidadeDisponivel" da tabela de Produtos

```sql
ALTER TABLE Produtos
DROP COLUMN QuantidadeDisponivel;
```

output

```bash
Query OK, 0 rows affected (0.49 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após a remoção da coluna

```sql
DESCRIBE Produtos;
```

output

```bash
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| ProdutoID   | int           | NO   | PRI | NULL    |       |
| NomeProduto | varchar(255)  | YES  |     | NULL    |       |
| Preco       | decimal(10,2) | YES  |     | NULL    |       |
| Categoria   | varchar(50)   | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Apagar a tabela

```sql
DROP TABLE Produtos;
```

output

```bash
Query OK, 0 rows affected (0.83 sec)
```

**[:arrow_up: back to top](#índice)**

#### SQL RENAME Column

Criação inicial da tabela de Funcionarios

```sql
CREATE TABLE Funcionarios (
    FuncionarioID INT PRIMARY KEY,
    NomeCompleto VARCHAR(255),
    Cargo VARCHAR(100),
    Salario DECIMAL(10, 2),
    Departamento VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (0.50 sec)
```

Exibindo a estrutura da tabela antes da renomeação da coluna

```sql
DESCRIBE Funcionarios;
```

output

```bash
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
| FuncionarioID | int           | NO   | PRI | NULL    |       |
| NomeCompleto  | varchar(255)  | YES  |     | NULL    |       |
| Cargo         | varchar(100)  | YES  |     | NULL    |       |
| Salario       | decimal(10,2) | YES  |     | NULL    |       |
| Departamento  | varchar(50)   | YES  |     | NULL    |       |
+---------------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Renomeando a coluna "NomeCompleto" para "Nome" na tabela de Funcionarios

```sql
ALTER TABLE Funcionarios
RENAME COLUMN NomeCompleto TO Nome;
```

output

```bash
Query OK, 0 rows affected (0.40 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após a renomeação da coluna

```sql
DESCRIBE Funcionarios;
```

output

```bash
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
| FuncionarioID | int           | NO   | PRI | NULL    |       |
| Nome          | varchar(255)  | YES  |     | NULL    |       |
| Cargo         | varchar(100)  | YES  |     | NULL    |       |
| Salario       | decimal(10,2) | YES  |     | NULL    |       |
| Departamento  | varchar(50)   | YES  |     | NULL    |       |
+---------------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Apagar a tabela

```sql
DROP TABLE Funcionarios;
```

output

```bash
Query OK, 0 rows affected (0.40 sec)
```

**[:arrow_up: back to top](#índice)**

#### SQL ALTER DATATYPE

Criação inicial da tabela de Pedidos

```sql
CREATE TABLE Pedidos (
    PedidoID INT PRIMARY KEY,
    ClienteID INT,
    ValorTotal DECIMAL(10, 2),
    DataPedido DATE,
    Status VARCHAR(50)
);
```

output

```bash
Query OK, 0 rows affected (1.11 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Pedidos;
```

output

```bash
+------------+---------------+------+-----+---------+-------+
| Field      | Type          | Null | Key | Default | Extra |
+------------+---------------+------+-----+---------+-------+
| PedidoID   | int           | NO   | PRI | NULL    |       |
| ClienteID  | int           | YES  |     | NULL    |       |
| ValorTotal | decimal(10,2) | YES  |     | NULL    |       |
| DataPedido | date          | YES  |     | NULL    |       |
| Status     | varchar(50)   | YES  |     | NULL    |       |
+------------+---------------+------+-----+---------+-------+
5 rows in set (0.01 sec)
```

Alterando o tipo de dados da coluna "DataPedido" para TIMESTAMP na tabela de Pedidos (exemplo para MySQL)

```sql
ALTER TABLE Pedidos
MODIFY COLUMN DataPedido TIMESTAMP;
```

output

```bash
Query OK, 0 rows affected (1.65 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura

```sql
DESCRIBE Pedidos;
```

output

```bash
+------------+---------------+------+-----+---------+-------+
| Field      | Type          | Null | Key | Default | Extra |
+------------+---------------+------+-----+---------+-------+
| PedidoID   | int           | NO   | PRI | NULL    |       |
| ClienteID  | int           | YES  |     | NULL    |       |
| ValorTotal | decimal(10,2) | YES  |     | NULL    |       |
| DataPedido | 'timestamp'   | YES  |     | NULL    |       |
| Status     | varchar(50)   | YES  |     | NULL    |       |
+------------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Apagar a tabela

```sql
DROP TABLE Pedidos;
```

output

```bash
Query OK, 0 rows affected (0.34 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL Create Constraints

#### NOT NULL Constraint

A restrição NOT NULL impõe uma coluna para NÃO aceitar valores NULL.

Criando a tabela "Employees" com a restrição NOT NULL

```sql
CREATE TABLE Employees (
    EmployeeID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Department varchar(100),
    PRIMARY KEY (EmployeeID)
);
```

output

```bash
Query OK, 0 rows affected (1.25 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Employees;
```

output

```bash
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| EmployeeID | int          | NO   | PRI | NULL    |       |
| LastName   | varchar(255) | NO   |     | NULL    |       |
| FirstName  | varchar(255) | NO   |     | NULL    |       |
| Department | varchar(100) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela com valores não nulos

```sql
INSERT INTO Employees (EmployeeID, LastName, FirstName, Department)
VALUES (1, 'Silva', 'Ana', 'HR'),
       (2, 'Santos', 'Carlos', 'IT'),
       (3, 'Oliveira', 'Mariana', 'Finance');
```

output

```bash
Query OK, 3 rows affected (0.11 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

```sql
SELECT * FROM Employees;
```

output

```bash
+------------+----------+-----------+------------+
| EmployeeID | LastName | FirstName | Department |
+------------+----------+-----------+------------+
|          1 | Silva    | Ana       | HR         |
|          2 | Santos   | Carlos    | IT         |
|          3 | Oliveira | Mariana   | Finance    |
+------------+----------+-----------+------------+
3 rows in set (0.00 sec)
```

A seguinte instrução gerará um erro porque a coluna "FirstName" não aceita valores nulos

```sql
INSERT INTO Employees (EmployeeID, LastName, FirstName, Department)
 VALUES (4, 'Pereira', NULL, 'Marketing');
```

output

```bash
ERROR 1048 (23000): Column 'FirstName' cannot be null
```

Excluindo a tabela

```sql
DROP TABLE Employees;
```

output

```bash
Query OK, 0 rows affected (0.38 sec)
```

##### SQL NOT NULL on ALTER TABLE

Criando a tabela "Students" sem a restrição NOT NULL inicialmente

```sql
CREATE TABLE Students (
    StudentID int PRIMARY KEY,
    FirstName varchar(255) NOT NULL,
    LastName varchar(255) NOT NULL,
    Grade int
);
```

output:

```bash
Query OK, 0 rows affected (0.60 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Students;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| StudentID | int          | NO   | PRI | NULL    |       |
| FirstName | varchar(255) | NO   |     | NULL    |       |
| LastName  | varchar(255) | NO   |     | NULL    |       |
| Grade     | int          | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela

```sql
INSERT INTO Students (StudentID, FirstName, LastName, Grade)
VALUES (1, 'João', 'Silva', 90),
       (2, 'Ana', 'Santos', 85),
       (3, 'Carlos', 'Oliveira', 20);
```

output:

```bash
Query OK, 3 rows affected (0.09 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados antes de aplicar a restrição NOT NULL

```sql
SELECT * FROM Students;
```

output:

```bash
+-----------+-----------+----------+-------+
| StudentID | FirstName | LastName | Grade |
+-----------+-----------+----------+-------+
|         1 | Joo       | Silva    |    90 |
|         2 | Ana       | Santos   |    85 |
|         3 | Carlos    | Oliveira |    20 |
+-----------+-----------+----------+-------+
3 rows in set (0.00 sec)
```

Adicionando a restrição NOT NULL à coluna "Grade" usando ALTER TABLE

```sql
ALTER TABLE Students
MODIFY Grade INT NOT NULL;
```

output:

```bash
Query OK, 0 rows affected (1.74 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Students;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| StudentID | int          | NO   | PRI | NULL    |       |
| FirstName | varchar(255) | NO   |     | NULL    |       |
| LastName  | varchar(255) | NO   |     | NULL    |       |
| Grade     | int          | NO   |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Students;
```

output:

```bash
Query OK, 0 rows affected (0.41 sec)
```

**[:arrow_up: back to top](#índice)**

#### UNIQUE Constraint

A restrição UNIQUE garante que todos os valores em uma coluna sejam diferentes.

Ambas as restrições UNIQUE e PRIMARY KEY fornecem uma garantia de exclusividade para uma coluna ou conjunto de colunas.

Uma restrição PRIMARY KEY possui automaticamente uma restrição UNIQUE.

Criando a tabela "Employees" com uma restrição UNIQUE na coluna "EmployeeID"

```sql
CREATE TABLE Employees (
    EmployeeID int NOT NULL UNIQUE,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```

output:

```bash
Query OK, 0 rows affected (1.04 sec)
```

Criando a tabela "Employees" com uma restrição UNIQUE composta nas colunas "EmployeeID" e "LastName"

```sql
CREATE TABLE EmployeesWithCompositeUnique (
    EmployeeID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT UC_Employees UNIQUE (EmployeeID, LastName)
);
```

output:

```bash
Query OK, 0 rows affected (1.61 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Employees;
DESCRIBE EmployeesWithCompositeUnique;
```

output:

```bash
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| EmployeeID | int          | NO   | PRI | NULL    |       |
| LastName   | varchar(255) | NO   |     | NULL    |       |
| FirstName  | varchar(255) | YES  |     | NULL    |       |
| Age        | int          | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

output:

```bash
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| EmployeeID | int          | NO   | PRI | NULL    |       |
| LastName   | varchar(255) | NO   | PRI | NULL    |       |
| FirstName  | varchar(255) | YES  |     | NULL    |       |
| Age        | int          | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela

```sql
INSERT INTO Employees (EmployeeID, LastName, FirstName, Age)
VALUES (1, 'Silva', 'Ana', 30),
       (2, 'Santos', 'Carlos', 25),
       (3, 'Oliveira', 'Mariana', 28);
```

output:

```bash
Query OK, 3 rows affected (0.13 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

```sql
INSERT INTO EmployeesWithCompositeUnique (EmployeeID, LastName, FirstName, Age)
VALUES (1, 'Silva', 'Ana', 30),
       (2, 'Santos', 'Carlos', 25),
       (3, 'Oliveira', 'Mariana', 28);
```

output:

```bash
Query OK, 3 rows affected (0.22 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados antes

```sql
SELECT * FROM Employees;
SELECT * FROM EmployeesWithCompositeUnique;
```

output:

```bash
+------------+----------+-----------+------+
| EmployeeID | LastName | FirstName | Age  |
+------------+----------+-----------+------+
|          1 | Silva    | Ana       |   30 |
|          2 | Santos   | Carlos    |   25 |
|          3 | Oliveira | Mariana   |   28 |
+------------+----------+-----------+------+
3 rows in set (0.00 sec)
```

output:

```bash
+------------+----------+-----------+------+
| EmployeeID | LastName | FirstName | Age  |
+------------+----------+-----------+------+
|          1 | Silva    | Ana       |   30 |
|          2 | Santos   | Carlos    |   25 |
|          3 | Oliveira | Mariana   |   28 |
+------------+----------+-----------+------+
3 rows in set (0.00 sec)
```

Tentativa de inserir um registro com o mesmo valor na coluna "EmployeeID", resultará em erro

```sql
INSERT INTO Employees (EmployeeID, LastName, FirstName, Age)
VALUES (1, 'Pereira', 'João', 22);
```

output:

```bash
ERROR 1062 (23000): Duplicate entry '1' for key 'Employees.EmployeeID'
```

Tentativa de inserir um registro com a mesma combinação de "EmployeeID" e "LastName", resultará em erro

```sql
INSERT INTO EmployeesWithCompositeUnique (EmployeeID, LastName, FirstName, Age)
VALUES (1, 'Silva', 'João', 22);
```

output:

```bash
ERROR 1062 (23000): Duplicate entry '1-Silva' for key 'EmployeesWithCompositeUnique.UC_Employees'
```

Excluindo a tabela

```sql
DROP TABLE Employees;
DROP TABLE EmployeesWithCompositeUnique;
```

output:

```bash
Query OK, 0 rows affected (0.37 sec)
```

**[:arrow_up: back to top](#índice)**

##### SQL UNIQUE Constraint on ALTER TABLE

```sql
CREATE TABLE Customers (
    CustomerID int NOT NULL,
    FirstName varchar(255) NOT NULL,
    LastName varchar(255) NOT NULL,
    Email varchar(255) UNIQUE,
    Age int
);
```

output:

```bash
Query OK, 0 rows affected (0.62 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Customers;
```

output:

```bash
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| CustomerID | int          | NO   |     | NULL    |       |
| FirstName  | varchar(255) | NO   |     | NULL    |       |
| LastName   | varchar(255) | NO   |     | NULL    |       |
| Email      | varchar(255) | YES  | UNI | NULL    |       |
| Age        | int          | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Inserindo dados na tabela

```sql
INSERT INTO Customers (CustomerID, FirstName, LastName, Email, Age)
VALUES (1, 'João', 'Silva', 'joao@example.com', 30),
       (2, 'Ana', 'Santos', 'ana@example.com', 25),
       (3, 'Carlos', 'Oliveira', 'carlos@example.com', 28);
```

output:

```bash
Query OK, 3 rows affected (0.17 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo dados antes de adicionar a restrição UNIQUE

```sql
SELECT * FROM Customers;
```

output:

```bash
+------------+-----------+----------+--------------------+------+
| CustomerID | FirstName | LastName | Email              | Age  |
+------------+-----------+----------+--------------------+------+
|          1 | Joo       | Silva    | joao@example.com   |   30 |
|          2 | Ana       | Santos   | ana@example.com    |   25 |
|          3 | Carlos    | Oliveira | carlos@example.com |   28 |
+------------+-----------+----------+--------------------+------+
3 rows in set (0.00 sec)
```

Adicionando a restrição UNIQUE à coluna "CustomerID"

```sql
ALTER TABLE Customers
ADD UNIQUE (CustomerID);
```

output:

```bash
Query OK, 0 rows affected (2.03 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Tentativa de adicionar um novo registro com o mesmo valor em "CustomerID", resultará em erro

```sql
INSERT INTO Customers (CustomerID, FirstName, LastName, Email, Age)
VALUES (1, 'Pereira', 'Mariana', 'mariana@example.com', 22);
```

output:

```bash
ERROR 1062 (23000): Duplicate entry '1' for key 'Customers.CustomerID'
```

Adicionando a restrição UNIQUE composta nas colunas "CustomerID" e "Email"

```sql
ALTER TABLE Customers
ADD CONSTRAINT UC_Customers UNIQUE (CustomerID, Email);
```

output:

```bash
Query OK, 0 rows affected (0.50 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Customers;
```

output:

```bash
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| CustomerID | int          | NO   | PRI | NULL    |       |
| FirstName  | varchar(255) | NO   |     | NULL    |       |
| LastName   | varchar(255) | NO   |     | NULL    |       |
| Email      | varchar(255) | YES  | UNI | NULL    |       |
| Age        | int          | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Tentativa de adicionar um novo registro com o mesmo valor em "CustomerID" ou "Email", resultará em erro

```sql
INSERT INTO Customers (CustomerID, FirstName, LastName, Email, Age)
VALUES (4, 'Fernando', 'Pereira', 'joao@example.com', 35);
```

output:

```bash
ERROR 1062 (23000): Duplicate entry 'joao@example.com' for key 'Customers.Email'
```

Exibindo dados após adicionar as restrições UNIQUE

```sql
SELECT * FROM Customers;
```

output:

```bash
+------------+-----------+----------+--------------------+------+
| CustomerID | FirstName | LastName | Email              | Age  |
+------------+-----------+----------+--------------------+------+
|          1 | Joo       | Silva    | joao@example.com   |   30 |
|          2 | Ana       | Santos   | ana@example.com    |   25 |
|          3 | Carlos    | Oliveira | carlos@example.com |   28 |
+------------+-----------+----------+--------------------+------+
3 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Customers;
```

output:

```bash
Query OK, 0 rows affected (0.43 sec)
```

##### DROP a UNIQUE Constraint

-- Criando a tabela "Students" com uma restrição UNIQUE

```sql
CREATE TABLE Students (
    StudentID int NOT NULL UNIQUE,
    FirstName varchar(255) NOT NULL,
    LastName varchar(255) NOT NULL,
    Age int
);
```

output:

```bash
Query OK, 0 rows affected (0.49 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Students;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| StudentID | int          | NO   | PRI | NULL    |       |
| FirstName | varchar(255) | NO   |     | NULL    |       |
| LastName  | varchar(255) | NO   |     | NULL    |       |
| Age       | int          | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela

```sql
INSERT INTO Students (StudentID, FirstName, LastName, Age)
VALUES (1, 'João', 'Silva', 20),
       (2, 'Ana', 'Santos', 22),
       (3, 'Carlos', 'Oliveira', 25);
```

output:

```bash
Query OK, 3 rows affected (0.14 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo dados antes de remover a restrição UNIQUE

```sql
SELECT * FROM Students;
```

output:

```bash
+-----------+-----------+----------+------+
| StudentID | FirstName | LastName | Age  |
+-----------+-----------+----------+------+
|         1 | Joo       | Silva    |   20 |
|         2 | Ana       | Santos   |   22 |
|         3 | Carlos    | Oliveira |   25 |
+-----------+-----------+----------+------+
3 rows in set (0.00 sec)
```

Removendo a restrição UNIQUE da coluna "StudentID"
No MySQL, a restrição UNIQUE é implementada como um índice, portanto, usamos DROP INDEX

```sql
ALTER TABLE Students
DROP INDEX StudentID;
```

output:

```bash
Query OK, 3 rows affected (1.78 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Students;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| StudentID | int          | NO   |     | NULL    |       |
| FirstName | varchar(255) | NO   |     | NULL    |       |
| LastName  | varchar(255) | NO   |     | NULL    |       |
| Age       | int          | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Tentativa de adicionar um novo registro com o mesmo valor em "StudentID", não resultará em erro

```sql
INSERT INTO Students (StudentID, FirstName, LastName, Age)
VALUES (1, 'Sabrina', 'Silva', 20);
```

output:

```bash
Query OK, 1 row affected (0.11 sec)
```

Exibindo dados após remover a restrição UNIQUE

```sql
SELECT * FROM Students;
```

output:

```bash
+-----------+-----------+----------+------+
| StudentID | FirstName | LastName | Age  |
+-----------+-----------+----------+------+
|         1 | Joo       | Silva    |   20 |
|         2 | Ana       | Santos   |   22 |
|         3 | Carlos    | Oliveira |   25 |
|         1 | Sabrina   | Silva    |   20 |
+-----------+-----------+----------+------+
4 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Students;
```

output:

```bash
DROP TABLE Students;
```

**[:arrow_up: back to top](#índice)**

#### PRIMARY KEY Constraint

A restrição PRIMARY KEY identifica exclusivamente cada registro em uma tabela.

As chaves primárias devem conter valores UNIQUE e não podem conter valores NULL.

Criar a tabela "Clientes"

```sql
CREATE TABLE Clientes (
    ClienteID INTEGER NOT NULL,
    Nome VARCHAR(255) NOT NULL,
    Email VARCHAR(255) UNIQUE, -- O e-mail deve ser único
    Telefone VARCHAR(20),
    PRIMARY KEY (ClienteID)
);
```

output:

```bash
Query OK, 0 rows affected (1.16 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| ClienteID | int          | NO   | PRI | NULL    |       |
| Nome      | varchar(255) | NO   |     | NULL    |       |
| Email     | varchar(255) | YES  | UNI | NULL    |       |
| Telefone  | varchar(20)  | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.01 sec)
```

Inserir dados na tabela "Clientes"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Telefone)
VALUES
    (1, 'João Silva', 'joao@email.com', '123-456-7890'),
    (2, 'Maria Oliveira', 'maria@email.com', '987-654-3210'),
    (3, 'Carlos Souza', 'carlos@email.com', '555-123-4567');
```

output:

```bash
Query OK, 3 rows affected (0.12 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo dados

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+----------------+------------------+--------------+
| ClienteID | Nome           | Email            | Telefone     |
+-----------+----------------+------------------+--------------+
|         1 | Joo Silva      | joao@email.com   | 123-456-7890 |
|         2 | Maria Oliveira | maria@email.com  | 987-654-3210 |
|         3 | Carlos Souza   | carlos@email.com | 555-123-4567 |
+-----------+----------------+------------------+--------------+
3 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Clientes;
```

output:

```bash
Query OK, 0 rows affected (0.42 sec)
```

**[:arrow_up: back to top](#índice)**

##### PRIMARY KEY on ALTER TABLE

Para criar uma restrição PRIMARY KEY na coluna "ID" quando a tabela já estiver criada, use o seguinte SQL:

Criar a tabela "Produtos" sem chave primária

```sql
CREATE TABLE Produtos (
    ProdutoID INT,
    Nome VARCHAR(255) NOT NULL,
    Categoria VARCHAR(50),
    Preco DECIMAL(10, 2) NOT NULL
);
```

output:

```bash
Query OK, 0 rows affected (1.05 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Produtos;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| ProdutoID | int           | YES  |     | NULL    |       |
| Nome      | varchar(255)  | NO   |     | NULL    |       |
| Categoria | varchar(50)   | YES  |     | NULL    |       |
| Preco     | decimal(10,2) | NO   |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
4 rows in set (0.01 sec)
```

Inserir alguns dados na tabela "Produtos"

```sql
INSERT INTO Produtos (ProdutoID, Nome, Categoria, Preco)
VALUES
    (1, 'Camiseta', 'Roupas', 19.99),
    (2, 'Notebook', 'Eletrônicos', 899.99),
    (3, 'Livro', 'Literatura', 12.50);
```

output:

```bash
Query OK, 3 rows affected (0.10 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo dados

```sql
SELECT * FROM Produtos;
```

output:

```bash
+-----------+----------+------------+--------+
| ProdutoID | Nome     | Categoria  | Preco  |
+-----------+----------+------------+--------+
|         1 | Camiseta | Roupas     |  19.99 |
|         2 | Notebook | Eletrnicos | 899.99 |
|         3 | Livro    | Literatura |  12.50 |
+-----------+----------+------------+--------+
3 rows in set (0.00 sec)
```

Agora, adicionar uma PRIMARY KEY à coluna "ProdutoID" usando ALTER TABLE

```sql
ALTER TABLE Produtos
ADD PRIMARY KEY (ProdutoID);
```

output:

```bash
Query OK, 0 rows affected (1.89 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Produtos;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| ProdutoID | int           | NO   | PRI | NULL    |       |
| Nome      | varchar(255)  | NO   |     | NULL    |       |
| Categoria | varchar(50)   | YES  |     | NULL    |       |
| Preco     | decimal(10,2) | NO   |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
```

output:

```bash
Query OK, 0 rows affected (0.50 sec)
```

**[:arrow_up: back to top](#índice)**

##### DROP a PRIMARY KEY Constraint

Criar a tabela "Funcionarios" com uma chave primária

```sql
CREATE TABLE Funcionarios (
    FuncionarioID INT PRIMARY KEY,
    Nome VARCHAR(255) NOT NULL,
    Cargo VARCHAR(50),
    Salario DECIMAL(10, 2) NOT NULL
);
```

output:

```bash
Query OK, 0 rows affected (0.66 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Funcionarios;
```

output:

```bash
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
| FuncionarioID | int           | NO   | PRI | NULL    |       |
| Nome          | varchar(255)  | NO   |     | NULL    |       |
| Cargo         | varchar(50)   | YES  |     | NULL    |       |
| Salario       | decimal(10,2) | NO   |     | NULL    |       |
+---------------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

```sql
INSERT INTO Funcionarios (FuncionarioID, Nome, Cargo, Salario)
VALUES
    (1, 'Ana Silva', 'Analista de Marketing', 5000.00),
    (2, 'Pedro Oliveira', 'Desenvolvedor Web', 7000.00),
    (3, 'Mariana Santos', 'Gerente de Projetos', 9000.00);
```

output:

```bash
Query OK, 3 rows affected (0.12 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo dados

```sql
SELECT * FROM Funcionarios;
```

output:

```bash
+---------------+----------------+-----------------------+---------+
| FuncionarioID | Nome           | Cargo                 | Salario |
+---------------+----------------+-----------------------+---------+
|             1 | Ana Silva      | Analista de Marketing | 5000.00 |
|             2 | Pedro Oliveira | Desenvolvedor Web     | 7000.00 |
|             3 | Mariana Santos | Gerente de Projetos   | 9000.00 |
+---------------+----------------+-----------------------+---------+
3 rows in set (0.00 sec)
```

Agora, remover a PRIMARY KEY da coluna "FuncionarioID" usando ALTER TABLE

```sql
ALTER TABLE Funcionarios
DROP PRIMARY KEY; 
```

output:

```bash
Query OK, 3 rows affected (1.65 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após remover a PRIMARY KEY

```sql
DESCRIBE Funcionarios;
```

output:

```bash
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
| FuncionarioID | int           | NO   |     | NULL    |       |
| Nome          | varchar(255)  | NO   |     | NULL    |       |
| Cargo         | varchar(50)   | YES  |     | NULL    |       |
| Salario       | decimal(10,2) | NO   |     | NULL    |       |
+---------------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Funcionarios;
```

output:

```bash
Query OK, 0 rows affected (0.76 sec)
```

**[:arrow_up: back to top](#índice)**

#### FOREIGN KEY Constraint

Uma CHAVE ESTRANGEIRA é um campo (ou coleção de campos) em uma tabela, que se refere à CHAVE PRIMÁRIA em outra tabela.

Criar a tabela "Clientes" com chave primária

```sql
CREATE TABLE Clientes (
    PersonID INT PRIMARY KEY,
    LastName VARCHAR(255) NOT NULL,
    FirstName VARCHAR(255) NOT NULL,
    Age INT
);
```

output:

```bash
Query OK, 0 rows affected (0.59 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| PersonID  | int          | NO   | PRI | NULL    |       |
| LastName  | varchar(255) | NO   |     | NULL    |       |
| FirstName | varchar(255) | NO   |     | NULL    |       |
| Age       | int          | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserir alguns dados na tabela "Clientes"

```sql
INSERT INTO Clientes (PersonID, LastName, FirstName, Age)
VALUES
    (1, 'Hansen', 'Ola', 30),
    (2, 'Svendson', 'Tove', 23),
    (3, 'Pettersen', 'Kari', 20);
```

output:

```bash
Query OK, 3 rows affected (0.09 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibir dados na tabela "Clientes"

```sql
SELECT * FROM Clientes;
```

output:

```bash
+----------+-----------+-----------+------+
| PersonID | LastName  | FirstName | Age  |
+----------+-----------+-----------+------+
|        1 | Hansen    | Ola       |   30 |
|        2 | Svendson  | Tove      |   23 |
|        3 | Pettersen | Kari      |   20 |
+----------+-----------+-----------+------+
3 rows in set (0.00 sec)
```

Criar a tabela "Pedidos" com uma chave estrangeira referenciando "Clientes"

```sql
CREATE TABLE Pedidos (
    OrderID INT PRIMARY KEY,
    OrderNumber INT,
    PersonID INT,
    FOREIGN KEY (PersonID) REFERENCES Clientes(PersonID)
);
```

output:

```bash
Query OK, 0 rows affected (1.10 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Pedidos;
```

output:

```bash
+-------------+------+------+-----+---------+-------+
| Field       | Type | Null | Key | Default | Extra |
+-------------+------+------+-----+---------+-------+
| OrderID     | int  | NO   | PRI | NULL    |       |
| OrderNumber | int  | YES  |     | NULL    |       |
| PersonID    | int  | YES  | MUL | NULL    |       |
+-------------+------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserir alguns dados na tabela "Pedidos"

```sql
INSERT INTO Pedidos (OrderID, OrderNumber, PersonID)
VALUES
    (1, 77895, 3), -- Kari Pettersen fez um pedido
    (2, 44678, 3), -- Kari fez outro pedido
    (3, 22456, 2), -- Tove Svendson fez um pedido
    (4, 24562, 1); -- Ola Hansen fez um pedido
```

output:

```bash
Query OK, 4 rows affected (0.09 sec)
Records: 4  Duplicates: 0  Warnings: 0
```

Exibir dados na tabela "Pedidos"

```sql
SELECT * FROM Pedidos;
```

output:

```bash
+---------+-------------+----------+
| OrderID | OrderNumber | PersonID |
+---------+-------------+----------+
|       1 |       77895 |        3 |
|       2 |       44678 |        3 |
|       3 |       22456 |        2 |
|       4 |       24562 |        1 |
+---------+-------------+----------+
4 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Pedidos;
DROP TABLE Clientes;
```

output:

```bash
Query OK, 0 rows affected (0.92 sec)
```

**[:arrow_up: back to top](#índice)**

##### FOREIGN KEY on ALTER TABLE

Criar a tabela "Clientes" com chave primária

```sql
CREATE TABLE Clientes (
    ClienteID INT PRIMARY KEY,
    Nome VARCHAR(255) NOT NULL,
    Email VARCHAR(255) UNIQUE,
    Telefone VARCHAR(20)
);
```

output:

```bash
Query OK, 0 rows affected (1.54 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| ClienteID | int          | NO   | PRI | NULL    |       |
| Nome      | varchar(255) | NO   |     | NULL    |       |
| Email     | varchar(255) | YES  | UNI | NULL    |       |
| Telefone  | varchar(20)  | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserir alguns dados na tabela "Clientes"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Telefone)
VALUES
    (1, 'João Silva', 'joao@email.com', '123-456-7890'),
    (2, 'Maria Oliveira', 'maria@email.com', '987-654-3210'),
    (3, 'Carlos Souza', 'carlos@email.com', '555-123-4567');
```

output:

```bash
Query OK, 3 rows affected (0.09 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Criar a tabela "Vendas" sem chave estrangeira

```sql
CREATE TABLE Vendas (
    VendaID INT PRIMARY KEY,
    Valor DECIMAL(10, 2) NOT NULL,
    ClienteID INT
);
```

output:

```bash
Query OK, 0 rows affected (0.58 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Vendas;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| VendaID   | int           | NO   | PRI | NULL    |       |
| Valor     | decimal(10,2) | NO   |     | NULL    |       |
| ClienteID | int           | YES  |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserir alguns dados na tabela "Vendas"

```sql
INSERT INTO Vendas (VendaID, Valor, ClienteID)
VALUES
    (1, 100.00, 1), -- Venda de João Silva
    (2, 150.50, 2), -- Venda de Maria Oliveira
    (3, 75.25, 3);  -- Venda de Carlos Souza
```

output:

```bash
Query OK, 3 rows affected (0.10 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibir dados na tabela "Vendas" antes de adicionar a FOREIGN KEY

```sql
SELECT * FROM Vendas;
```

output:

```bash
+---------+--------+-----------+
| VendaID | Valor  | ClienteID |
+---------+--------+-----------+
|       1 | 100.00 |         1 |
|       2 | 150.50 |         2 |
|       3 |  75.25 |         3 |
+---------+--------+-----------+
3 rows in set (0.00 sec)
```

Agora, adicionar uma FOREIGN KEY à coluna "ClienteID" usando ALTER TABLE

```sql
ALTER TABLE Vendas
ADD FOREIGN KEY (ClienteID) REFERENCES Clientes(ClienteID);
```

output:

```bash
Query OK, 3 rows affected (2.03 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Vendas;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| VendaID   | int           | NO   | PRI | NULL    |       |
| Valor     | decimal(10,2) | NO   |     | NULL    |       |
| ClienteID | int           | YES  | MUL | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Vendas;
DROP TABLE Clientes;
```

output:

```bash
Query OK, 0 rows affected (0.49 sec)
```

**[:arrow_up: back to top](#índice)**

##### DROP a FOREIGN KEY Constraint

Criar a tabela "Produtos" com chave primária

```sql
CREATE TABLE Produtos (
    ProdutoID INT PRIMARY KEY,
    Nome VARCHAR(255) NOT NULL,
    Preco DECIMAL(10, 2) NOT NULL
);
```

output:

```bash
Query OK, 0 rows affected (0.88 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Produtos;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| ProdutoID | int           | NO   | PRI | NULL    |       |
| Nome      | varchar(255)  | NO   |     | NULL    |       |
| Preco     | decimal(10,2) | NO   |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserir alguns dados na tabela "Produtos"

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES
    (1, 'Camiseta', 19.99),
    (2, 'Notebook', 899.99),
    (3, 'Livro', 12.50);
```

output:

```bash
Query OK, 3 rows affected (0.12 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Criar a tabela "ItensVenda" com chave estrangeira referenciando "Produtos"

```sql
CREATE TABLE ItensVenda (
    ItemID INT PRIMARY KEY,
    Quantidade INT NOT NULL,
    ProdutoID INT,
    FOREIGN KEY (ProdutoID) REFERENCES Produtos(ProdutoID)
);
```

output:

```bash
Query OK, 0 rows affected (0.62 sec)
```

Exibir a definição da tabela "ItensVenda" para encontrar o nome da chave estrangeira

```sql
SHOW CREATE TABLE ItensVenda;
```

output:

```bash
+------------+--------------------------------------------------------------------------------+
| Table      | Create 
+------------+--------------------------------------------------------------------------------+
| ItensVenda | CREATE TABLE `ItensVenda` (
  `ItemID` int NOT NULL,
  `Quantidade` int NOT NULL,
  `ProdutoID` int DEFAULT NULL,
  PRIMARY KEY (`ItemID`),
  KEY `ProdutoID` (`ProdutoID`),
  CONSTRAINT `ItensVenda_ibfk_1` FOREIGN KEY (`ProdutoID`) REFERENCES `Produtos` (`ProdutoID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+------------+---------------------------------------------------------------------------------+
```

Inserir alguns dados na tabela "ItensVenda"

```sql
INSERT INTO ItensVenda (ItemID, Quantidade, ProdutoID)
VALUES
    (1, 3, 1), -- 3 Camisetas vendidas
    (2, 1, 2), -- 1 Notebook vendido
    (3, 5, 3); -- 5 Livros vendidos
```

output:

```bash
Query OK, 3 rows affected (0.12 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibir dados na tabela "ItensVenda" antes de remover a FOREIGN KEY

```sql
SELECT * FROM ItensVenda;
```

output:

```bash
+--------+------------+-----------+
| ItemID | Quantidade | ProdutoID |
+--------+------------+-----------+
|      1 |          3 |         1 |
|      2 |          1 |         2 |
|      3 |          5 |         3 |
+--------+------------+-----------+
3 rows in set (0.00 sec)
```

Agora, remover a FOREIGN KEY usando ALTER TABLE

```sql
ALTER TABLE ItensVenda
DROP FOREIGN KEY ItensVenda_ibfk_1;
```

output:

```bash
Query OK, 0 rows affected (0.21 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela

```sql
SHOW CREATE TABLE ItensVenda;
```

output:

```bash
+------------+--------------------------------------------------------+
| Table      | Create  |
+------------+--------------------------------------------------------+
| ItensVenda | CREATE TABLE `ItensVenda` (
  `ItemID` int NOT NULL,
  `Quantidade` int NOT NULL,
  `ProdutoID` int DEFAULT NULL,
  PRIMARY KEY (`ItemID`),
  KEY `ProdutoID` (`ProdutoID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+------------+---------------------------------------------------------+
1 row in set (0.00 sec)

```

Exibir dados na tabela "ItensVenda" após remover a FOREIGN KEY

```sql
SELECT * FROM ItensVenda;
```

output:

```bash
mysql> SELECT * FROM ItensVenda;
+--------+------------+-----------+
| ItemID | Quantidade | ProdutoID |
+--------+------------+-----------+
|      1 |          3 |         1 |
|      2 |          1 |         2 |
|      3 |          5 |         3 |
+--------+------------+-----------+
3 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
DROP TABLE ItensVenda;
```

output:

```bash
Query OK, 0 rows affected (0.38 sec)
Query OK, 0 rows affected (0.44 sec)
```

**[:arrow_up: back to top](#índice)**

#### CHECK Constraint

A restrição CHECK é usada para limitar o intervalo de valores que pode ser colocado em uma coluna.

Criando a tabela "Produtos" com a restrição CHECK

```sql
CREATE TABLE Produtos (
    ProdutoID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Preco decimal(10, 2) CHECK (Preco > 0)
);
```

output:

```bash
Query OK, 0 rows affected (0.61 sec)
```

Exibindo a estrutura da tabela

```sql
SHOW CREATE TABLE Produtos;
```

output:

```bash
+----------+-------------------------------------------------------+
| Table    | Create  |
+----------+-------------------------------------------------------+
| Produtos | CREATE TABLE `Produtos` (
  `ProdutoID` int NOT NULL,
  `Nome` varchar(255) NOT NULL,
  `Preco` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`ProdutoID`),
  CONSTRAINT `Produtos_chk_1` CHECK ((`Preco` > 0))
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+----------+-------------------------------------------------------+
1 row in set (0.00 sec)
```

Inserindo dados na tabela com valores que atendem à restrição CHECK

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES (1, 'Notebook', 2500.00),
       (2, 'Smartphone', 1200.50),
       (3, 'Fones de Ouvido', 80.99);
```

output:

```bash
Query OK, 3 rows affected (0.14 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados da tabela

```sql
SELECT * FROM Produtos;
```

output:

```bash
+-----------+-----------------+---------+
| ProdutoID | Nome            | Preco   |
+-----------+-----------------+---------+
|         1 | Notebook        | 2500.00 |
|         2 | Smartphone      | 1200.50 |
|         3 | Fones de Ouvido |   80.99 |
+-----------+-----------------+---------+
3 rows in set (0.00 sec)
```

A seguinte instrução gerará um erro porque o valor do "Preco" não é maior que zero

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES (4, 'Mouse', 0.00);
```

output:

```bash
ERROR 3819 (HY000): Check constraint 'Produtos_chk_1' is violated.
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
```

output:

```bash
Query OK, 0 rows affected (0.38 sec)
```

**[:arrow_up: back to top](#índice)**

##### CHECK on ALTER TABLE

Para criar uma restrição CHECK na coluna "Idade" quando a tabela já estiver criada, utilize o seguinte SQL:

Criando a tabela "Jogadores" sem a restrição CHECK inicialmente

```sql
CREATE TABLE Jogadores (
    JogadorID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Pontuacao int
);
```

output:

```bash
Query OK, 0 rows affected (0.61 sec)
```

Exibindo a estrutura da tabela antes da restrição CHECK

```sql
DESCRIBE Jogadores;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| JogadorID | int          | NO   | PRI | NULL    |       |
| Nome      | varchar(255) | NO   |     | NULL    |       |
| Pontuacao | int          | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

Inserindo dados na tabela

```sql
INSERT INTO Jogadores (JogadorID, Nome, Pontuacao)
VALUES (1, 'Ronaldo', 25),
       (2, 'Messi', 30),
       (3, 'Neymar', 15);
```

output:

```bash
Query OK, 3 rows affected (0.10 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados antes de aplicar a restrição CHECK

```sql
SELECT * FROM Jogadores;
```

output:

```bash
+-----------+---------+-----------+
| JogadorID | Nome    | Pontuacao |
+-----------+---------+-----------+
|         1 | Ronaldo |        25 |
|         2 | Messi   |        30 |
|         3 | Neymar  |        15 |
+-----------+---------+-----------+
3 rows in set (0.00 sec)
```

Adicionando a restrição CHECK à coluna "Pontuacao" usando ALTER TABLE

```sql
ALTER TABLE Jogadores
ADD CHECK (Pontuacao >= 0);
```

output:

```bash
Query OK, 3 rows affected (1.66 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após a adição da restrição CHECK

```sql
SHOW CREATE TABLE Jogadores;
```

output:

```bash
+-----------+---------------------------------------------------------+
| Table     | Create 
+-----------+---------------------------------------------------------+
| Jogadores | CREATE TABLE `Jogadores` (
  `JogadorID` int NOT NULL,
  `Nome` varchar(255) NOT NULL,
  `Pontuacao` int DEFAULT NULL,
  PRIMARY KEY (`JogadorID`),
  CONSTRAINT `Jogadores_chk_1` CHECK ((`Pontuacao` >= 0))
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+-----------+--------------------------------------------------------+
1 row in set (0.00 sec)

```

A seguinte instrução gerará um erro porque a restrição CHECK não é atendida

```sql
INSERT INTO Jogadores (JogadorID, Nome, Pontuacao)
VALUES (4, 'Mbappe', -5);
```

output:

```bash
ERROR 3819 (HY000): Check constraint 'Jogadores_chk_1' is violated.
```

Exibindo os dados após a adição da restrição CHECK

```sql
SELECT * FROM Jogadores;
```

output:

```bash
+-----------+---------+-----------+
| JogadorID | Nome    | Pontuacao |
+-----------+---------+-----------+
|         1 | Ronaldo |        25 |
|         2 | Messi   |        30 |
|         3 | Neymar  |        15 |
+-----------+---------+-----------+
3 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Jogadores;
```

output:

```bash
Query OK, 0 rows affected (0.50 sec)
```

**[:arrow_up: back to top](#índice)**

##### DROP a CHECK Constraint

Criando a tabela "ContasBancarias" com uma restrição CHECK

```sql
CREATE TABLE ContasBancarias (
    ContaID int PRIMARY KEY,
    Titular varchar(255) NOT NULL,
    Saldo decimal(10, 2) CHECK (Saldo >= 0)
);
```

output:

```bash
Query OK, 0 rows affected (0.51 sec)
```

Exibindo a estrutura da tabela antes de remover a restrição CHECK

```sql
SHOW CREATE TABLE ContasBancarias;
```

output:

```bash
+-----------------+--------------------------------------------------+
| Table           | Create 
+-----------------+--------------------------------------------------+
| ContasBancarias | CREATE TABLE `ContasBancarias` (
  `ContaID` int NOT NULL,
  `Titular` varchar(255) NOT NULL,
  `Saldo` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`ContaID`),
  CONSTRAINT `ContasBancarias_chk_1` CHECK ((`Saldo` >= 0))
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+-----------------+-------------------------------------------------+
1 row in set (0.00 sec)
```

Inserindo dados na tabela

```sql
INSERT INTO ContasBancarias (ContaID, Titular, Saldo)
VALUES (1, 'João Silva', 5000.00),
       (2, 'Maria Santos', 10000.50),
       (3, 'Carlos Oliveira', 1500.75);
```

output:

```bash
Query OK, 3 rows affected (0.09 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados antes de remover a restrição CHECK

```sql
SELECT * FROM ContasBancarias;
```

output:

```bash
+---------+-----------------+----------+
| ContaID | Titular         | Saldo    |
+---------+-----------------+----------+
|       1 | Joo Silva       |  5000.00 |
|       2 | Maria Santos    | 10000.50 |
|       3 | Carlos Oliveira |  1500.75 |
+---------+-----------------+----------+
3 rows in set (0.00 sec)
```

Removendo a restrição CHECK à coluna "Saldo" usando ALTER TABLE

```sql
ALTER TABLE ContasBancarias
DROP CHECK ContasBancarias_chk_1;
```

output:

```bash
Query OK, 0 rows affected (0.18 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após remover a restrição CHECK

```sql
SHOW CREATE TABLE ContasBancarias;
```

output:

```bash
mysql> SHOW CREATE TABLE ContasBancarias;
+-----------------+-------------------------------------------------+
| Table           | Create  |
+-----------------+--------------------------------------------------+
| ContasBancarias | CREATE TABLE `ContasBancarias` (
  `ContaID` int NOT NULL,
  `Titular` varchar(255) NOT NULL,
  `Saldo` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`ContaID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+-----------------+-------------------------------------------------+
1 row in set (0.00 sec)

```

Excluindo a tabela

```sql
DROP TABLE ContasBancarias;
```

output:

```bash
Query OK, 0 rows affected (0.40 sec)
```

**[:arrow_up: back to top](#índice)**

#### DEFAULT Constraint

A restrição DEFAULT é usada para definir um valor padrão para uma coluna.
O valor padrão será adicionado a todos os novos registros, se nenhum outro valor for especificado.

Criando a tabela "Clientes" com um valor padrão para a coluna "Cidade"

```sql
CREATE TABLE Clientes (
    ClienteID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Email varchar(255) NOT NULL,
    Cidade varchar(255) DEFAULT 'Rio de Janeiro'
);
```

output:

```bash
Query OK, 0 rows affected (0.61 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

output:

```bash
+-----------+--------------+------+-----+----------------+-------+
| Field     | Type         | Null | Key | Default        | Extra |
+-----------+--------------+------+-----+----------------+-------+
| ClienteID | int          | NO   | PRI | NULL           |       |
| Nome      | varchar(255) | NO   |     | NULL           |       |
| Email     | varchar(255) | NO   |     | NULL           |       |
| Cidade    | varchar(255) | YES  |     | Rio de Janeiro |       |
+-----------+--------------+------+-----+----------------+-------+
4 rows in set (0.01 sec)
```

Inserindo dados na tabela sem fornecer um valor para a coluna "Cidade"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email)
VALUES (1, 'Ana Silva', 'ana@email.com'),
       (2, 'Carlos Oliveira', 'carlos@email.com'),
       (3, 'Mariana Santos', 'mariana@email.com');
```

output:

```bash
Query OK, 3 rows affected (0.10 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados da tabela

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-----------------+-------------------+----------------+
| ClienteID | Nome            | Email             | Cidade         |
+-----------+-----------------+-------------------+----------------+
|         1 | Ana Silva       | ana@email.com     | Rio de Janeiro |
|         2 | Carlos Oliveira | carlos@email.com  | Rio de Janeiro |
|         3 | Mariana Santos  | mariana@email.com | Rio de Janeiro |
+-----------+-----------------+-------------------+----------------+
3 rows in set (0.00 sec)
```

Inserindo dados na tabela fornecendo um valor específico para a coluna "Cidade"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Cidade)
VALUES (4, 'Pedro Pereira', 'pedro@email.com', 'São Paulo');
```

output:

```bash
Query OK, 1 row affected (0.10 sec)
```

Exibindo os dados da tabela após a inserção com valor específico para a coluna "Cidade"

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-----------------+-------------------+----------------+
| ClienteID | Nome            | Email             | Cidade         |
+-----------+-----------------+-------------------+----------------+
|         1 | Ana Silva       | ana@email.com     | Rio de Janeiro |
|         2 | Carlos Oliveira | carlos@email.com  | Rio de Janeiro |
|         3 | Mariana Santos  | mariana@email.com | Rio de Janeiro |
|         4 | Pedro Pereira   | pedro@email.com   | So Paulo       |
+-----------+-----------------+-------------------+----------------+
4 rows in set (0.01 sec)
```

Excluindo a tabela

```sql
DROP TABLE Clientes;
```

output:

```bash
Query OK, 0 rows affected (0.84 sec)
```

**[:arrow_up: back to top](#índice)**

#### DEFAULT on ALTER TABLE

Criando a tabela "Clientes" sem a restrição DEFAULT inicialmente

```sql
CREATE TABLE Clientes (
    ClienteID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Email varchar(255) NOT NULL,
    Estado varchar(255)
);
```

output:

```bash
Query OK, 0 rows affected (0.49 sec)
```

Exibindo a estrutura da tabela antes da restrição DEFAULT

```sql
DESCRIBE Clientes;
```

output:

```bash
 DESCRIBE Clientes;
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| ClienteID | int          | NO   | PRI | NULL    |       |
| Nome      | varchar(255) | NO   |     | NULL    |       |
| Email     | varchar(255) | NO   |     | NULL    |       |
| Estado    | varchar(255) | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela

```sql
INSERT INTO Clientes (ClienteID, Nome, Email)
VALUES (1, 'Ana Silva', 'ana@email.com'),
       (2, 'Carlos Oliveira', 'carlos@email.com'),
       (3, 'Mariana Santos', 'mariana@email.com');
```

output:

```bash
Query OK, 3 rows affected (0.42 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados antes de aplicar a restrição DEFAULT

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-----------------+-------------------+--------+
| ClienteID | Nome            | Email             | Estado |
+-----------+-----------------+-------------------+--------+
|         1 | Ana Silva       | ana@email.com     | NULL   |
|         2 | Carlos Oliveira | carlos@email.com  | NULL   |
|         3 | Mariana Santos  | mariana@email.com | NULL   |
+-----------+-----------------+-------------------+--------+
3 rows in set (0.00 sec)
```

Adicionando a restrição DEFAULT à coluna "Estado" usando ALTER TABLE

```sql
ALTER TABLE Clientes
ALTER Estado SET DEFAULT 'Rio de Janeiro';
```

output:

```bash
Query OK, 0 rows affected (0.21 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após adicionar a restrição DEFAULT

```sql
DESCRIBE Clientes;
```

output:

```bash
+-----------+--------------+------+-----+----------------+-------+
| Field     | Type         | Null | Key | Default        | Extra |
+-----------+--------------+------+-----+----------------+-------+
| ClienteID | int          | NO   | PRI | NULL           |       |
| Nome      | varchar(255) | NO   |     | NULL           |       |
| Email     | varchar(255) | NO   |     | NULL           |       |
| Estado    | varchar(255) | YES  |     | Rio de Janeiro |       |
+-----------+--------------+------+-----+----------------+-------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela sem fornecer um valor para a coluna "Estado"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email)
VALUES (4, 'Pedro Pereira', 'pedro@email.com');
```

output:

```bash
Query OK, 1 row affected (0.13 sec)
```

Exibindo os dados após a inserção sem fornecer um valor para a coluna "Estado"

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-----------------+-------------------+----------------+
| ClienteID | Nome            | Email             | Estado         |
+-----------+-----------------+-------------------+----------------+
|         1 | Ana Silva       | ana@email.com     | NULL           |
|         2 | Carlos Oliveira | carlos@email.com  | NULL           |
|         3 | Mariana Santos  | mariana@email.com | NULL           |
|         4 | Pedro Pereira   | pedro@email.com   | Rio de Janeiro |
+-----------+-----------------+-------------------+----------------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela fornecendo um valor específico para a coluna "Estado"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Estado)
VALUES (5, 'Maria Oliveira', 'maria@email.com', 'São Paulo');
```

output:

```bash
Query OK, 1 row affected (0.10 sec)
```

Exibindo os dados após a inserção com valor específico para a coluna "Estado"

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-----------------+-------------------+----------------+
| ClienteID | Nome            | Email             | Estado         |
+-----------+-----------------+-------------------+----------------+
|         1 | Ana Silva       | ana@email.com     | NULL           |
|         2 | Carlos Oliveira | carlos@email.com  | NULL           |
|         3 | Mariana Santos  | mariana@email.com | NULL           |
|         4 | Pedro Pereira   | pedro@email.com   | Rio de Janeiro |
|         5 | Maria Oliveira  | maria@email.com   | So Paulo       |
+-----------+-----------------+-------------------+----------------+
5 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Clientes;
```

output:

```bash
Query OK, 0 rows affected (0.44 sec)
```

**[:arrow_up: back to top](#índice)**

##### DROP a DEFAULT Constraint

Criando a tabela "Produtos" com uma restrição DEFAULT

```sql
CREATE TABLE Produtos (
    ProdutoID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Preco decimal(10, 2) DEFAULT 0.00,
    Tipo varchar(255) DEFAULT 'Geral'
);
```

output:

```bash
Query OK, 0 rows affected (0.48 sec)
```

Exibindo a estrutura da tabela antes de remover a restrição DEFAULT

```sql
DESCRIBE Produtos;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| ProdutoID | int           | NO   | PRI | NULL    |       |
| Nome      | varchar(255)  | NO   |     | NULL    |       |
| Preco     | decimal(10,2) | YES  |     | 0.00    |       |
| Tipo      | varchar(255)  | YES  |     | Geral   |       |
+-----------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela sem fornecer um valor para a coluna "Tipo"

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES (1, 'Notebook', 2500.00),
       (2, 'Smartphone', 1200.50),
       (3, 'Fones de Ouvido', 80.99);
```

output:

```bash
Query OK, 3 rows affected (0.08 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados da tabela antes de remover a restrição DEFAULT

```sql
SELECT * FROM Produtos;
```

output:

```bash
+-----------+-----------------+---------+-------+
| ProdutoID | Nome            | Preco   | Tipo  |
+-----------+-----------------+---------+-------+
|         1 | Notebook        | 2500.00 | Geral |
|         2 | Smartphone      | 1200.50 | Geral |
|         3 | Fones de Ouvido |   80.99 | Geral |
+-----------+-----------------+---------+-------+
3 rows in set (0.00 sec)
```

Removendo a restrição DEFAULT à coluna "Tipo" usando ALTER TABLE

```sql
ALTER TABLE Produtos
ALTER Tipo DROP DEFAULT;
```

output:

```bash
Query OK, 0 rows affected (0.49 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após remover a restrição DEFAULT

```sql
DESCRIBE Produtos;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| ProdutoID | int           | NO   | PRI | NULL    |       |
| Nome      | varchar(255)  | NO   |     | NULL    |       |
| Preco     | decimal(10,2) | YES  |     | 0.00    |       |
| Tipo      | varchar(255)  | YES  |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo dados na tabela sem fornecer um valor para a coluna "Tipo" após a remoção

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES (4, 'Mouse', 25.00),
       (5, 'Teclado', 50.00);
```

output:

```bash
ERROR 1364 (HY000): Field 'Tipo' doesn't have a default value
```

Exibindo os dados da tabela após a inserção sem fornecer um valor para a coluna "Tipo"

```sql
SELECT * FROM Produtos;
```

output:

```bash
+-----------+-----------------+---------+-------+
| ProdutoID | Nome            | Preco   | Tipo  |
+-----------+-----------------+---------+-------+
|         1 | Notebook        | 2500.00 | Geral |
|         2 | Smartphone      | 1200.50 | Geral |
|         3 | Fones de Ouvido |   80.99 | Geral |
+-----------+-----------------+---------+-------+
3 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
```

output:

```bash
Query OK, 0 rows affected (0.57 sec)
```

**[:arrow_up: back to top](#índice)**

### SQL CREATE INDEX Statement

Os índices são usados para recuperar dados do banco de dados mais rapidamente do que de outra forma. Os usuários não podem ver os índices, eles apenas servem para agilizar pesquisas/consultas.

Criando a tabela "Produtos"

```sql
CREATE TABLE Produtos (
    ProdutoID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Preco decimal(10, 2),
    Categoria varchar(100)
);
```

output:

```bash
Query OK, 0 rows affected (1.10 sec)
```

Exibindo a estrutura da tabela antes da criação do índice

```sql
DESCRIBE Produtos;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| ProdutoID | int           | NO   | PRI | NULL    |       |
| Nome      | varchar(255)  | NO   |     | NULL    |       |
| Preco     | decimal(10,2) | YES  |     | NULL    |       |
| Categoria | varchar(100)  | YES  |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco, Categoria)
VALUES (1, 'Notebook', 2500.00, 'Eletrônicos'),
       (2, 'Smartphone', 1200.50, 'Eletrônicos'),
       (3, 'Fones de Ouvido', 80.99, 'Acessórios');
```

output:

```bash
Query OK, 3 rows affected (0.11 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados da tabela antes da criação do índice

```sql
SELECT * FROM Produtos;
```

output:

```bash
+-----------+-----------------+---------+------------+
| ProdutoID | Nome            | Preco   | Categoria  |
+-----------+-----------------+---------+------------+
|         1 | Notebook        | 2500.00 | Eletrnicos |
|         2 | Smartphone      | 1200.50 | Eletrnicos |
|         3 | Fones de Ouvido |   80.99 | Acessrios  |
+-----------+-----------------+---------+------------+
3 rows in set (0.00 sec)
```

Criando um índice na coluna "Nome" da tabela "Produtos"

```sql
CREATE INDEX idx_Nome ON Produtos (Nome);
```

output:

```bash
Query OK, 0 rows affected (0.69 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após a criação do índice

```sql
SHOW CREATE TABLE Produtos;
```

output:

```bash
+----------+----------------------------------------------------------+
| Table    | Create 
+----------+----------------------------------------------------------+
| Produtos | CREATE TABLE `Produtos` (
  `ProdutoID` int NOT NULL,
  `Nome` varchar(255) NOT NULL,
  `Preco` decimal(10,2) DEFAULT NULL,
  `Categoria` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`ProdutoID`),
  KEY `idx_Nome` (`Nome`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+----------+---------------------------------------------------------+
1 row in set (0.00 sec)
```

Agora, vamos criar uma tabela "Clientes" com um índice único na coluna "Cpf"

```sql
CREATE TABLE Clientes (
    ClienteID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Email varchar(255) NOT NULL,
    Cpf varchar(11) UNIQUE
);
```

output:

```bash
Query OK, 0 rows affected (0.70 sec)
```

Exibindo a estrutura da tabela "Clientes" antes da criação do índice único

```sql
DESCRIBE Clientes;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| ClienteID | int          | NO   | PRI | NULL    |       |
| Nome      | varchar(255) | NO   |     | NULL    |       |
| Email     | varchar(255) | NO   |     | NULL    |       |
| Cpf       | varchar(11)  | YES  | UNI | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

Inserindo alguns dados na tabela "Clientes"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Cpf)
VALUES (1, 'Ana Silva', 'ana@email.com', '12345678901'),
       (2, 'Carlos Oliveira', 'carlos@email.com', '98765432109'),
       (3, 'Mariana Santos', 'mariana@email.com', '12398745603');
```

output:

```bash
Query OK, 3 rows affected (0.11 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados da tabela "Clientes" antes da criação do índice único

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-----------------+-------------------+-------------+
| ClienteID | Nome            | Email             | Cpf         |
+-----------+-----------------+-------------------+-------------+
|         1 | Ana Silva       | ana@email.com     | 12345678901 |
|         2 | Carlos Oliveira | carlos@email.com  | 98765432109 |
|         3 | Mariana Santos  | mariana@email.com | 12398745603 |
+-----------+-----------------+-------------------+-------------+
3 rows in set (0.00 sec)
```

Criando um índice único na coluna "Cpf" da tabela "Clientes"

```sql
CREATE UNIQUE INDEX idx_Cpf ON Clientes (Cpf);
```

output:

```bash
Query OK, 0 rows affected, 1 warning (0.44 sec)
Records: 0  Duplicates: 0  Warnings: 1
```

Exibindo a estrutura da tabela "Clientes" após a criação do índice único

```sql
SHOW CREATE TABLE Clientes;
```

output:

```bash
+----------+-------------------------------------------------------+
| Table    | Create 
+----------+-------------------------------------------------------+
| Clientes | CREATE TABLE `Clientes` (
  `ClienteID` int NOT NULL,
  `Nome` varchar(255) NOT NULL,
  `Email` varchar(255) NOT NULL,
  `Cpf` varchar(11) DEFAULT NULL,
  PRIMARY KEY (`ClienteID`),
  UNIQUE KEY `Cpf` (`Cpf`),
  UNIQUE KEY `idx_Cpf` (`Cpf`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+----------+-------------------------------------------------------+
1 row in set (0.00 sec)
```

Tente inserir um registro com um Cpf duplicado para ver o efeito do índice único
A seguinte instrução gerará um erro

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Cpf) VALUES (4, 'Pedro Pereira', 'pedro@email.com', '12345678901');
```

output:

```bash
ERROR 1062 (23000): Duplicate entry '12345678901' for key 'Clientes.Cpf'
```

Excluindo as tabelas

```sql
DROP TABLE Produtos;
DROP TABLE Clientes;
```

output:

```bash
Query OK, 0 rows affected (0.59 sec)
```

**[:arrow_up: back to top](#índice)**

##### DROP INDEX Statement

Criando a tabela "Produtos" com um índice na coluna "Nome"

```sql
CREATE TABLE Produtos (
    ProdutoID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Preco decimal(10, 2),
    Categoria varchar(100)
);
```

output:

```bash
Query OK, 0 rows affected (1.29 sec)
```

Exibindo a estrutura da tabela antes da criação do índice

```sql
DESCRIBE Produtos;
```

output:

```bash
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| ProdutoID | int           | NO   | PRI | NULL    |       |
| Nome      | varchar(255)  | NO   |     | NULL    |       |
| Preco     | decimal(10,2) | YES  |     | NULL    |       |
| Categoria | varchar(100)  | YES  |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
4 rows in set (0.01 sec)
```

Inserindo alguns dados na tabela

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco, Categoria)
VALUES (1, 'Notebook', 2500.00, 'Eletrônicos'),
       (2, 'Smartphone', 1200.50, 'Eletrônicos'),
       (3, 'Fones de Ouvido', 80.99, 'Acessórios');
```

output:

```bash
Query OK, 3 rows affected (0.08 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados da tabela antes da criação do índice

```sql
SELECT * FROM Produtos;
```

output:

```bash
+-----------+-----------------+---------+------------+
| ProdutoID | Nome            | Preco   | Categoria  |
+-----------+-----------------+---------+------------+
|         1 | Notebook        | 2500.00 | Eletrnicos |
|         2 | Smartphone      | 1200.50 | Eletrnicos |
|         3 | Fones de Ouvido |   80.99 | Acessrios  |
+-----------+-----------------+---------+------------+
3 rows in set (0.00 sec)
```

Criando um índice na coluna "Nome" da tabela "Produtos"

```sql
CREATE INDEX idx_Nome ON Produtos (Nome);
```

output:

```bash
Query OK, 0 rows affected (0.78 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após a criação do índice

```sql
SHOW CREATE TABLE Produtos;
```

output:

```bash
+----------+------------------------------------------------------+
| Table    | Create 
+----------+------------------------------------------------------+
| Produtos | CREATE TABLE `Produtos` (
  `ProdutoID` int NOT NULL,
  `Nome` varchar(255) NOT NULL,
  `Preco` decimal(10,2) DEFAULT NULL,
  `Categoria` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`ProdutoID`),
  KEY `idx_Nome` (`Nome`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+----------+-------------------------------------------------------+
1 row in set (0.00 sec)
```

Removendo o índice "idx_Nome" da tabela "Produtos"

```sql
ALTER TABLE Produtos
DROP INDEX idx_Nome;
```

output:

```bash
Query OK, 0 rows affected (0.26 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Exibindo a estrutura da tabela após a remoção do índice

```sql
SHOW CREATE TABLE Produtos;
```

output:

```bash
+----------+--------------------------------------------------------+
| Table    | Create 
+----------+--------------------------------------------------------+
| Produtos | CREATE TABLE `Produtos` (
  `ProdutoID` int NOT NULL,
  `Nome` varchar(255) NOT NULL,
  `Preco` decimal(10,2) DEFAULT NULL,
  `Categoria` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`ProdutoID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+----------+-------------------------------------------------------+
1 row in set (0.01 sec)
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
```

output:

```bash
Query OK, 0 rows affected (0.83 sec)
```

**[:arrow_up: back to top](#índice)**

#### SQL AUTO INCREMENT Field

O incremento automático permite que um número exclusivo seja gerado automaticamente quando um novo registro é inserido em uma tabela.

Criando a tabela "Clientes" com uma chave primária de incremento automático

```sql
CREATE TABLE Clientes (
    ClienteID int NOT NULL AUTO_INCREMENT,
    Nome varchar(255) NOT NULL,
    Email varchar(255) NOT NULL,
    PRIMARY KEY (ClienteID)
);
```

output:

```bash
Query OK, 0 rows affected (0.61 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

output:

```bash
 DESCRIBE Clientes;
+-----------+--------------+------+-----+---------+----------------+
| Field     | Type         | Null | Key | Default | Extra          |
+-----------+--------------+------+-----+---------+----------------+
| ClienteID | int          | NO   | PRI | NULL    | auto_increment |
| Nome      | varchar(255) | NO   |     | NULL    |                |
| Email     | varchar(255) | NO   |     | NULL    |                |
+-----------+--------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)
```

Alterando o valor inicial para a sequência de incremento automático

```sql
ALTER TABLE Clientes AUTO_INCREMENT=100;
```

output:

```bash
Query OK, 0 rows affected (0.17 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

Inserindo novos registros na tabela "Clientes" sem especificar um valor para "ClienteID"

```sql
INSERT INTO Clientes (Nome, Email)
VALUES ('Lars Monsen', 'lars@email.com'),
       ('Eva Hansen', 'eva@email.com'),
       ('Sven Olsen', 'sven@email.com');
```

output:

```bash
Query OK, 3 rows affected (0.11 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados da tabela após a inserção

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-------------+----------------+
| ClienteID | Nome        | Email          |
+-----------+-------------+----------------+
|       100 | Lars Monsen | lars@email.com |
|       101 | Eva Hansen  | eva@email.com  |
|       102 | Sven Olsen  | sven@email.com |
+-----------+-------------+----------------+
3 rows in set (0.00 sec)
```

Inserindo mais um registro sem especificar um valor para "ClienteID"

```sql
INSERT INTO Clientes (Nome, Email)
VALUES ('Karen Johansen', 'karen@email.com');
```

output:

```bash
Query OK, 1 row affected (0.08 sec)
```

Exibindo os dados após a inserção do novo registro

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+----------------+-----------------+
| ClienteID | Nome           | Email           |
+-----------+----------------+-----------------+
|       100 | Lars Monsen    | lars@email.com  |
|       101 | Eva Hansen     | eva@email.com   |
|       102 | Sven Olsen     | sven@email.com  |
|       103 | Karen Johansen | karen@email.com |
+-----------+----------------+-----------------+
4 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Clientes;
```

output:

```bash
Query OK, 0 rows affected (0.44 sec)
```

**[:arrow_up: back to top](#índice)**

#### SQL Date Data Types

O MySQL vem com os seguintes tipos de dados para armazenar uma data ou um valor de data/hora no banco de dados:

- DATE  - formato AAAA-MM-DD
- DATETIME - formato: AAAA-MM-DD HH:MI:SS
- TIMESTAMP - formato: AAAA-MM-DD HH:MI:SS
- YEAR - formato AAAA ou AA

Criando a tabela "Eventos" com diferentes tipos de dados para datas e horas

```sql
CREATE TABLE Eventos (
    EventoID int PRIMARY KEY,
    NomeEvento varchar(255) NOT NULL,
    DataEvento DATE,
    HoraEvento TIME,
    DataHoraEvento DATETIME,
    UltimaAtualizacao TIMESTAMP,
    AnoEvento YEAR
);
```

output:

```bash
Query OK, 0 rows affected (1.01 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Eventos;
```

output:

```bash
+-------------------+--------------+------+-----+---------+-------+
| Field             | Type         | Null | Key | Default | Extra |
+-------------------+--------------+------+-----+---------+-------+
| EventoID          | int          | NO   | PRI | NULL    |       |
| NomeEvento        | varchar(255) | NO   |     | NULL    |       |
| DataEvento        | date         | YES  |     | NULL    |       |
| HoraEvento        | time         | YES  |     | NULL    |       |
| DataHoraEvento    | datetime     | YES  |     | NULL    |       |
| UltimaAtualizacao | timestamp    | YES  |     | NULL    |       |
| AnoEvento         | year         | YES  |     | NULL    |       |
+-------------------+--------------+------+-----+---------+-------+
7 rows in set (0.00 sec)
```

Inserindo alguns registros na tabela

```sql
INSERT INTO Eventos (EventoID, NomeEvento, DataEvento, HoraEvento, DataHoraEvento, UltimaAtualizacao, AnoEvento)
VALUES (1, 'Conferência de Tecnologia', '2023-05-15', '15:30:00', '2023-05-15 15:30:00', '2023-05-15 15:30:00', 2023),
       (2, 'Workshop de Programação', '2023-06-20', '10:00:00', '2023-06-20 10:00:00', '2023-06-20 10:00:00', 2023),
       (3, 'Apresentação de Produto', '2023-07-10', '18:45:00', '2023-07-10 18:45:00', '2023-07-10 18:45:00', 2023);
```

output:

```bash
Query OK, 3 rows affected (0.09 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Exibindo os dados da tabela

```sql
SELECT * FROM Eventos;
```

output:

```bash
+----------+--------------------------+------------+------------+---------------------+---------------------+-----------+
| EventoID | NomeEvento               | DataEvento | HoraEvento | DataHoraEvento      | UltimaAtualizacao   | AnoEvento |
+----------+--------------------------+------------+------------+---------------------+---------------------+-----------+
|        1 | Conferncia de Tecnologia | 2023-05-15 | 15:30:00   | 2023-05-15 15:30:00 | 2023-05-15 15:30:00 |      2023 |
|        2 | Workshop de Programao    | 2023-06-20 | 10:00:00   | 2023-06-20 10:00:00 | 2023-06-20 10:00:00 |      2023 |
|        3 | Apresentao de Produto    | 2023-07-10 | 18:45:00   | 2023-07-10 18:45:00 | 2023-07-10 18:45:00 |      2023 |
+----------+--------------------------+------------+------------+---------------------+---------------------+-----------+
3 rows in set (0.00 sec)
```

Excluindo a tabela

```sql
DROP TABLE Eventos;
```

output:

```bash
Query OK, 0 rows affected (0.32 sec)
```

**[:arrow_up: back to top](#índice)**

#### SQL CREATE VIEW Statement

Uma visualização contém linhas e colunas, assim como uma tabela real. Os campos em uma visualização são campos de uma ou mais tabelas reais do banco de dados.

Criando uma tabela de clientes

```sql
CREATE TABLE Clientes (
    ClienteID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Email varchar(255) NOT NULL,
    Status varchar(50) DEFAULT 'Ativo'
);
```

output:

```bash
Query OK, 0 rows affected (1.20 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| ClienteID | int          | NO   | PRI | NULL    |       |
| Nome      | varchar(255) | NO   |     | NULL    |       |
| Email     | varchar(255) | NO   |     | NULL    |       |
| Status    | varchar(50)  | YES  |     | Ativo   |       |
+-----------+--------------+------+-----+---------+-------+
```

Inserindo alguns registros na tabela de clientes

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Status)
VALUES (1, 'Ana Silva', 'ana@email.com', 'Ativo'),
       (2, 'Carlos Oliveira', 'carlos@email.com', 'Inativo'),
       (3, 'Mariana Santos', 'mariana@email.com', 'Ativo');
```

output:

```bash
Query OK, 3 rows affected (0.10 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Selecionando dados da tabela Clientes

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-----------------+-------------------+---------+
| ClienteID | Nome            | Email             | Status  |
+-----------+-----------------+-------------------+---------+
|         1 | Ana Silva       | ana@email.com     | Ativo   |
|         2 | Carlos Oliveira | carlos@email.com  | Inativo |
|         3 | Mariana Santos  | mariana@email.com | Ativo   |
+-----------+-----------------+-------------------+---------+
3 rows in set (0.00 sec)
```

Criando uma view chamada ClientesAtivos

```sql
CREATE VIEW ClientesAtivos AS
SELECT ClienteID, Nome, Email
FROM Clientes
WHERE Status = 'Ativo';
```

output:

```bash
Query OK, 0 rows affected (0.18 sec)
```

Selecionando dados da view ClientesAtivos

```sql
SELECT * FROM ClientesAtivos;
```

output:

```bash
+-----------+----------------+-------------------+
| ClienteID | Nome           | Email             |
+-----------+----------------+-------------------+
|         1 | Ana Silva      | ana@email.com     |
|         3 | Mariana Santos | mariana@email.com |
+-----------+----------------+-------------------+
2 rows in set (0.00 sec)
```

Excluindo a tabela de clientes e a view

```sql
DROP TABLE Clientes;
DROP VIEW ClientesAtivos;
```

output:

```bash
Query OK, 0 rows affected (0.41 sec)
```

**[:arrow_up: back to top](#índice)**

##### SQL Updating a View

Uma visualização pode ser atualizada com a instrução CREATE OR REPLACE VIEW.

Criando uma tabela de clientes

```sql
CREATE TABLE Clientes (
    ClienteID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Email varchar(255) NOT NULL,
    Status varchar(50) DEFAULT 'Ativo',
    NivelVIP int DEFAULT 0
);
```

output:

```bash
Query OK, 0 rows affected (0.56 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| ClienteID | int          | NO   | PRI | NULL    |       |
| Nome      | varchar(255) | NO   |     | NULL    |       |
| Email     | varchar(255) | NO   |     | NULL    |       |
| Status    | varchar(50)  | YES  |     | Ativo   |       |
| NivelVIP  | int          | YES  |     | 0       |       |
+-----------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

Inserindo alguns registros na tabela de clientes

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Status, NivelVIP)
VALUES (1, 'Ana Silva', 'ana@email.com', 'Ativo', 2),
       (2, 'Carlos Oliveira', 'carlos@email.com', 'Inativo', 0),
       (3, 'Mariana Santos', 'mariana@email.com', 'Ativo', 3);
```

output:

```bash
Query OK, 3 rows affected (0.13 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Selecionando dados da tabela Clientes

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-----------------+-------------------+---------+----------+
| ClienteID | Nome            | Email             | Status  | NivelVIP |
+-----------+-----------------+-------------------+---------+----------+
|         1 | Ana Silva       | ana@email.com     | Ativo   |        2 |
|         2 | Carlos Oliveira | carlos@email.com  | Inativo |        0 |
|         3 | Mariana Santos  | mariana@email.com | Ativo   |        3 |
+-----------+-----------------+-------------------+---------+----------+
3 rows in set (0.00 sec)
```

Criando uma view chamada ClientesVIP

```sql
CREATE VIEW ClientesVIP AS
SELECT ClienteID, Nome, Email, NivelVIP
FROM Clientes
WHERE NivelVIP > 0;
```

output:

```bash
Query OK, 0 rows affected (0.18 sec)
```

Selecionando dados da view ClientesVIP

```sql
SELECT * FROM ClientesVIP;
```

output:

```bash
+-----------+----------------+-------------------+----------+
| ClienteID | Nome           | Email             | NivelVIP |
+-----------+----------------+-------------------+----------+
|         1 | Ana Silva      | ana@email.com     |        2 |
|         3 | Mariana Santos | mariana@email.com |        3 |
+-----------+----------------+-------------------+----------+
2 rows in set (0.00 sec)
```

Utilizando CREATE OR REPLACE VIEW para adicionar a coluna "Status" à view

```sql
CREATE OR REPLACE VIEW ClientesVIP AS
SELECT ClienteID, Nome, Email, NivelVIP, Status
FROM Clientes
WHERE NivelVIP > 0;
```

output:

```bash
Query OK, 0 rows affected (0.18 sec)
```

Selecionando dados da view ClientesVIP após a modificação

```sql
SELECT * FROM ClientesVIP;
```

output:

```bash
+-----------+----------------+-------------------+----------+--------+
| ClienteID | Nome           | Email             | NivelVIP | Status |
+-----------+----------------+-------------------+----------+--------+
|         1 | Ana Silva      | ana@email.com     |        2 | Ativo  |
|         3 | Mariana Santos | mariana@email.com |        3 | Ativo  |
+-----------+----------------+-------------------+----------+--------+
2 rows in set (0.01 sec)
```

Excluindo a tabela de clientes e a view

```sql
DROP TABLE Clientes;
DROP VIEW ClientesVIP;
```

output:

```bash
Query OK, 0 rows affected (0.47 sec)
Query OK, 0 rows affected (0.17 sec)
```

**[:arrow_up: back to top](#índice)**

##### SQL Dropping a View

Uma view é excluída com a instrução DROP VIEW.

Criando uma tabela de clientes

```sql
CREATE TABLE Clientes (
    ClienteID int PRIMARY KEY,
    Nome varchar(255) NOT NULL,
    Email varchar(255) NOT NULL,
    Status varchar(50) DEFAULT 'Ativo'
);
```

output:

```bash
Query OK, 0 rows affected (0.91 sec)
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

output:

```bash
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| ClienteID | int          | NO   | PRI | NULL    |       |
| Nome      | varchar(255) | NO   |     | NULL    |       |
| Email     | varchar(255) | NO   |     | NULL    |       |
| Status    | varchar(50)  | YES  |     | Ativo   |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.01 sec)
```

Inserindo alguns registros na tabela de clientes

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Status)
VALUES (1, 'Ana Silva', 'ana@email.com', 'Ativo'),
       (2, 'Carlos Oliveira', 'carlos@email.com', 'Inativo'),
       (3, 'Mariana Santos', 'mariana@email.com', 'Ativo');
```

output:

```bash
Query OK, 3 rows affected (0.11 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Selecionando dados da tabela Clientes

```sql
SELECT * FROM Clientes;
```

output:

```bash
+-----------+-----------------+-------------------+---------+
| ClienteID | Nome            | Email             | Status  |
+-----------+-----------------+-------------------+---------+
|         1 | Ana Silva       | ana@email.com     | Ativo   |
|         2 | Carlos Oliveira | carlos@email.com  | Inativo |
|         3 | Mariana Santos  | mariana@email.com | Ativo   |
+-----------+-----------------+-------------------+---------+
3 rows in set (0.00 sec)
```

Criando uma view chamada ClientesAtivos

```sql
CREATE VIEW ClientesAtivos AS
SELECT ClienteID, Nome, Email
FROM Clientes
WHERE Status = 'Ativo';
```

output:

```bash
Query OK, 0 rows affected (0.23 sec)
```

Selecionando dados da view ClientesAtivos

```sql
SELECT * FROM ClientesAtivos;
```

output:

```bash
+-----------+----------------+-------------------+
| ClienteID | Nome           | Email             |
+-----------+----------------+-------------------+
|         1 | Ana Silva      | ana@email.com     |
|         3 | Mariana Santos | mariana@email.com |
+-----------+----------------+-------------------+
2 rows in set (0.01 sec)
```

Excluindo a view ClientesAtivos

```sql
DROP VIEW ClientesAtivos;
```

output:

```bash
Query OK, 0 rows affected (0.14 sec)
```

Tentando selecionar dados da view após a exclusão
A seguinte instrução gerará um erro

```sql
SELECT * FROM ClientesAtivos;
```

output:

```bash
ERROR 1146 (42S02): Table 'TUTORIAL.ClientesAtivos' doesn't exist
```

Excluindo a tabela de clientes

```sql
DROP TABLE Clientes;
```

output:

```bash
Query OK, 0 rows affected (0.38 sec)
```

**[:arrow_up: back to top](#índice)**
