# 🧠 Aula 07 — Funções e Escopo em JavaScript

> Declaração • Parâmetros • Retorno • Escopo Local e Global • Arrow Functions

---

## 🎯 Objetivos

- Compreender o conceito e utilidade das funções
- Aprender a declarar funções tradicionais e modernas
- Trabalhar com parâmetros e valores de retorno
- Dominar escopos: global, local, função, bloco
- Aplicar modularização em scripts

---

## 📌 O que é uma função?

> Uma função é um bloco de código que executa uma tarefa específica e pode ser reutilizado.

```js
function saudacao() {
  console.log("Olá, bem-vindo!");
}
saudacao(); // Executa a função
```
---
## 🧾 Funções com parâmetros
```js
function apresentar(nome, idade) {
  console.log(`Nome: ${nome} — Idade: ${idade}`);
}
apresentar("Emerson", 36);
```
---
## 🔙 Retorno de valor (`return`)
```js
function somar(a, b) {
  return a + b;
}
let resultado = somar(5, 3); // resultado = 8
```
🔁 Pode retornar valores para serem usados em outras partes do código.
---
## 💡 Arrow Functions
```js
const subtrair = (a, b) => a - b;
console.log(subtrair(10, 4)); // 6
```
☕ Sintaxe moderna mais compacta (ES6)
---
## 📚 Escopo de variáveis
### Escopo Global
```js
let nome = "Ana"; // visível em todo o script
```
### Escopo local (somente dentro da função)
```js
function mostrar() {
  let idade = 30; // só existe dentro da função
}
```
### Escopo de bloco
```js
if (true) {
  let mensagem = "Dentro do bloco";
}
console.log(mensagem); // Erro: variável fora do escopo
```
---
## 🔧 Atividade prática
1. Criar função que recebe 3 notas e retorna a média
2. Criar uma função que verifica se o valor é par ou ímpar
3. Criar arrow function que multiplica dois números
4. Criar uma função que recebe um nome e retorna "Olá, [nomelido]!"
📁 Criar pasta `funcoes-js` e o arquivo `funcoes.js` para os scripts.
---
## 💪 Desafio criativo
📋 Criar um **sistema de cálculo de desconto** com base em valor e porcentagem:
```js
function calcularDesconto(valor, porcentagem) {
  const desconto = valor * (porcentagem / 100);
  return valor - desconto;
}

console.log(calcularDesconto(100, 20)); // 80
```
🎯 Adicionar *arrow function*, validação e comentários explicativos.
---
## 📚 Recursos complementares
* [Funções - MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Functions)
* [Arrow Functions](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
* [Escopo de variáveis - W3Schools](https://www.w3schools.com/js/js_scope.asp)
