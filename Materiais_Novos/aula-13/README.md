# ✅ Aula 14 - Controle de acesso com perfis
> Autenticação via JWT • Perfis de usuário (Admin, Comum) • Claims personalizadas • Autorização condicional
---
## 🎯 Objetivos
* Introduzir o conceito de **Claims** no token JWT
* Implementar **níveis de acesso** (admin vs comum)
* Criar rotas **restritas para administradores**
* Testar **comportamento autorizado vs negado**
* Registrar perfis no banco (sem hardcode)
---
## 🛂 Perfis e Claims - o que são?
* **Perfis:** tipo de usuário (ex: admin, aluno, gerente)
* **Claims:** informações embutidas no JWT para definir permissões
Exemplo de Claim:
<img width="375" height="121" alt="image" src="https://github.com/user-attachments/assets/0135656b-f3bb-45a5-9101-7de1a668aec0" />

> Estas informações são usadas no backend para saber **quem pode fazer o quê**.
