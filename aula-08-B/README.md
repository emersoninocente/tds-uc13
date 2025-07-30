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
