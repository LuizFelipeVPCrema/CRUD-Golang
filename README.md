
---

# CRUD Básico em Go

Este é um projeto simples de CRUD (Create, Read, Update, Delete) desenvolvido em **Golang** para gerenciar usuários, armazenando nome e email em um banco de dados **MySQL**.

O projeto foi criado para reforçar os conhecimentos em **Go**, **banco de dados**, **API REST**, e **Gorilla Mux**.

## 🚀 Funcionalidades

- Criar um usuário (`POST /usuarios`)
- Buscar todos os usuários (`GET /usuarios`)
- Buscar um usuário por ID (`GET /usuarios/{id}`)
- Atualizar um usuário (`PUT /usuarios/{id}`)
- Deletar um usuário (`DELETE /usuarios/{id}`)

## 📌 Tecnologias Utilizadas

- **Golang**
- **MySQL**
- **Gorilla Mux** (Router)
- **Driver MySQL para Go**

## 🛠 Configuração do Ambiente

### 1️⃣ Requisitos

- Go **1.23.5** ou superior
- MySQL instalado e rodando
- Banco de dados e tabela configurados

### 2️⃣ Configuração do Banco de Dados

Crie um banco de dados no MySQL e a tabela necessária para armazenar os usuários:

```sql
CREATE DATABASE devbook;

USE devbook;

CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE
);
```

Edite a string de conexão com o banco no arquivo `banco/banco.go`:

```go
stringConexao := "usuario:senha@/devbook?charset=utf8&parseTime=True&loc=Local"
```

Substitua `usuario` e `senha` pelos dados corretos do seu banco de dados.

### 3️⃣ Instalando as Dependências

No diretório do projeto, rode o comando:

```sh
go mod tidy
```

Isso instalará todas as dependências do projeto.

## 🔥 Executando o Projeto

Para rodar a aplicação, execute:

```sh
go run main.go
```

O servidor será iniciado na porta **5000**.

## 📡 Endpoints da API

| Método | Rota               | Descrição                           |
|--------|--------------------|-----------------------------------|
| `POST` | `/usuarios`        | Cria um novo usuário             |
| `GET`  | `/usuarios`        | Retorna todos os usuários        |
| `GET`  | `/usuarios/{id}`   | Retorna um usuário específico    |
| `PUT`  | `/usuarios/{id}`   | Atualiza um usuário              |
| `DELETE` | `/usuarios/{id}` | Deleta um usuário                |

## 📝 Exemplo de Requisição

### Criar um usuário

```sh
curl -X POST http://localhost:5000/usuarios \
     -H "Content-Type: application/json" \
     -d '{"nome": "João Silva", "email": "joao@email.com"}'
```

### Buscar todos os usuários

```sh
curl -X GET http://localhost:5000/usuarios
```

### Buscar um usuário por ID

```sh
curl -X GET http://localhost:5000/usuarios/1
```

### Atualizar um usuário

```sh
curl -X PUT http://localhost:5000/usuarios/1 \
     -H "Content-Type: application/json" \
     -d '{"nome": "João Pereira", "email": "joaopereira@email.com"}'
```

### Deletar um usuário

```sh
curl -X DELETE http://localhost:5000/usuarios/1
```

## 📜 Licença

Este projeto foi criado para fins de aprendizado e não possui uma licença específica.

---
