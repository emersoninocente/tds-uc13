# 🖱️ Aula 06 — Manipulação do DOM e Eventos com JavaScript

> DOM • Eventos • Interatividade • Alteração dinâmica de elementos

---

## 🎯 Objetivos

- Compreender o conceito de DOM (Document Object Model)
- Interagir com elementos HTML via JavaScript
- Capturar e reagir a eventos do usuário
- Alterar estilo, conteúdo e comportamento da página em tempo real

---

## 🌐 O que é o DOM?

> O DOM é uma representação em árvore da estrutura HTML que pode ser acessada e modificada com JavaScript.

Exemplo:
```html
<body>
  <h1>Olá</h1>
  <button>Clique</button>
</body>
```
> É representado assim:
<img width="145" height="78" alt="image" src="https://github.com/user-attachments/assets/1fd11afd-8cea-4c92-a8a1-502a056fca26" />

---
## 📌 Selecionando elementos
```js
document.getElementById("titulo");
document.querySelector(".botao");
document.querySelectorAll("p");
```
🎯 Permite acessar qualquer elemento HTML para leitura ou alteração.

---
## ✏️ Alterando conteúdo e estilo
```js
const titulo = document.getElementById("titulo");
titulo.innerText = "Novo título";

titulo.style.color = "red";
titulo.style.fontSize = "24px";
```
---
## 📣 Eventos: clique, input, mouseover
```js
document.getElementById("botao").addEventListener("click", function() {
  alert("Botão clicado!");
});
```
> 💡 Eventos comuns:
> * `click`
> * `mouseover`
> * `keydown`
> * `submit`
---
## 💡 Mini-projeto de aula
### Objetivo:
Criar uma página interativa que:
* Exibe mensagens ao clicar em botão
* Altera estilo de parágrafo ao passar o mouse
* Atualiza texto em tempo real com `input`
---
## 🧠 Desafio interativo
1. Criar uma página com 3 botões:
   * Um altera cor de fundo
   * Outro altera o texto principal
   * Um que altera o conteúdo entre "ON" e "OFF"
2. Implementar efeitos visuais com CSS após interação.
---
## 📚 Recursos de apoio
* [DOM - MDN](https://developer.mozilla.org/pt-BR/docs/Web/API/Document_Object_Model)
* [Eventos em JS](https://developer.mozilla.org/en-US/docs/Web/Events)
* [W3School - DOM Tutorial](https://www.w3schools.com/js/js_htmldom.asp)
