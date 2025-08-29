# 📦 Aula 19 - Projeto Final

## 🎯 Objetivos
- Informar as regras de negócio
- Informar processo de desenvolvimento do projeto

---
## 🛠️ Pré-requisitos
- Criar uma nova pasta para o desenvovimento do projeto
- Iniciar o projeto
- Instalar o pacotes necessários
- Iniciar o Git para versionamento do código

---
## 🧠 Especificações de Requisitos
> O sistema deve ser desenvolvido em formato de uma API usando Node.JS e banco de dados MySQL. O sistema deve tratar do cadastro de produtos para nossa empresa. Deve exisir as seguintes possibilidades no sistema:
- Listagem de todos os produtos contendo todas as informações;
- Listagem de todas as informações de um produto específico via seu EAN;
- Cadastro de um novo produto;
- Atualizar um produto, exceto alterar o EAN;
- Deletar um produto existente;

---
## 🗄️ Modelo ER

| Atributo    | Tipo            | Descrição                       |
|-------------|-----------------|---------------------------------|
| id          | INTEGER PK      | Identificador único do produto  |
| nome        | STRING          | Nome do produto                 |
| ean         | STRING          | Identificar global              |
| description | STRING          | Desscrição detalhada            |
| fabricante  | STRING          | Nome do fabricante              |
| fornecedor  | STRING          | Nome do fornecedor              |
| contatoForn | STRING          | Nome e telefone no fornecedor   |
| unidade     | STRING          | Unidade de medida (Ex.: Kg)     |
| createdAt   | DATETIME        | Data de criação                 |
| updatedAt   | DATETIME        | Data de atualização             |

---
## 🚀 Bom trabalho