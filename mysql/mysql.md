# índice

- [Criar um container MySQL](#criar-um-container-mysql)
- [SQL Básico](#sql-básico)
  - [SQL SELECT Statement](#sql-select-statement)
  - [SQL SELECT DISTINCT Statement](#sql-select-distinct-statement)
  - [SQL WHERE Clause](#sql-where-clause)
  - [SQL ORDER BY](#sql-order-by)
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
  - [SQL MIN() and MAX() Functions](#sql-min-and-max-functions)
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

**[:arrow_up: back to top](#índice)**

### SQL SELECT DISTINCT Statement

**[:arrow_up: back to top](#índice)**

### SQL WHERE Clause

**[:arrow_up: back to top](#índice)**

### SQL ORDER BY

**[:arrow_up: back to top](#índice)**

## Operadores Lógicos

**[:arrow_up: back to top](#índice)**

### SQL AND Operator

**[:arrow_up: back to top](#índice)**

### SQL OR Operator

**[:arrow_up: back to top](#índice)**

### NOT Operator

**[:arrow_up: back to top](#índice)**

## Manipulação de Dados

**[:arrow_up: back to top](#índice)**

### SQL UPDATE Statement

**[:arrow_up: back to top](#índice)**

### SQL DELETE Statement

**[:arrow_up: back to top](#índice)**

### NULL

**[:arrow_up: back to top](#índice)**

### SQL INSERT INTO Statement

**[:arrow_up: back to top](#índice)**

## Consultas Avançadas

### SQL SELECT TOP Clause

**[:arrow_up: back to top](#índice)**

### SQL MIN() and MAX() Functions

**[:arrow_up: back to top](#índice)**

### SQL COUNT() Function

**[:arrow_up: back to top](#índice)**

### SQL SUM() Function

**[:arrow_up: back to top](#índice)**

### SQL AVG() Function

**[:arrow_up: back to top](#índice)**

## Operadores de Comparação

**[:arrow_up: back to top](#índice)**

### SQL BETWEEN Operator

**[:arrow_up: back to top](#índice)**

### SQL LIKE Operator

**[:arrow_up: back to top](#índice)**

### SQL Wildcard Characters

**[:arrow_up: back to top](#índice)**

### SQL IN Operator

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
