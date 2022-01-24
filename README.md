# Documentação API

Repositório para cadastro de pessoas e requisição de produtos.

## Endpoints

As endpoints abaixo podem ser utilizadas na criação, de usuários e na requisição de produtos pré-determinados.
Todas as endpoints precisam da baseURL especificada a seguir.

baseURL: https://hamburgueria-marcelo-server.herokuapp.com/

---

---

### CADASTRO

`BODY`

```
{
	"email": "seuemail@email.com",
	"password": "123456",
	"name": "Fulano",
}
```

`POST /users - FORMATO DA RESPOSTA - STATUS: 201`

```
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6Im1hcmNlbG9Aa2VuemllLmNvbSIsImlhdCI6MTY0MjQ1ODc0MywiZXhwIjoxNjQyNDYyMzQzLCJzdWIiOiIyIn0.IrV6pp4wgQzgxKcpK_xSTnaOZq5H_mIEgxAXt7tw68M",
  "user": {
    "email": "seuemail@email.com",
    "name": "Fulano",
    "id": 1
  }
}
```

### POSSÍVEIS ERROS

\*\* Escrever um **_BODY_** sem e-mail ou senha.

`BODY`

```
{
  "password": "123456",
  "name": "Fulano",
}
```

`POST /users - FORMATO DA RESPOSTA - STATUS: 400`

```
"Email and password are required"
```

\*\* Escrever um **_BODY_** com a senha menor que 4 caracteres.

`BODY`

```
{
  "email": "marcelo23@kenzie.com",
  "password": "123",
  "name": "Fulano",
}
```

`POST /user/register - FORMATO DA RESPOSTA - STATUS: 400`

```
"Password is too short"
```

---

### LOGIN

`BODY`

```
{
  "email": "seuemail@mail.com",
  "password": "suasenha"
}
```

`POST /login - FORMATO DA RESPOSTA - STATUS: 200`

```
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6Im1hcmNlbG9Aa2VuemllLmNvbSIsImlhdCI6MTY0MjQ1ODc0MywiZXhwIjoxNjQyNDYyMzQzLCJzdWIiOiIyIn0.IrV6pp4wgQzgxKcpK_xSTnaOZq5H_mIEgxAXt7tw68M",
  "user": {
    "email": "seuemail@email.com",
    "name": "Fulano",
    "id": 1
  }
}
```

### POSSÍVEIS ERROS

\*\* Escrever um **_BODY_** sem e-mail ou senha.

`BODY`

```
{
  "password": "123456",
}
```

`POST /users - FORMATO DA RESPOSTA - STATUS: 400`

```
"Email and password are required"
```

\*\* Escrever um **_BODY_** com um e-mail inexistente.

`BODY`

```
{
  "email": "unexistentuser@mail.com",
  "password": "123456",
}
```

`POST /users - FORMATO DA RESPOSTA - STATUS: 400`

```
"Cannot find user"
```

\*\* Escrever um **_BODY_** com a senha incorreta.

`BODY`

```
{
  "email": "unexistentuser@mail.com",
  "password": "123456",
}
```

`POST /users - FORMATO DA RESPOSTA - STATUS: 400`

```
"Incorrect password"
```

---

### ALL PRODUCTS

`GET /products - FORMATO DA RESPOSTA - STATUS: 200`

```
[
  {
    "id": 1,
    "name": "Hamburguer",
    "category": "Sanduíches",
    "price": 14,
    "img": "https://i.ibb.co/642tBWS/hamburguer.png"
  },
  {
    "id": 2,
    "name": "X-Burguer",
    "category": "Sanduíches",
    "price": 16,
    "img": "https://i.ibb.co/pRnLc5j/x-burgue.png"
  },
  {
    "id": 3,
    "name": "Big Kenzie",
    "category": "Sanduíches",
    "price": 18,
    "img": "https://i.ibb.co/DYPpcK1/big-kenzie.png"
  }
]
```

---

### PRODUCTS FILTER

Substituir **_TEXTNAME_** pelo texto que deseja filtrar.

`GET /products?name_like=TEXTNAME - FORMATO DA RESPOSTA - STATUS: 200`

```
[
  {
    "class": "FullStack Kenzie Academy",
    "institution": "Kenzie Academy",
    "how_many_months": 12,
    "actual_month": 5,
    "userId": 1,
    "id": 1
  }
]
```

**OBSERVAÇÃO**: Caso o **_TEXTNAME_** esteja em branco, todos os produtos aparecem, caso seja um valor que não exista, nenhum produto é encontrado.

`GET /products?name_like=TEXTNAME - FORMATO DA RESPOSTA - STATUS: 200`

```
[]
```
