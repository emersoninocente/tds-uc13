# 📱 Aula 12 - Dia 12/08/2025

## 📣 Material da aula anterior
> Executar download do arquivo [material_aula12_full.tar.bz2](https://github.com/emersoninocente/tds-uc13/blob/main/aula-10/material_aula12_full.tar.bz2) diretamente na VM Linux e vamos extrair ele na pasta da nossa API.
> Dentro do arquivo vamos encontrar a API funcional com acesso ao banco de dados e os models (relacionam-se com as tabelas) já criados. Já ajustado o UserController para o correto acesso aos dados usando a model. Ajuste no `src/database/index.js` para inicializar os models e sincronizar com o database.
> Precisamos importar a base de dados para dentro do MySQL, para isto vamos importar o arquivo minhabasededados_aula12.txt.
```bash
mysql -u meuusuario -p minhabasededados < minhabasededados_aula12.txt
```

## 🧭 Seguindo com os trabalhos
> O que precisamos agora é continuar os ajustes das regras de negócio (controllers) e ajustar todas as rotas.
- `src/routes.js`
  - Importar as controllers faltantes
  - Ajustar as rotas das reservas e generos para apontar para as classes e métodos das controllers

- `src/controllers/BookController.js`
  - Escrever os métodos

- `src/controllers/GenresController.js`
  - Escrever os métodos

- `src/controllers/ReservationController.js`
  - Escrever os métodos
