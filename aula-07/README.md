# 🧑‍💻Aula 07 - Trabalhando com Rotas

## 🎯 Objetivos
 - Compreender o conceito de rotas no Node.js Express
 - Aplicar o uso de rotas

## 📌 Conceitos
### API
> Uma interface de programação de aplicativos (API) é uma forma pela qual um aplicativo solicita um serviço a outro aplicativo. Ou seja, um conjunto de rotinas, protocolos e ferramentas para construir aplicações.

### Endpoint
> Um endpoint da API é o local em que estas solicitações são atendidas.

<img width="347" height="164" alt="image" src="https://github.com/user-attachments/assets/b9b66fa6-df26-44a9-bc3e-3dad77728702" />

## 📌 O que é uma rota?

> O **roteamento** refere-se como os **endpoints** de uma aplicação (URI) respondem às requisições do cliente. Cada rota pode ter uma ou mais funções de manipulação, que são executadas quando uma rota é correspondida.

```js
const express = require('express');
const router = express.Router();

router.get('/customers', (req, res) => {
  res.send('Lista de usuários');
});

router.get('/customers/:id', (req, res) => {
  res.send(`Detalhes do usuário ID: ${req.params.id}`);
});

module.exports = router;

```
### URL - Uniform Resource Locator
> Em português: **Localizador de Recursos Universal** refere-se ao local, o *host* que deve ser acessado determinado recurso.
> Exemplo: `www.emersoninocente.com.br`
> **URL é uma parte da URI**
### URN - Uniform Resource Name
> **Nome de Recursos Universal**, ou seja o nome pelo qual o recurso será acessado. Também compõem a **URI**.
> Exemplo: `home.html`  `contato.php`
### URI - Uniform Resource Identifier
> **Identificador de Recursos Universal**, como o nome já diz, é o identificador do recurso. Nele vamos ter o protocolo usado, método para acesso, o localizador e o nome do recurso a ser acessado.
> Exemplo: `http://www.emersoninocente.com.br/index.html` se for um navegador solicitando a página o método será **GET**.
---

## Projeto Primeira API usando Express.js
> app.js
```js
import express from 'express';

const app = express();
// Montar nossas rotas
app.get('/', (req, res) => {
    res.status(200).send('Acessando a raiz da API usando GET');
});
app.post('/', (req, res) => {
    res.status(201).send('Acessando a raiz da API usando POST');
});
app.put('/', (req, res) => {
    res.status(200).send('Acessando a raiz da API usando PUT');
});
app.delete('/', (req, res) => {
    res.status(204).send();
});

export default app;
```
