# 🧑‍💻 Aula 1 — Ambiente de Desenvolvimento Web com Linux e MySQL

## 🎯 Objetivos
- Configurar sistema Linux Ubuntu (máquina física ou virtual)
- Instalar o MySQL, Node.js, Git e VS Code
- Testar o ambiente com comandos básicos
- Preparar ambiente para desenvolvimento web com JavaScript e banco de dados

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
```bash
CREATE DATABASE devweb;
CREATE USER 'aluno'@'localhost' IDENTIFIED BY '1234';
GRANT ALL PRIVILEGES ON devweb.* TO 'aluno'@'localhost';
FLUSH PRIVILEGES;
```

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
