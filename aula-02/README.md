# 🌐 Aula 2 — Fundamentos da Web

> Arquitetura Cliente-Servidor • Front-end e Back-end • Sites Estáticos e Dinâmicos

---

## 🎯 Objetivos
- Entender o funcionamento básico da Web
- Compreender o modelo cliente-servidor
- Identificar as camadas de uma aplicação web
- Diferenciar sites estáticos de dinâmicos
- Contextualizar as linguagens e tecnologias utilizadas

---

## 🧩 O que é a Web?

A Web é um sistema distribuído de documentos e aplicações interconectadas, acessadas por navegadores através de protocolos como HTTP.

### Componentes principais:
- **Navegador** (Chrome, Firefox, Edge)
- **Servidores Web** (Apache, Nginx)
- **HTTP/HTTPS** — protocolos de comunicação
- **URLs** — endereços dos recursos
- **DNS** — traduz nomes em IPs

---

## 🖥️ Cliente vs Servidor

| Aspecto         | Cliente                      | Servidor                        |
|-----------------|------------------------------|----------------------------------|
| Localização     | Navegador do usuário         | Máquina remota (host)           |
| Função          | Solicita recursos da Web     | Processa e envia resposta       |
| Exemplo         | Chrome acessando um site     | Apache/Nginx servindo páginas   |

---

## 🏗️ Arquitetura Web em Duas Camadas

### 1️⃣ Front-end (Cliente)
- Interface gráfica visível ao usuário
- Tecnologias: `HTML`, `CSS`, `JavaScript`
- Responsável por: layout, navegação, interatividade

### 2️⃣ Back-end (Servidor)
- Gerencia lógica de negócio e dados
- Tecnologias: `Node.js`, `PHP`, `Python`, `Java`, `SQL`
- Responsável por: validação, autenticação, banco de dados

---

## 🖌️ Sites Estáticos vs Dinâmicos

| Tipo       | Estático                         | Dinâmico                                  |
|------------|----------------------------------|-------------------------------------------|
| Conteúdo   | Fixo, não muda                   | Gerado sob demanda                        |
| Exemplo    | Portfólio simples                | E-commerce com login e carrinho           |
| Tecnologias| HTML, CSS                        | HTML, JS, servidor + banco de dados       |
| Alteração  | Manual                           | Automatizada por scripts ou banco         |

---

## 💬 Atividade em Sala

### Discussão Guiada
1. Liste sites estáticos e dinâmicos que você usa.
2. Quais partes são processadas no cliente? E no servidor?
3. Cite aplicações que usam autenticação e banco de dados.

---

## 🧠 Desafio Conceitual

**Contexto**: Sistema de pedidos online.

Tarefa:
- Identifique funções do front-end (ex: formulário de pedido)
- Identifique funções do back-end (ex: salvar pedido no banco)
- Desenhe o fluxo de dados desde o usuário até o servidor e de volta

---

## 📝 Exercícios Práticos

### 1. Crie arquivo de conceitos com as definições para:
* Web
* Cliente
* Servidor
* HTTP
* HTML, CSS e JS

```bash
touch conceitos.md
code conceitos.md
```

### 2. Simule uma requisição HTTP usando `curl` no terminal
```bash
curl -I https://www.exemplo.com
```

### 3. Usando `node.js`, crie um pequeno servidor local:
```js
// server.js
const http://require("http");

http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "text/html" });
  res.end("<h1>Servidor ativo!</h1>");
}).listen(3000);
```
> Executar o programa:
```bash
node server.js
```
> Acesso no navegador http://localhost:3000

## 📂 Material Extra
* [MDN - Como funciona a web](https://developer.mozilla.org/pt-BR/docs/Learn_web_development/Getting_started/Web_standards/How_the_web_works)
* [HTTP explicado](https://developer-mozilla-org.translate.goog/en-US/docs/Web/HTTP?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt-BR&_x_tr_pto=wapp)
