# Integração entre Frontend e Backend

Aplicação da atividade em sala para cadastrar, listar, editar e excluir usuários, com React, Spring Boot e PostgreSQL.

## Requisitos

- Java 21.
- Node.js 22 e npm.
- PostgreSQL em execução na porta 5432.

## Banco de dados

Execute no PostgreSQL o comando disponível em `database.sql`:

```sql
CREATE DATABASE aulaintegracao;
```

O backend utiliza o usuário `postgres`. Para configurar a senha, copie `backend/application-local.example.properties` para `backend/application-local.properties` e substitua o valor de exemplo pela senha do seu PostgreSQL. O arquivo local não é enviado ao GitHub.

Também é possível informar a senha pela variável de ambiente `DB_PASSWORD`, sem criar o arquivo local. Sem nenhuma configuração, o valor padrão é `postgres`, como no material da aula.

As tabelas são criadas ou atualizadas automaticamente pelo Hibernate ao iniciar o backend.

## Backend

No PowerShell, a partir da pasta do projeto:

```powershell
cd backend
.\mvnw.cmd spring-boot:run
```

No Linux ou macOS, utilize `./mvnw spring-boot:run` dentro de `backend`.

A API fica disponível em `http://localhost:8080/api/users`.

| Método | Caminho | Operação |
| --- | --- | --- |
| GET | `/api/users` | Listar usuários |
| GET | `/api/users/{id}` | Consultar um usuário |
| POST | `/api/users` | Cadastrar usuário |
| PUT | `/api/users/{id}` | Editar usuário |
| DELETE | `/api/users/{id}` | Excluir usuário |

Cadastro e edição recebem JSON com os campos `name` e `email`.

## Frontend

Em outro terminal, a partir da pasta do projeto:

```powershell
cd frontend
npm install
npm run dev
```

Acesse `http://localhost:5173` e mantenha o backend e o PostgreSQL em execução.

## Compilação

- Frontend: `npm run build`, dentro de `frontend`.
- Backend: `.\mvnw.cmd verify`, dentro de `backend`, no Windows; `./mvnw verify` no Linux ou macOS.
