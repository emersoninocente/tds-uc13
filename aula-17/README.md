# 🧑‍🎨 Aula 17 - Aplicando autenticação
## 🎯 Objetivos
> Implementar processo de autenticação em nossa API para que possamos controlar o acesso ao dados, no processo de desenvolvimeto até agora o servidor responde com os dados de nossa base de dados a qualquer requisição encaminhada. Isto em caso de uma publicação na Internet estaria expondo dados sensíveis, bem como ficando vulnerável a pessoas que queiram prejudicar nosso sistema de livros.
> - Implementar autenticação baseado em usuário e senha
> - Após autenticação criar token para acesso as demais funcionalidades do sistema

---
## 🧠 Conceitos
> Um token é uma string de caractéres que tem por finalidade confirmar a autenticidade do cliente. O token **não é** criptografado, mas sim **assinado** usando o ***segredo*** criado no servidor.
> - **Autenticação**: Processo de comprovar o usuário que está acessando o sistema;
> - **Autorização**: Processo de validar se o usuário autenticado tem permissão de acesso ao recurso;

---
## 💬 Funcionamento
1) Usuário faz login informando usuário e senha;
2) Se login for válido, é retornado um token pelo JWT;
3) O usuário ao consultar a API, informa seu token;
4) A aplicação valida o token para seguir com o processamento da solicitação;
5) Retorno da API para o cliente.

   <img width="525" height="430" alt="image" src="https://github.com/user-attachments/assets/6eac2b9e-578d-48af-a542-876e51847e40" />

---
## 🧩 Procedimentos
1) Instalação do pacote JWT
```bash
npm install jsonwebtoken
```
> Caso queiram mais detalhes sobre o funcionamento do pacote, acesse o [link](https://www.npmjs.com/package/jsonwebtoken).

2) Criar as variáveis de ambiente no `.env`, sendo uma para um segredo para uso do JWT e qual o tempo de "vida" do token (este por padrão é aplicado em segundos).
```js
...
JWT_SECRET='informaraquiumsegredo'
JWT_EXPIRES=3600 # Tempo em segundos para 1H (60*60)
...
```

3) Criar método de login, levando em consideração nosso atual projeto, vamos criar dentro da **controller** do **usuário** um novo método chamado de *login* (poderia ter qualquer outro nome) onde vamos recuperar do corpo da requisição um json com usuário e senha do cliente. Vamos recuperar na base de dados a senha armazenada do usuário e verificar se as senhas conferem. Se Ok, vamos invocar o método *sign* do JWT para criar o token e retornar ao cliente. Vamos criar também na **model** do **usuário** um método *checkPassword* para validar a senha informada com a senha armazenada. Por fim, vamos criar nas **routes** do **usuário** uma nova rota para o processo de login. E claro, documentar tudo dentro do nosso `swagger.yaml`.

4) Agora vamos criar um middleware para validar o token. Em `src/middleware/UsersMiddleware.js`, criamos um novo método chamado *verifyToken* onde validamos se o token enviado pelo cliente é válido.

5) Implementar nas rotas os procedimentos criados.

---
### 🗃️ Arquivos
`src/controllers/UsersController.js`
```js
    ...
    async login(req, res) {
        try {
            const { email, password } = req.body;
            const user = await User.findOne({ where: {email}});
            if(!user || !await user.checkPassword(password)) {
                return res.status(401).json({ error: 'Invalid email or password' });
            }
            const token = jwt.sign({ id: user.id, email: user.email }, process.env.JWT_SECRET, { expiresIn: parseInt(process.env.JWT_EXPIRES) || '1h' });
            return res.json({ message: 'Login successful', token: token });
        } catch (err) {
            console.log('Erro: POST :: USERS.login', err);
            return res.status(500).json({ error: 'Failed to login' });
        }
    }
    ...
```

`src/models/UserModel.js`
```js
  ...
  checkPassword(password) {
    if(password === this.password && this.status === 1) {
      return true;
    }
    return false;
  }
  ...
```

`src/routes/UsersRoute.js`
```js
...
routes.post('/login', users.login);
...
```

`src/middleware/UsersMiddleware.js`
```js
    ...
    static verifyToken(req, res, next) {
        const authToken = req.headers['authorization'];
        if (!authToken) {
            return res.status(401).json({ message: 'Token not provided' });
        }
        const token = authToken.split(' ')[1];
        try {
            const decoded = jwt.verify(token, process.env.JWT_SECRET);
            req.userId = decoded.id;
            next();
        } catch (err) {
            console.log('Erro: Middleware verifyToken', err);
            return res.status(401).json({ message: 'Invalid token' });
        }
    }
    ...
``´
