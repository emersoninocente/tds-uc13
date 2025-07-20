# 🧩 Aula 06 — Objetos e Arrays em JavaScript

> Modelagem de dados • Acesso e manipulação • Métodos úteis • Iteração e filtragem

---

## 🎯 Objetivos

- Compreender estruturas de dados complexas
- Criar e utilizar **arrays** e **objetos**
- Acessar e modificar propriedades e índices
- Aplicar métodos úteis: `push`, `pop`, `map`, `forEach`, `filter`
- Iterar listas e gerar relatórios dinâmicos

---

## 📦 Arrays (Vetores)

> Um array armazena uma coleção ordenada de valores.

### Criando um array:

```js
const frutas = ["maçã", "banana", "laranja"];
```
### Acessando elementos:
```js
console.log(frutas[0]); // "maçã"
```
### Adicionando elemento:
```js
frutas.push("uva"); // ["maçã", "banana", "laranja", "uva"];
```
### Removendo elemento:
```js
frutas.pop(); // ["maçã", "banana", "laranja"];
```

---
## 🧠 Objetos
> Objetos agrupam informações como chave e valor.
### Criando um objeto
```js
const pessoa = {
  nome: "Emerson",
  idade: 36,
  profissao: "Instrutor"
};
```
### Acessando propriedades:
```js
console.log(pessoa.nome); // "Emerson"
```
### Modificando valores:
```js
pessoa.idade = 37;
```

---
## 🔁 Iterando arrays
`forEach`
```js
frutas.forEach((fruta, i) => {
  console.log(`Fruta ${i + 1}: ${fruta}`);
});
```
`map` - cria novo array
```js
const maiusculas = frutas.map(fruta => fruta.toUpperCase());
```
`filter` - filtra elementos
```js
const maioresDeIdade = pessoas.filter(p => p.idade >= 18);
```

---
## 📋 Mini-projeto de aula
* Criar uma **lista de alunos** com nome e notas.

---
## 🧠 Exercícios propostos
1. Criar array de 5 números e imprimir o dobro de cada um
2. Criar objeto representando um livro (título, autor, ano)
3. Criar lista de produtos (com preço) e calcular total da compra
4. Filtrar apenas produtos acima de R$50
5. Criar função que recebe um array de objetos e retorna a média das idades

---
## 💡 Desafio extra
Modelar um **sistema de estoque** simples que lê objetos contendo o nome do produto e a quantidade em estoque e identifica se o estoque de algum item está abaixo de 5 itens. Imprimir na console o item abaixo do estoque.

---
## 📚 Recursos de apoio
* [Array - MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array)
* [Object - MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Object)
* [Métodos úteis](https://www.w3schools.com/js/js_array_methods.asp)

---
# 📡 Aula 06.5 — JSON e Consumo de API com JavaScript

> Estrutura JSON • `fetch()` • Promises • Manipulação de dados externos

---

## 🎯 Objetivos

- Compreender a estrutura e sintaxe do **JSON**
- Realizar requisições para APIs públicas com `fetch`
- Manipular dados recebidos e exibi-los no DOM
- Tratar erros e latência com **Promises** e `.catch()`

---

## 📦 O que é JSON?

> JavaScript Object Notation — formato leve e padronizado para troca de dados

### Exemplo de JSON:

```json
{
  "nome": "Emerson",
  "idade": 36,
  "cursos": ["HTML", "CSS", "JavaScript"]
}
```
🧠 Representa dados como objetos e arrays, fácil de interpretar e usar com JavaScript.

---
## 🔄 Consumo de API com `fetch`
```js
fetch("https://jsonplaceholder.typicode.com/users")
  .then(response => response.json())
  .then(data => {
    console.log("Usuários:", data);
  })
  .catch(error => {
    console.error("Erro na requisição:", error);
  });
```
📌 A função `fetch` retorna uma **Promise** e é usada para fazer requisições HTTP (GET, POST, etc.)

---
## 🧾 Acessando dados da resposta
```js
data.forEach(usuario => {
  console.log(`${usuario.name} - ${usuario.email}`);
});
```
📋 Pode-se iterar, exibir, filtrar e até exibir dinamicamente na interface.

---
## 🔧 Mini-projeto: Listagem de usuários
1. Criar página com botão: **"Carregar usuários"**
2. Ao clicar, usar `fetch()` para consumir dados da API pública
3. Exibir nome e e-mail de cada usuário em uma `<ul>` na página

---
## 🧠 Exercícios interativos
1. Consumir uma API com dados aleatórios (https://randomuser.me/api)
2. Criar função que exibe o nome e foto do usuário recebido
3. Tratar erros e mostrar mensagem amigável caso a API falhe

---
## 📚 Recursos de apoio
* [JSON - MDN](https://developer.mozilla.org/pt-BR/docs/Learn_web_development/Core/Scripting/JSON)
* [API - MDN](https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API)
* [JSONPlaceholder (API Gratuita](https://jsonplaceholder.typicode.com/)
* [RandomUser API](https://randomuser.me/)
