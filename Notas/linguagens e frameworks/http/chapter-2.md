# Part 2: Responses

## Query params

- **Query parms** são parametros nomeados enviado na rota após a interogação. Servem para páginação, filtros.

```javascript
// 'http://localhost:3333/users?name=john'
app.get("/users", (request, response) => {
  const name = request.query.name; // query params acessa de query
  return response.json({
    name,
  });
});
```

## Route parms

- **Route parms** são parâmetros utilizados para identificar recursos com um usuário ou produto pelo id.

```javascript
app.get("/users:id", (request, response) => {
  const id = request.params.id;
  return response.send(id);
});
```

## Request body

- O **corpo da requisição** é utilizado para criar ou alterar recursos.

```javascript
const app = express();
app.use(express.json());

/* request
    POST http://localhost:3333/user
    {
        "name": "Fish",
        "age": 25
    }
*/

app.post("/users", (request, response) => {
  const body = request.body;

  return response.json({
    user: body
  });
});
```
