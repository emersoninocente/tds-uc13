# ✅ Aula 12 — Documentação de projeto

> • Swagger UI

---

## 🎯 Objetivos

- Documentar a API com Swagger

---
## 📝 Documentação com Swagger
> Como parte importante de nosso projeto, precisamos criar documentação das classes e métodos desenvolvidos.
> * Isto facilita o uso dos nossos programas;
> * Ajuda na manutenção do código por outros desenvolvedores;
> * Torna nosso desenvolvimento mais profissional.
---
### Etapas:
1. Instalar
```bash
npm install swagger-ui swagger-ui-express swagger-jsdoc
```
2. Precisamos importar os middlawares do Swagger no `app.js`
```js
...
import swaggerUI from 'swagger-ui-express';
import swaggerJSDoc from 'swagger-jsdoc';
...
```
3. Precisamos criar um método para o Swagger
> Neste método vamos colocar as configurações do Swagger, informando o nome da API, uma descrição, a versão da API e demais info necessárias. Precisamos informar em que arquivo ou arquivos o Swagger vai encontrar as descrições da documentação. Para isto usamos a tag `apis: []`, como trata-se de um Array podemos ter mais de um local.

`app.js`
```js
  ...
  swaggerDOCS() {
    const options = {
      definition: {
        openapi: "3.0.0",
        info: {
          title: "API",
          version: "1.0.0",
        },
      },
      apis: ['./src/routes.js'],
    };
    const swaggerSpec = swaggerJSDoc(options);
    this.server.use('/api-docs', swaggerUI.serve, swaggerUI.setup(swaggerSpec));
  }
  ...
```
4. Uma vez criado o método precisamos instanciá-lo dentro do método `constructor()`

5. Adicionar comentários JSDoc nas rotas
```js
/**
 * @swagger
 * /usuarios:
 *   post:
 *     summary: Cria um novo usuário
 *     tags: [Usuários]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             properties:
 *               nome:
 *                 type: string
 *               email:
 *                 type: string
 *               idade:
 *                 type: integer
 *     responses:
 *       201:
 *         description: Usuário criado com sucesso
 */
```
6. Rota acessível em **`http://localhost:[PORTA]/api-docs`** conforme definido no método criado.

---
## 🧮 Atividades práticas
1) Aplicar documentação na nossa API
2) Acessar a documentação gerada e validar se Ok

---
## 📚 Recursos de apoio
* [Swagger UI](https://swagger.io/tools/swagger-ui/)
* [Exemplos JSDoc + Swagger](https://github.com/Surnet/swagger-jsdoc)