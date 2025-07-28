# ⚙️ Aula 11 — Express.js e Criação de API REST

> Node.js • Express • Rotas • Controladores • Integração com MySQL

---

## 🎯 Objetivos

- Configurar servidor Express em Node.js
- Criar uma API REST básica com rotas `GET`, `POST`, `PUT`, `DELETE`
- Implementar controladores e organização de código
- Conectar a API ao banco de dados MySQL com Sequelize (ou mysql2)
- Retornar e manipular dados em formato JSON

---

## 🧱 Estrutura do Projeto
<img width="343" height="268" alt="image" src="https://github.com/user-attachments/assets/f3d79982-76f4-414e-b390-386aa8b2dcbe" />


---
## 🚀 Configuração Express
```bash
npm init -y
npm install express mysql2 dotenv
```

---
## 🚀 Lançador da aplicação
`src/app.js`
```js
const express = require("express");
const usuariosRoutes = require("./routes/usuarios");

const app = express();
app.use(express.json());

app.use("/usuarios", usuariosRoutes); // Prefixo de rota

module.exports = app;
```

`src/server.js`
```js
const app = require("./app");

const port = 3000;
app.listen(port, () => {
  console.log(`API rodando em http://localhost:${port}`);
});
```

---
## 📦 Conexão com MySQL
`.env`
```
DB_HOST=localhost
DB_USER=aluno
DB_PASSWORD=1234
DB_NAME=sistema_web
```

`src/database/mysql.js`
```js
const mysql = require("mysql2");
require("dotenv").config();

const db = mysql.createConnection({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME,
});

db.connect(err => {
  if (err) {
    console.error("Erro ao conectar no banco:", err.message);
  } else {
    console.log("Conectado ao banco de dados MySQL.");
  }
});

module.exports = db;
```
## 📋 Rotas REST
`src/routes/usuarios.js`
```js
const express = require("express");
const router = express.Router();
const usuarioController = require("../controllers/usuarioController");

router.get("/", usuarioController.listar);
router.post("/", usuarioController.criar);
router.put("/:id", usuarioController.atualizar);
router.delete("/:id", usuarioController.excluir);

module.exports = router;
```
---
## 🧠 Controlador
`src/controllers/usuarioController.js`
```js
const db = require("../database/mysql");

exports.listar = (req, res) => {
  db.query("SELECT * FROM usuarios", (err, results) => {
    if (err) return res.status(500).json({ erro: err.message });
    res.json(results);
  });
};

exports.criar = (req, res) => {
  const { nome, email, idade } = req.body;
  const sql = "INSERT INTO usuarios (nome, email, idade) VALUES (?, ?, ?)";

  db.query(sql, [nome, email, idade], err => {
    if (err) return res.status(500).json({ erro: err.message });
    res.status(201).json({ mensagem: "Usuário criado com sucesso" });
  });
};

exports.atualizar = (req, res) => {
  const id = req.params.id;
  const { nome, email, idade } = req.body;
  const sql = "UPDATE usuarios SET nome = ?, email = ?, idade = ? WHERE id = ?";

  db.query(sql, [nome, email, idade, id], err => {
    if (err) return res.status(500).json({ erro: err.message });
    res.json({ mensagem: "Usuário atualizado com sucesso" });
  });
};

exports.excluir = (req, res) => {
  const id = req.params.id;
  const sql = "DELETE FROM usuarios WHERE id = ?";

  db.query(sql, [id], err => {
    if (err) return res.status(500).json({ erro: err.message });
    res.json({ mensagem: "Usuário removido com sucesso" });
  });
};
```
---
## 🧾 Comando SQL para criação da tabela
```sql
CREATE TABLE usuarios (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100),
  email VARCHAR(100),
  idade INT
);
```
---
<img width="872" height="352" alt="image" src="https://github.com/user-attachments/assets/e579dfc9-2efd-4e67-80fc-0d28705c2b9f" />

---
## 💡 Desafio de aula
1. Criar API `cursos` com rotas REST
2. Relacionar `usuarios` e `cursos` (ex. inscrição)
3. Retornar usuários com seus cursos (JOIN)
4. Testar todas as rotas com dados reais

---
## 📚 Recursos de apoio
* [Express.js DOCs](https://expressjs.com/)
* [RESTfull API - MDN](https://developer.mozilla.org/en-US/docs/Glossary/REST)
* [Postman](https://www.postman.com/)
* [Thuder Client VS Code](https://www.thunderclient.com/)
