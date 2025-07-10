# ✅ Aula 12 — Validação, Testes Automatizados e Documentação de API REST

> Express.js • Middleware de validação • Testes com Jest + Supertest • Swagger UI

---

## 🎯 Objetivos

- Implementar validações de entrada (nome, email, idade etc.)
- Criar testes automatizados das rotas com Supertest e Jest
- Documentar a API com Swagger
- Garantir segurança, clareza e confiabilidade na API

---

## 🧪 Validação de Dados

### Middleware de validação (exemplo para `usuarios`)

```js
function validarUsuario(req, res, next) {
  const { nome, email, idade } = req.body;
  if (!nome || typeof nome !== "string") {
    return res.status(400).json({ erro: "Nome inválido" });
  }
  if (!email.includes("@")) {
    return res.status(400).json({ erro: "Email inválido" });
  }
  if (!Number.isInteger(idade) || idade < 0) {
    return res.status(400).json({ erro: "Idade inválida" });
  }
  next(); // segue para a rota
}
```
### Usar nas rotas
```js
router.post("/", validarUsuario, usuarioController.criar);
```

---
## 📦 Testes automatizados com Supertest e Jest
### Fluxo sugerido de testes
1. Criar usuário
2. Listar usuários
3. Atualizar registro
4. Deletar usuário
5. Validar erro em requisição malformada
#### Exemplo:
```js
test("POST inválido", async () => {
  const res = await request(app).post("/usuarios").send({ nome: "", email: "x", idade: -2 });
  expect(res.statusCode).toBe(400);
  expect(res.body.erro).toBeDefined();
});
```
🧠 **Dica prática:** Use **`afterAll()`** para fechar o banco e limpar registros no **`beforeEach()`** se necessário.

---
## 📝 Documentação com Swagger
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
## 🔧 Atividade prática
1. Criar validações para todas rotas de criação:
   * usuários
   * cursos
   * inscrições
2. Adicionar testes para:
   * requisição válida
   * requisição inválida
   * consulta de lista com dados esperados
3. Comentar cada rota com Swagger e revisar a visualização

---
## 📚 Recursos de apoio
* [Express Middleware](https://expressjs.com/en/guide/writing-middleware.html)
* [Supertest Docs](https://github.com/forwardemail/supertest)
* [Jet Docs](https://jestjs.io/)
* [Swagger UI](https://swagger.io/tools/swagger-ui/)
* [Exemplos JSDoc + Swagger](https://github.com/Surnet/swagger-jsdoc)
