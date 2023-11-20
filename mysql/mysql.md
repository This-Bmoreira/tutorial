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

- Exibindo a estrutura da tabela

```sql
DESCRIBE Employees;
```

Inserindo dados na tabela com valores não nulos

```sql
INSERT INTO Employees (EmployeeID, LastName, FirstName, Department)
VALUES (1, 'Silva', 'Ana', 'HR'),
       (2, 'Santos', 'Carlos', 'IT'),
       (3, 'Oliveira', 'Mariana', 'Finance');
```

```sql
SELECT * FROM Employees;
```

A seguinte instrução gerará um erro porque a coluna "FirstName" não aceita valores nulos

```sql
INSERT INTO Employees (EmployeeID, LastName, FirstName, Department)
 VALUES (4, 'Pereira', NULL, 'Marketing');
```

Excluindo a tabela

```sql
DROP TABLE Employees;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Students;
```

Inserindo dados na tabela

```sql
INSERT INTO Students (StudentID, FirstName, LastName, Grade)
VALUES (1, 'João', 'Silva', 90),
       (2, 'Ana', 'Santos', 85),
       (3, 'Carlos', 'Oliveira', 20);
```

Exibindo os dados antes de aplicar a restrição NOT NULL

```sql
SELECT * FROM Students;
```

Adicionando a restrição NOT NULL à coluna "Grade" usando ALTER TABLE

```sql
ALTER TABLE Students
ALTER COLUMN Grade int NOT NULL;
```

Exibindo os dados após aplicar a restrição NOT NULL

```sql
SELECT * FROM Students;
```

Excluindo a tabela

```sql
DROP TABLE Students;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Employees;
DESCRIBE EmployeesWithCompositeUnique;
```

Inserindo dados na tabela

```sql
INSERT INTO Employees (EmployeeID, LastName, FirstName, Age)
VALUES (1, 'Silva', 'Ana', 30),
       (2, 'Santos', 'Carlos', 25),
       (3, 'Oliveira', 'Mariana', 28);
```

```sql
INSERT INTO EmployeesWithCompositeUnique (EmployeeID, LastName, FirstName, Age)
VALUES (1, 'Silva', 'Ana', 30),
       (2, 'Santos', 'Carlos', 25),
       (3, 'Oliveira', 'Mariana', 28);
```

Exibindo os dados antes

```sql
SELECT * FROM Employees;
SELECT * FROM EmployeesWithCompositeUnique
```

Tentativa de inserir um registro com o mesmo valor na coluna "EmployeeID", resultará em erro

```sql
INSERT INTO Employees (EmployeeID, LastName, FirstName, Age)
VALUES (1, 'Pereira', 'João', 22);
```

Tentativa de inserir um registro com a mesma combinação de "EmployeeID" e "LastName", resultará em erro

```sql
INSERT INTO EmployeesWithCompositeUnique (EmployeeID, LastName, FirstName, Age)
VALUES (1, 'Silva', 'João', 22);
```

Excluindo a tabela

```sql
DROP TABLE Employees;
DROP TABLE EmployeesWithCompositeUnique;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Customers;
```

Inserindo dados na tabela

```sql
INSERT INTO Customers (CustomerID, FirstName, LastName, Email, Age)
VALUES (1, 'João', 'Silva', 'joao@example.com', 30),
       (2, 'Ana', 'Santos', 'ana@example.com', 25),
       (3, 'Carlos', 'Oliveira', 'carlos@example.com', 28);
```

Exibindo dados antes de adicionar a restrição UNIQUE

```sql
SELECT * FROM Customers;
```

Adicionando a restrição UNIQUE à coluna "CustomerID"

```sql
ALTER TABLE Customers
ADD UNIQUE (CustomerID);
```

Tentativa de adicionar um novo registro com o mesmo valor em "CustomerID", resultará em erro

```sql
INSERT INTO Customers (CustomerID, FirstName, LastName, Email, Age)
VALUES (1, 'Pereira', 'Mariana', 'mariana@example.com', 22);
```

Adicionando a restrição UNIQUE composta nas colunas "CustomerID" e "Email"

```sql
ALTER TABLE Customers
ADD CONSTRAINT UC_Customers UNIQUE (CustomerID, Email);
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Customers;
```

Tentativa de adicionar um novo registro com o mesmo valor em "CustomerID" ou "Email", resultará em erro

```sql
INSERT INTO Customers (CustomerID, FirstName, LastName, Email, Age)
VALUES (4, 'Fernando', 'Pereira', 'joao@example.com', 35);
```

Exibindo dados após adicionar as restrições UNIQUE

```sql
SELECT * FROM Customers;
```

Excluindo a tabela

```sql
DROP TABLE Customers;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Students;
```

Inserindo dados na tabela

```sql
INSERT INTO Students (StudentID, FirstName, LastName, Age)
VALUES (1, 'João', 'Silva', 20),
       (2, 'Ana', 'Santos', 22),
       (3, 'Carlos', 'Oliveira', 25);
```

Exibindo dados antes de remover a restrição UNIQUE

```sql
SELECT * FROM Students;
```

Removendo a restrição UNIQUE da coluna "StudentID"
No MySQL, a restrição UNIQUE é implementada como um índice, portanto, usamos DROP INDEX

```sql
ALTER TABLE Students
DROP INDEX StudentID;
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Students;
```

Tentativa de adicionar um novo registro com o mesmo valor em "StudentID", não resultará em erro

```sql
INSERT INTO Students (StudentID, FirstName, LastName, Age)
VALUES (1, 'Sabrina', 'Silva', 20),
```

Exibindo dados após remover a restrição UNIQUE

```sql
SELECT * FROM Students;
```

Excluindo a tabela

```sql
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

Inserir dados na tabela "Clientes"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Telefone)
VALUES
    (1, 'João Silva', 'joao@email.com', '123-456-7890'),
    (2, 'Maria Oliveira', 'maria@email.com', '987-654-3210'),
    (3, 'Carlos Souza', 'carlos@email.com', '555-123-4567');
```

Exibindo dados

```sql
SELECT * FROM Clientes;
```

Excluindo a tabela

```sql
DROP TABLE Clientes;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Produtos;
```

Inserir alguns dados na tabela "Produtos"

```sql
INSERT INTO Produtos (ProdutoID, Nome, Categoria, Preco)
VALUES
    (1, 'Camiseta', 'Roupas', 19.99),
    (2, 'Notebook', 'Eletrônicos', 899.99),
    (3, 'Livro', 'Literatura', 12.50);
```

Exibindo dados

```sql
SELECT * FROM Produtos;
```

Agora, adicionar uma PRIMARY KEY à coluna "ProdutoID" usando ALTER TABLE

```sql
ALTER TABLE Produtos
ADD PRIMARY KEY (ProdutoID);
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Produtos;
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Funcionarios;
```

```sql
INSERT INTO Funcionarios (FuncionarioID, Nome, Cargo, Salario)
VALUES
    (1, 'Ana Silva', 'Analista de Marketing', 5000.00),
    (2, 'Pedro Oliveira', 'Desenvolvedor Web', 7000.00),
    (3, 'Mariana Santos', 'Gerente de Projetos', 9000.00);
```

Exibindo dados

```sql
SELECT * FROM Funcionarios;
```

Agora, remover a PRIMARY KEY da coluna "FuncionarioID" usando ALTER TABLE

```sql
ALTER TABLE Persons
DROP PRIMARY KEY; 
```

Exibindo a estrutura da tabela após remover a PRIMARY KEY

```sql
DESCRIBE Funcionarios;
```

Excluindo a tabela

```sql
DROP TABLE Funcionarios;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

Inserir alguns dados na tabela "Clientes"

```sql
INSERT INTO Clientes (PersonID, LastName, FirstName, Age)
VALUES
    (1, 'Hansen', 'Ola', 30),
    (2, 'Svendson', 'Tove', 23),
    (3, 'Pettersen', 'Kari', 20);
```

Exibir dados na tabela "Clientes"

```sql
SELECT * FROM Clientes;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Pedidos;
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

Exibir dados na tabela "Pedidos"

```sql
SELECT * FROM Pedidos;
```

Excluindo a tabela

```sql
DROP TABLE Pedidos;
DROP TABLE Clientes;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

Inserir alguns dados na tabela "Clientes"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Telefone)
VALUES
    (1, 'João Silva', 'joao@email.com', '123-456-7890'),
    (2, 'Maria Oliveira', 'maria@email.com', '987-654-3210'),
    (3, 'Carlos Souza', 'carlos@email.com', '555-123-4567');
```

Criar a tabela "Vendas" sem chave estrangeira

```sql
CREATE TABLE Vendas (
    VendaID INT PRIMARY KEY,
    Valor DECIMAL(10, 2) NOT NULL,
    ClienteID INT
);
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Vendas;
```

Inserir alguns dados na tabela "Vendas"

```sql
INSERT INTO Vendas (VendaID, Valor, ClienteID)
VALUES
    (1, 100.00, 1), -- Venda de João Silva
    (2, 150.50, 2), -- Venda de Maria Oliveira
    (3, 75.25, 3);  -- Venda de Carlos Souza
```

Exibir dados na tabela "Vendas" antes de adicionar a FOREIGN KEY

```sql
SELECT * FROM Vendas;
```

Agora, adicionar uma FOREIGN KEY à coluna "ClienteID" usando ALTER TABLE

```sql
ALTER TABLE Vendas
ADD FOREIGN KEY (ClienteID) REFERENCES Clientes(ClienteID);
```

Exibindo a estrutura da tabela

```sql
DESCRIBE Vendas;
```

Excluindo a tabela

```sql
DROP TABLE Clientes;
DROP TABLE Vendas;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Produtos;
```

Inserir alguns dados na tabela "Produtos"

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES
    (1, 'Camiseta', 19.99),
    (2, 'Notebook', 899.99),
    (3, 'Livro', 12.50);
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

Exibindo a estrutura da tabela

```sql
DESCRIBE ItensVenda;
```

Inserir alguns dados na tabela "ItensVenda"

```sql
INSERT INTO ItensVenda (ItemID, Quantidade, ProdutoID)
VALUES
    (1, 3, 1), -- 3 Camisetas vendidas
    (2, 1, 2), -- 1 Notebook vendido
    (3, 5, 3); -- 5 Livros vendidos
```

Exibir dados na tabela "ItensVenda" antes de remover a FOREIGN KEY

```sql
SELECT * FROM ItensVenda;
```

Agora, remover a FOREIGN KEY usando ALTER TABLE

```sql
ALTER TABLE ItensVenda
DROP FOREIGN KEY;
```

Exibindo a estrutura da tabela

```sql
DESCRIBE ItensVenda;
```

Exibir dados na tabela "ItensVenda" após remover a FOREIGN KEY

```sql
SELECT * FROM ItensVenda;
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
DROP TABLE ItensVenda;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Produtos;
```

Inserindo dados na tabela com valores que atendem à restrição CHECK

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES (1, 'Notebook', 2500.00),
       (2, 'Smartphone', 1200.50),
       (3, 'Fones de Ouvido', 80.99);
```

Exibindo os dados da tabela

```sql
SELECT * FROM Produtos;
```

A seguinte instrução gerará um erro porque o valor do "Preco" não é maior que zero

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES (4, 'Mouse', 0.00);
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
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

Exibindo a estrutura da tabela antes da restrição CHECK

```sql
DESCRIBE Jogadores;
```

Inserindo dados na tabela

```sql
INSERT INTO Jogadores (JogadorID, Nome, Pontuacao)
VALUES (1, 'Ronaldo', 25),
       (2, 'Messi', 30),
       (3, 'Neymar', 15);
```

Exibindo os dados antes de aplicar a restrição CHECK

```sql
SELECT * FROM Jogadores;
```

Adicionando a restrição CHECK à coluna "Pontuacao" usando ALTER TABLE

```sql
ALTER TABLE Jogadores
ADD CHECK (Pontuacao >= 0);
```

Exibindo a estrutura da tabela após a adição da restrição CHECK

```sql
DESCRIBE Jogadores;
```

A seguinte instrução gerará um erro porque a restrição CHECK não é atendida

```sql
INSERT INTO Jogadores (JogadorID, Nome, Pontuacao)
VALUES (4, 'Mbappe', -5);
```

Exibindo os dados após a adição da restrição CHECK

```sql
SELECT * FROM Jogadores;
```

Excluindo a tabela

```sql
DROP TABLE Jogadores;
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

Exibindo a estrutura da tabela antes de remover a restrição CHECK

```sql
DESCRIBE ContasBancarias;
```

Inserindo dados na tabela

```sql
INSERT INTO ContasBancarias (ContaID, Titular, Saldo)
VALUES (1, 'João Silva', 5000.00),
       (2, 'Maria Santos', 10000.50),
       (3, 'Carlos Oliveira', 1500.75);
```

Exibindo os dados antes de remover a restrição CHECK

```sql
SELECT * FROM ContasBancarias;
```

Removendo a restrição CHECK à coluna "Saldo" usando ALTER TABLE

```sql
ALTER TABLE ContasBancarias
DROP CHECK CHK_Saldo;
```

Exibindo a estrutura da tabela após remover a restrição CHECK

```sql
DESCRIBE ContasBancarias;
```

Excluindo a tabela

```sql
DROP TABLE ContasBancarias;
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

Exibindo a estrutura da tabela

```sql
DESCRIBE Clientes;
```

Inserindo dados na tabela sem fornecer um valor para a coluna "Cidade"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email)
VALUES (1, 'Ana Silva', 'ana@email.com'),
       (2, 'Carlos Oliveira', 'carlos@email.com'),
       (3, 'Mariana Santos', 'mariana@email.com');
```

Exibindo os dados da tabela

```sql
SELECT * FROM Clientes;
```

Inserindo dados na tabela fornecendo um valor específico para a coluna "Cidade"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Cidade)
VALUES (4, 'Pedro Pereira', 'pedro@email.com', 'São Paulo');
```

Exibindo os dados da tabela após a inserção com valor específico para a coluna "Cidade"

```sql
SELECT * FROM Clientes;
```

Excluindo a tabela

```sql
DROP TABLE Clientes;
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

Exibindo a estrutura da tabela antes da restrição DEFAULT

```sql
DESCRIBE Clientes;
```

Inserindo dados na tabela

```sql
INSERT INTO Clientes (ClienteID, Nome, Email)
VALUES (1, 'Ana Silva', 'ana@email.com'),
       (2, 'Carlos Oliveira', 'carlos@email.com'),
       (3, 'Mariana Santos', 'mariana@email.com');
```

Exibindo os dados antes de aplicar a restrição DEFAULT

```sql
SELECT * FROM Clientes;
```

Adicionando a restrição DEFAULT à coluna "Estado" usando ALTER TABLE

```sql
ALTER TABLE Clientes
ALTER Estado SET DEFAULT 'Rio de Janeiro';
```

Exibindo a estrutura da tabela após adicionar a restrição DEFAULT

```sql
DESCRIBE Clientes;
```

Inserindo dados na tabela sem fornecer um valor para a coluna "Estado"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email)
VALUES (4, 'Pedro Pereira', 'pedro@email.com');
```

Exibindo os dados após a inserção sem fornecer um valor para a coluna "Estado"

```sql
SELECT * FROM Clientes;
```

Inserindo dados na tabela fornecendo um valor específico para a coluna "Estado"

```sql
INSERT INTO Clientes (ClienteID, Nome, Email, Estado)
VALUES (5, 'Maria Oliveira', 'maria@email.com', 'São Paulo');
```

Exibindo os dados após a inserção com valor específico para a coluna "Estado"

```sql
SELECT * FROM Clientes;
```

Excluindo a tabela

```sql
DROP TABLE Clientes;
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

Exibindo a estrutura da tabela antes de remover a restrição DEFAULT

```sql
DESCRIBE Produtos;
```


Inserindo dados na tabela sem fornecer um valor para a coluna "Tipo"

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES (1, 'Notebook', 2500.00),
       (2, 'Smartphone', 1200.50),
       (3, 'Fones de Ouvido', 80.99);
```

Exibindo os dados da tabela antes de remover a restrição DEFAULT

```sql
SELECT * FROM Produtos;
```

Removendo a restrição DEFAULT à coluna "Tipo" usando ALTER TABLE

```sql
ALTER TABLE Produtos
ALTER Tipo DROP DEFAULT;
```

Exibindo a estrutura da tabela após remover a restrição DEFAULT

```sql
DESCRIBE Produtos;
```

Inserindo dados na tabela sem fornecer um valor para a coluna "Tipo" após a remoção

```sql
INSERT INTO Produtos (ProdutoID, Nome, Preco)
VALUES (4, 'Mouse', 25.00),
       (5, 'Teclado', 50.00);
```

Exibindo os dados da tabela após a inserção sem fornecer um valor para a coluna "Tipo"

```sql
SELECT * FROM Produtos;
```

Excluindo a tabela

```sql
DROP TABLE Produtos;
```

**[:arrow_up: back to top](#índice)**
