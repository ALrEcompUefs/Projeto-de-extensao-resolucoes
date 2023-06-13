# Gerenciamento de usuário

## Link do repositório
https://github.com/VitorVA6/exa844-user

## Sobre
Este repositório contém o módulo de gerenciamento de usuário, responsável por autenticar usuário por login, cadastrar, excluir e editar usuários.

## Implementação do módulo
O módulo foi implementado utilizando a linguagem Javascript, onde no backend foi utilizado o framework Express e no frontend foi utilizado a biblioteca React. O módulo conta com autenticação por token JWT utilizando a biblioteca jsonwebtoken, e criptografia de senhas por meio da biblioteca bcryt. O banco de dados utilizado nesse módulo foi o MongoDB Atlas, o que permite hospedagem gratuita. O servidor Express foi hospedado no Render e o frontend hospedado no Vercel.

## API

A URL base da API é 'https://exa844-users.onrender.com'. E conta com 8 rotas:

- GET '/all': Retorna todos os usuários;
- GET '/get-user': Retorna os dados do usuário;
- POST '/register': Cadastra novo usuário;
- POST '/login': Autentica usuário retornando um token JWT;
- PUT '/update': Atualiza dados do usuário;
- PUT '/update-pw': Atualiza senha do usuário;
- PUT '/admin/:id': Permite um administrador alterar a senha de outro usuário;
- DELETE '/:id': Permite o administrador excluir a conta de um usuáro; 

## Dependências

No backend:

- bcrypt: "^5.1.0",
- cors: "^2.8.5",
- dotenv: "^16.1.4",
- express: "^4.18.2",
- jsonwebtoken: "^9.0.0",
- mongoose: "^6.11.2",
- nodemon: "^2.0.22"

No frontend:

- axios: "^1.4.0",
- react-icons: "^4.9.0",
- react-router-dom: "^6.11.2"
- tailwindcss

## Rodando a API localmente

Clone o repositório em sua máquina local:
```
git clone https://github.com/VitorVA6/exa844-user
```
Acesse o diretório da aplicação:
```
cd api
```
Instale as dependências
```
yarn
```
Execute a aplicação
```
node index.js
```

## Rodando o frontend locamente

Com o projeto já clonado entre no diretório
```
cd front
```
Instale as dependências
```
yarn
```
Execute a aplicação
```
yarn dev
```
