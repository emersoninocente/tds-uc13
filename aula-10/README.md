# 📺 Aula 10 - Implementando ORM no nosso projeto

## 🎯 Objetivos
- O que é um ORM
- ORM no Nodejs - Sequelize
- Usando o Sequelize: instalação, configuração, models, migrations e seeds

---
## 🧾 ORM - Object Relational Mapping
> O mapeamento objeto relacional é uma técnica usada para criar uma ponte entre nossos programas e os bancos de dados relacionais. Podemos assim considerar que o ORM é uma camada entre conecta nossa programação OOP com as tabelas em um banco de dados.
> Por se tratar de uma camada entre os programas e o banco de dados, fica mais fácil portar nossa aplicação para outros SGBDs sem precisar severas modificações de código.
> Claro que nem tudo são maravilhas, as ferramentas de ORM tem suas vantagens e desvantagens que devem sempre ser analisadas quando vamos desenvolver algo.

### ⬆️ Vantagens
- Acelera o tempo de desenvolvimento para equipes.
- Diminui o custo de desenvolvimento.
- Lida com a lógica necessária para interagir com os bancos de dados.
- Melhora a segurança. As ferramentas ORM são construídas para eliminar a possibilidade de ataques de injeção de SQL.
- Você escreve menos código ao usar ferramentas ORM do que com SQL.

### ⬇️ Desvantagens
- Aprender a usar ferramentas ORM pode ser demorado.
- Elas provavelmente não terão um desempenho melhor quando consultas muito complexas estiverem envolvidas.
- As ferramentas de ORMs são geralmente mais lentas do que usar SQL.

---
## 🚀 Sequelize
> O **Sequelize** é uma ferramenta ORM baseada em *promises* do NodeJS com capacidade para lidar com diversos SGBDs como PostgreSQL, MariaDB, MySQL, MSSQL entre outros. Foi construido para facilitar a manipulação dos dados usando *models*, abstraindo assim o uso de querys SQL pelo uso de funções.

### ⚙️ Instalando e configurando
> O processo de instação do sequelize é bem simples e pelo uso do gerenciador de pacotes do NodeJS. Precisamos junto com a instalação do Sequelize, instalar o *dialect*, ou seja o interpretador, do banco de dados que vamos trabalhar, para cada SGBD existe um pacote específico, para melhor orientação acesse a documentação oficial do Sequelize. (https://sequelize.org/)

```bash
npm install sequelize @sequelize/mariadb
```
> Para nos ajudar no processo de desenvolvimento, podemos usar ainda um CLI do Sequelize.
```bash
npm install sequelize-cli --save-dev
```

> Vamos criar um arquivo chamado `.sequelizerc` (este arquivo tem formato js) na raiz de nosso projeto para parametrizar nosso Sequelize. Neste arquivo vamos informar os caminhos das pastas que o Sequelize vai trabalhar, usamos a lib *path* para abstrair o path do sistema operacional, deixando assim de uma forma padrão para qualquer SO.


```js
const { resolve } = require('path');

module.exports = {
    "config": resolve(__dirname, 'src', 'config', 'database.cjs'),
    "models-path": resolve(__dirname, 'src', 'models'),
    "seeders-path": resolve(__dirname, 'src', 'database', 'seeders.js'),
    "migrations-path": resolve(__dirname, 'src', 'database', 'migrations')
};
```
> Precisamos criar agora como informado acima o arquivo `src/config/database.cjs` onde vamos informar os dados de conexão com nosso SGBD. Este arquivo tem `.cjs` como extensão pois usa notação *CommonJS*. Note que este arquivo está buscando valores no nosso `.env`.

```js
require('dotenv').config();
'use strict';

module.exports = {
  "username": process.env.USERNAMEDB,
  "password": process.env.PASSWORDDB,
  "database": process.env.NAMEDB,
  "host": process.env.HOSTDB,
  "port": process.env.PORTDB,
  "dialect": process.env.DIALECTDB,
  define: {
    "timestamp": true,
    "underscored": false,
    "underscoredAll": false
  }
}
```
> Precisamos agora criar nossa classe de acesso ao banco de dados em `src/database/index.js`

```js
import Sequelize from 'sequelize';
import config from '../config/database.cjs';
//import Book from '../models/Book.js';
//import Reservation from '../models/Reservation.js';
//import User from '../models/User.js';
//import Genre from '../models/Genre.js';

//const models = [Book, Reservation, User, Genre];
class Database {
    constructor() {
        try {
          this.testConnection();
          this.connection = new Sequelize(config);
//          this.init();
//          this.sync();
        } catch (error) {
          console.error('Database connection error: ', error);
        }
    }

//    init() {
//        models.forEach(model => {
//            model.init(this.connection);
//        });
//        models.forEach(model => {
//            if (typeof model.associate === 'function') {
//                model.associate(this.connection.models);
//            }
//        });
//    }

    testConnection() {
        this.connection.authenticate()
            .then(() => {
                console.log('Database connection has been established successfully.');
            })
            .catch(err => {
                console.error('Unable to connect to the database:', err);
            });
    }

//    sync() {
//        this.connection.sync({ force: false })
//            .then(() => {
//                console.log('Database synchronized successfully.');
//            })
//            .catch(err => {
//                console.error('Error synchronizing the database:', err);
//            });
//    }
}

export default new Database();
```

### 🏗️ Criando as classes de acesso as tabelas (Models)

### Consumindo as classes criadas (Controllers)
> As classes criadas nos Controllers, servem para as chamadas das rotas consumindo as classes dos Models para acesso aos dados gravados no SGBD.



📺
🧑‍💻
🖱️
🖥️
🗃️
📱
🎙️
📣
🎨
💬
🧑‍🎨
🧱
⚖️
💡
🧩
🧠
🌍
📌
✏️
🖌️
🧭
🚀
🛡️
⚙️
🧮
🛂
🔧
🛠️
🏗️
📐
🗂️
📖
🧾
📝
📋
📦
🎯
✅
🧪
📚
➡️
⬅️
↔️
↩️
🔄
↕️
⬆️
⬇️
↖️
↘️