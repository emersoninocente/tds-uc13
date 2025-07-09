# 🧑‍💻 Aula 1 — Ambiente de Desenvolvimento Web com Linux e MySQL

## 🎯 Objetivos
- Configurar sistema Linux Ubuntu (máquina física ou virtual)
- Instalar o MySQL, Node.js, Git e VS Code
- Testar o ambiente com comandos básicos
- Preparar ambiente para desenvolvimento web com JavaScript e banco de dados

---
## 🛠️ Pré-requisitos
* Acesso à máquina (real ou virtual) com conexão internet
* Conhecimento básico de terminal (shell)

---
## 🖥️ Instalação do Linux
> Pode ser feito via máquina física, VirtualBox, ou WSL (Windows Subsystem for Linux)

### Sugestão de configuração para VM:
- Ubuntu Desktop 22.04 LTS
- 2 CPUs, 4 GB RAM, 25 GB HD
- VirtualBox Guest Additions (para melhor desempenho)

---
## 🗃️ Instalação do MySQL

```bash
sudo apt update
sudo apt install mysql-server -y
sudo systemctl start mysql
sudo systemctl enable mysql
sudo mysql
```
```sql
CREATE DATABASE devweb;
CREATE USER 'aluno'@'localhost' IDENTIFIED BY '1234';
GRANT ALL PRIVILEGES ON devweb.* TO 'aluno'@'localhost';
FLUSH PRIVILEGES;
```

---
## 🖥️ Instação do Node.js + npm

```bash
sudo apt install nodejs npm -y
node -v
npm -v
```
* Opcional: Instalação do nodemon para facilitar os testes.
```bash
sudo npm install -g nodemon
```

---
## 🔧 Instalação do Git
```bash
sudo apt install git -y
git --version
```
> Configuração inicial:
```bash
git config --global user.name "Nome do aluno"
git config --global user.email "email@doaluno.dominio"
```
---
## 🧑‍🎨 Instalação do VS Code
* Baixar o ` .deb ` do site oficial: https://code.visualstudio.com
* Instalar via terminal:
```bash
sudo dpkg -i code*.deb
```
> Abrir o VS Code e instalar as extenções abaixo:
- Live Server
- ESLint
- Prettier
- GitLens
- MySQL

---
## ✅ Teste de conectividade
Abrir o VS Code e criar arquivo JavaScript simples (`teste.js`):
```js
console.log("Ambiente configurado com sucesso!");
```
Executar com:
```bash
node teste.js
```
---
![Atividade Prática 01](https://github.com/user-attachments/assets/791ab5fb-6bb3-4e7e-b770-0c312faa6c76)
![Atividade Prática 02](https://github.com/user-attachments/assets/1700b2f4-12e2-4150-9fb4-3a11c9f203de)
![Atividade Prática 03 e 04](https://github.com/user-attachments/assets/4ea066d7-5a06-4653-8200-70c66fcf9d53)

---
## 🗂️ Referências
* [Ubuntu Download](https://ubuntu.com/download)
* [MySQL Documentação](https://dev.mysql.com/doc/)
* [Node.JS](https://nodejs.org/pt)
* [Git Official Site](https://git-scm.com/)
* [VS Code](https://code.visualstudio.com/)
