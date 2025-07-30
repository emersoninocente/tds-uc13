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
