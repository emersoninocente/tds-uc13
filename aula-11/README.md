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
<img width="280" height="280" alt="estrutura_projeto_api" src="https://github.com/user-attachments/assets/fc1d200c-d07d-4b7b-93bf-bac596ccb8a5" />

---
## 🚀 Configuração Express
```bash
npm init -y
npm install express mysql2 dotenv
```

---
`app.js`
```js
const express = require("express");
const app = express();

app.use(express.json()); // Permite JSON no corpo da requisição

module.exports = app;
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

`database/mysql.js`
```js
const mysql = require("mysql2");
require("dotenv").config();

const db = mysql.createConnection({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME
});

module.exports = db;
```
## 📋 Rotas REST
`routes/usuarios.js`
```js
const express = require("express");
const router = express.Router();
const usuarioController = require("../contr/usuarioController");

router.get("/", usuarioController.listar);
router.post("/", usuarioController.criar);
router.put("/:id", usuarioController.atualizar);
router.delete("/:id", usuarioController.excluir);

module.exports = router;
```
---
## 🧠 Controlador
`contr/usuarioController.js`
```js
const db = require("../database/mysql");

exports.listar = (req, res) => {
  db.query("SELECT * FROM usuarios", (err, results) => {
    if (err) return res.status(500).json({ erro: "Erro ao consultar" });
    res.json(results);
  });
};

exports.criar = (req, res) => {
  const { nome, email, idade } = req.body;
  db.query(
    "INSERT INTO usuarios (nome, email, idade) VALUES (?, ?, ?)",
    [nome, email, idade],
    (err) => {
      if (err) return res.status(500).json({ erro: err.message });
      res.status(201).json({ mensagem: "Usuário criado com sucesso" });
    }
  );
};

// atualizar e excluir seguem lógica semelhante
```
---
