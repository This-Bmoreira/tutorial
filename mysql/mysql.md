# índice

- [Criar um container MySQL](#criar-um-container-mysql)
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
