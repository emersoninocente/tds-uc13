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
npm install swagger-ui-express swagger-jsdoc
```
2. Criar arquivo **`swagger.js`**
3. Adicionar comentários JSDoc nas rotas
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
4. Rota acessível em **`http://localhost:3000/api-docs`**
---