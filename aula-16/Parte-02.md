# Modificações aplicadas no código
> Neste modelo, para aplicar o processo de documentação tratado em aula, mas ainda continuando com `Swagger` para gerar a documentação, mudamos do JSDoc para YAML (mais usado para diversas linguagens).

## Procedimentos:
> Instalar o pacote yamljs

```bash
npm install yamljs
```

> Criar o arquivo da documentação (claro que ficou longo, podemos melhorar aplicando modularização - que fica para outro momento).
`src/swagger.yaml`
```js
openapi: 3.0.0
info:
  title: nova-api
  version: 1.0.0
  description: API para aula do curso TDS, disciplina UC13.

paths:
  /users:
    get:
      summary: Lista usuários
      tags: [Users]
      description: Retorna uma lista de usuários com filtros opcionais

// Colado somente um trecho
```

> Ajustar o `src/app.js` para gerar e publicar a documentação:

```js
import express from 'express';
import { configDotenv } from 'dotenv';
import routes from './routes/index.js';
// Importa as configuracoes para BD
import './database/index.js';
// Import do Swagger para documentacao
import swaggerUI from 'swagger-ui-express';
import YAML from 'yamljs';

configDotenv();

class App {
  constructor() {
    this.server = express();
    this.middlewares();
    this.routes();
    this.swaggerYAML();
  }

  middlewares() {
    this.server.use(express.json());
  }

  routes() {
    this.server.use(routes);
  }

  swaggerYAML() {
    const swaggerDocument = YAML.load('./src/swagger.yaml');
    this.server.use('/api-docs', swaggerUI.serve, swaggerUI.setup(swaggerDocument));
  }
}

export default new App().server;
```

> Acessar http://servidor:porta/api-docs para ver o resultado e executar a validação da documentação.

---