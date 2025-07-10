# 🧑‍🎨 Aula 04 — Revisão Prática de Front-end

> HTML5 • CSS3 • Estrutura Semântica • Layout Responsivo com Flexbox e Grid

---

## 🎯 Objetivos

- Reforçar a estrutura semântica com HTML5
- Aplicar estilização com CSS
- Criar layouts modernos com Flexbox e Grid
- Desenvolver páginas responsivas e acessíveis

---

## 🧱 Estrutura Básica de um Site Estático
revisao-frontend/

├── index.html

└── style.css

---

## 📄 HTML5 — Estrutura Semântica

### Tags principais:

```html
<header>   <!-- Cabeçalho -->
<nav>      <!-- Navegação -->
<main>     <!-- Conteúdo principal -->
<section>  <!-- Seções temáticas -->
<article>  <!-- Conteúdo independente -->
<aside>    <!-- Conteúdo auxiliar -->
<footer>   <!-- Rodapé -->
```
> 💡 Use ` alt ` em imagens, ` label ` em formulários e  ` title ` para melhorar a acessibilidade.

---
## 🎨 CSS - Estilização básica

### Estrutura de estilo externa (` style.css `):
```css
body {
  font-family: 'Segoe UI', sans-serif;
  margin: 0;
  padding: 0;
  background: #f2f2f2;
}

header, footer {
  background-color: #333;
  color: white;
  padding: 20px;
  text-align: center;
}

main {
  padding: 40px;
}
```

---
## 📐 Layout com Flexbox
### CSS
```css
.container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  gap: 20px;
}
```
### HTML
```html
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
</div>
```

---
## 🧮 Layout com Grid
### CSS
```css
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
```
### HTML
```html
<div class="grid">
  <div class="box">Conteúdo A</div>
  <div class="box">Conteúdo B</div>
</div>
```

---
## 📱 Responsividade com Media Querys
### CSS
```css
@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }

  .grid {
    grid-template-columns: 1fr;
  }
}
```
> Use desing "mobile first" e testes em diferentes tamanhos de tela.

---
![Atividaade Prática](https://github.com/user-attachments/assets/47fc00dd-abe6-4107-b956-e496f080069e)

---
## 📚 Recursos de Apoio
* [MDN HTML Semântico](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element)
* [CSS Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [CSS Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
* [Responsividade](https://developer.mozilla.org/pt-BR/docs/Learn_web_development/Core/CSS_layout/Responsive_Design)
