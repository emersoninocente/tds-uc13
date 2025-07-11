# 🚀 Aula 13 — Deploy de API Node + MySQL na Nuvem

> Railway • Render • Variáveis de Ambiente • Banco de Dados Remoto • Produção

---

## 🎯 Objetivos

- Publicar a API Express.js em ambiente online (produção)
- Configurar banco de dados remoto (MySQL em Railway ou Render)
- Ajustar variáveis de ambiente e conexão segura
- Testar API via internet com Postman/Thunder Client
- Evitar exposição de dados sensíveis

---

## 📦 Escolhendo Plataforma de Deploy

| Plataforma | Recursos gratuitos | Banco embutido | Fácil integração |
|------------|--------------------|----------------|------------------|
| Railway    | ✅ Sim              | ✅ MySQL       | 🔥 Recomendado   |
| Render     | ✅ Sim              | ❌ Externo     | 💡 Alternativa   |
| Vercel     | ❌ (apenas front)   | ❌             | ❌ Sem Node full |

---

## 🧭 Passo a passo com Railway

1. 👉 Acesse [railway.app](https://railway.app/)
2. Crie projeto com opção `Empty Project`
3. Adicione serviço **MySQL** (`New -> Provision Database`)
4. Copie dados de conexão:
   - Host, Database, User, Password, Port
5. Crie `New -> GitHub Repo` (ou arraste os arquivos do seu projeto)
6. Configure **Variables** no Railway com:
   - `DB_HOST`, `DB_USER`, `DB_PASSWORD`, `DB_NAME`

---

## 🛡️ Protegendo variáveis com `.env`

```env
DB_HOST=containers.railway.app
DB_USER=railway
DB_PASSWORD=xxxxxxxx
DB_NAME=sistema_web
```
✅ Nunca subir arquivos **`.env`** no GitHub! Use **`.gitignore`**

---
## 🔧 Ajuste o código para produção
No **`database/mysql.js`**:
```js
const db = mysql.createConnection({
  host: process.env.DB_HOST,
  port: process.env.DB_PORT || 3306,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME
});
```
---
## 🌍 Testar API em produção
Após deploy, a API ficará em:
```
https://api-sistema.up.railway.app
```
#### Exemplos:
* **`GET /usuarios`**
* **`POST /usuarios`**
* **`GET /cursos`**
* **`GET /inscricoes`**
---
## 🧪 Atividade prática
1. Criar conta no Railway
2. Subir projeto completo da API
3. Provisionar o banco MySQL
4. Testar rotas via Internet
5. Compartilhar URI com o professor e colegas
---
## 💡 Desafio extra: monitoramento de logs
* Usar **`console.log`** com data/hora nas rotas
* Criar middleware **`logDeRequisicao.js`** para exibir:
<img width="236" height="25" alt="image" src="https://github.com/user-attachments/assets/57549222-97c4-4e22-a8ab-591a68a3fdc5" />

* Registrar logs úteis de requisições

---
## 📚 Recursos complementares
* [Deploy com Railway (vídeo)](https://www.youtube.com/watch?v=3MqCa9tTHL4)
* [Deploy em texto (eng)](https://alphasec.io/how-to-deploy-a-nodejs-app-on-railway/)
* [Render.com](https://render.com/)
* [Segurança com dotenv](https://render.com/)
* [Banco remoto gratuito - alternativa ao MySQL](https://planetscale.com/)
