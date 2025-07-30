# 🌐 Aula 08 - Modelando nosso projeto
## 🎯 Objetivos
---
* Tipos de arquivos executáveis do Node.js
* Preparando para iniciar novo projeto
* Modelagem do projeto
---
### 🗂️ Tipos de arquivos executáveis do Node.js
> O node tem seu código javascript gravado em arquivos com as seguintes extensões:
> * .js -> Arquivos com código javascript (usado para CMJ ou ESM)
> * .cjs -> Arquivos com código javascript usando notação **CommonJS**
> * .mjs -> Arquivos com código javascript usando notação **ES Modules**
---
### 🛠️ Procedimentos para criar um novo projeto
> Para que possamos então criar um novo projeto usando node vamos executar os passos abaixo:

1º) Criar uma nova pasta, acessar a pasta e instalar as bibliotecas do Node.js
```bash
$ cd
$ mkdir nova-api
$ cd nova-api
$ npm init -y
$ npm install express dotenv sequelize @sequelize/mariadb
$ npm install sequelize-cli --save-dev
```
2º) Preparar o gerenciador de código (git)
```bash
$ echo "node_modules/" > .gitignore
$ echo ".env" >> .gitignore
$ git init
$ git add .
$ git commit -m "Primeiro commit para início do projeto"
```
3º) Se necessário, preparar o SGBD
```bash
sudo mysql
```
Ao acessar a console do SGBD:
```sql
CREATE DATABASE minhabasededados;
CREATE USER 'meuusuario'@'localhost' IDENTIFIED BY 'minhasenhadobanco';
GRANT ALL PRIVILEGES ON minhabasededados.* TO 'meuusuario'@'localhost';
FLUSH PRIVILEGES;
```
4º) Editar o arquivo `package.json`
> Vamos editar o arquivo para identificar nosso desenvolvimento. Lembrado que é um arquivo `json`.
```json
  "name": "nome do nosso projeto",
  "version": "1.0.0 - devemos ajustar conforme o desenvolvimento evolui",
  "description": "Uma descriacao do nosso projeto",
  "main": "./src/server.js - quem deve ser iniciado",
  "type": "module",
  "author": {
    "name": "Nome do autor se for o caso",
    "email": "email de contato se necessario"
  },
  "keywords": [],
  "license": "ISC",
.
. Vai seguir com as dependências instaladas.
.
```
5º) Criar o arquivo `.env` com as variáveis de ambiente necessárias

6º) Iniciar a estrutura de pastas do projeto

7º) Iniciar o desenvolvimento do projeto

---
