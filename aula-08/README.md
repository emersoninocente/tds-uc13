# 🗃️ Aula 08 — Banco de Dados Relacional + SQL Básico

> MySQL • Estrutura de Tabelas • Comandos CRUD • Operações com dados

---

## 🎯 Objetivos

- Compreender o conceito de banco de dados relacional
- Criar e configurar banco de dados no MySQL
- Dominar comandos SQL básicos: `SELECT`, `INSERT`, `UPDATE`, `DELETE`
- Executar testes de inserção e consulta via terminal ou IDE

---

## 🧠 Conceitos Fundamentais

### 🧱 O que é um Banco Relacional?

- Armazena informações em **tabelas** conectadas por **chaves**
- Cada tabela representa uma **entidade** (ex: usuários, produtos)
- Utiliza **SQL (Structured Query Language)** como linguagem de consulta

---

## 🗂 Estrutura Inicial — MySQL

```sql
CREATE DATABASE sistema_web;
USE sistema_web;
```
---
### 🧬 Criando a tabela `usuarios`
```sql
CREATE TABLE usuarios (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100),
  email VARCHAR(100),
  idade INT
);
```
---
## 🧾 Comandos SQL Essencial (CRUD)
### Inserir dados
```sql
INSERT INTO usuarios (nome, email, idade)
VALUES ("Ana", "ana@email.com", 25);
```
### Consultar dados
```sql
SELECT * FROM usuarios;
SELECT nome, idade FROM usuarios WHERE idade > 18;
```
### Atualizar dados
```sql
UPDATE usuarios SET idade = 26 WHERE id = 1;
```
### Deletar dados
```sql
DELETE FROM usuarios WHERE id = 3;
```
---
## 🧪 Atividade prática
<img width="554" height="362" alt="image" src="https://github.com/user-attachments/assets/24edc471-f819-4023-9328-7254d57efb80" />

---
<img width="636" height="194" alt="image" src="https://github.com/user-attachments/assets/38cf0c86-e7a6-450f-b4ef-b88faa87e7b2" />

---
## 💡 Desafio extra
* Criar uma segunda tabela chamada `cursos` contendo uma chave primária sequencial, uma coluna **nome** com 100 caractéres e uma coluna **carga_horaria** que armazene inteiros.
* E realizar:
  * 3 inserções de cursos
  * Consulta de cursos com carga > 40 horas
  * Atualização do nome de um curso
  * Exclusão de um curso

---
## 📚 Recursos de apoio
* [MySQL DOCs](https://dev.mysql.com/doc/)
* [W3Schools SQL](https://www.w3schools.com/sql/)
* [DBeaver - client SQL](https://dbeaver.io/)
* [SQL Tutorial - Mode](https://mode.com/sql-tutorial/introduction-to-sql)

---
## Modelo de banco de dados
### Diagrama ER
<img width="1196" height="516" alt="image" src="https://github.com/user-attachments/assets/19d36bb9-e7c3-4945-a5d7-d6bc1a437d17" />

### SQL
```sql
CREATE OR REPLACE TABLE `users` (
	`id` INTEGER NOT NULL AUTO_INCREMENT UNIQUE,
	`nome` TEXT(65535) NOT NULL,
	`email` TEXT(65535) NOT NULL UNIQUE,
	`passwordHash` TEXT(65535) NOT NULL,
	`provider` BOOLEAN NOT NULL DEFAULT true COMMENT 'True = Ativo, False = Inativo',
	`isAdmin` BOOLEAN NOT NULL DEFAULT false COMMENT 'True = Admin, False = user',
	`onlyRead` BOOLEAN NOT NULL COMMENT 'True = somente leitura, False = user normal',
	`createdAt` DATE,
	`updatedAt` DATE,
	PRIMARY KEY(`id`)
);

CREATE OR REPLACE TABLE `customers` (
	`id` INTEGER NOT NULL AUTO_INCREMENT UNIQUE,
	`nome` TEXT(65535) NOT NULL,
	`email` TEXT(65535) NOT NULL,
	`status` BOOLEAN NOT NULL,
	`createdAt` DATE,
	`updatedAt` DATE,
	PRIMARY KEY(`id`)
);

CREATE OR REPLACE TABLE `contacts` (
	`id` INTEGER NOT NULL AUTO_INCREMENT UNIQUE,
	`name` TEXT(65535) NOT NULL,
	`email` TEXT(65535) NOT NULL,
	`status` ENUM('active', 'inactive') NOT NULL DEFAULT 'active',
	`createdAt` DATE,
	`updatedAt` DATE,
	`customerId` INTEGER NOT NULL,
	PRIMARY KEY(`id`)
);

ALTER TABLE `contacts`
ADD FOREIGN KEY(`customerId`) REFERENCES `customers`(`id`)
ON UPDATE CASCADE ON DELETE CASCADE;
```
---
## Exemplos para testes em aula
```sql
-- Criar tabela Clientes
CREATE TABLE Clientes (
    ClienteID INTEGER NOT NULL AUTO_INCREMENT UNIQUE,
    Nome VARCHAR(50),
    Cidade VARCHAR(50)
);

-- Inserir dados na tabela Clientes
INSERT INTO Clientes (Nome, Cidade) VALUES
('Ana', 'Porto Alegre'),
('Bruno', 'São Paulo'),
('Carla', 'Rio de Janeiro'),
('Diego', 'Curitiba');

-- Criar tabela Pedidos
CREATE TABLE Pedidos (
    PedidoID INTEGER NOT NULL AUTO_INCREMENT UNIQUE,
    ClienteID INT,
    Valor DECIMAL(10, 2),
    DataPedido DATE,
    FOREIGN KEY (ClienteID) REFERENCES Clientes(ClienteID)
);

-- Inserir dados na tabela Pedidos
INSERT INTO Pedidos (ClienteID, Valor, DataPedido) VALUES
(1, 150.00, '2025-07-01'),
(2, 200.00, '2025-07-15'),
(2, 300.00, '2025-07-20'),
(4, 400.00, '2025-07-25');
```
---
# 🔗 Aula 08-B — SQL Avançado + Relacionamento de Tabelas

> WHERE • ORDER BY • LIKE • JOIN • Relacionamentos

---

## 🎯 Objetivos

- Reforçar consultas SQL com filtros e ordenações
- Compreender relacionamentos entre tabelas (`1:N`, `N:M`)
- Aplicar `INNER JOIN`, `LEFT JOIN` e `RIGHT JOIN`
- Executar consultas entre dados conectados

---

## 🧾 Revisando filtros básicos

### WHERE
```sql
SELECT * FROM usuarios WHERE idade > 30;
```
### ORDER BY
```sql
SELECT * FROM usuarios ORDER BY nome ASC;
```
### LIKE
```sql
SELECT * FROM usuarios WHERE email LIKE '%@gmail.com';
```

---
## 🧬 Relacionamento 1:N (usuarios e cursos)
### Criar tabela `cursos`
```sql
CREATE TABLE cursos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100)
);
```
### Criar tabela `inscricoes` com FK
```sql
CREATE TABLE inscricoes (
  id INT AUTO_INCREMENT PRIMARY KEY,
  usuario_id INT,
  curso_id INT,
  FOREIGN KEY (usuario_id) REFERENCES usuarios(id),
  FOREIGN KEY (curso_id) REFERENCES cursos(id)
);
```
### INNER JOIN - consulta com múltiplas tabelas
```sql
SELECT usuarios.nome, cursos.nome AS curso
FROM inscricoes
INNER JOIN usuarios ON usuarios.id = inscricoes.usuario_id
INNER JOIN cursos ON cursos.id = inscricoes.curso_id;
```

---
## 🧠 Atividade prática
1. Criar banco com tabelas `usuarios`, `cursos`, `inscricoes`
2. Inserir dados de exemplo (mínimo 3 usuarios e 3 cursos)
3. Realizar inscrições
4. Executar consultas:
   * Todos os usuários com seus respectivos cursos
   * Cursos com mais de 1 inscrito
   * Usuários inscritos em determinado curso

---
## 💪 Desafio relacional
Criar novo relacionamento entre `cursos` e `categorias`
```sql
CREATE TABLE categorias (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100)
);

ALTER TABLE cursos ADD categoria_id INT;
ALTER TABLE cursos ADD FOREIGN KEY (categoria_id) REFERENCES categorias(id);
```
📌 Realizar JOIN para listar cursos e suas categorias

---
## 📚 Recursos de apoio
* [SQL JOIN - W3Schools](https://www.w3schools.com/sql/sql_join.asp)
* [Guia SQL para relacionamentos](https://sqlbolt.com/)
* [Modelo Entidade-Relacional](https://www.lucidchart.com/pages/er-diagrams)