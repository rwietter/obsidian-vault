Funções geradoras criam um Interator e permite que o código seja pausado em determinado local para fazer outro processamento e continuar ao chamar o método `next()`.

```js
// 1. realiza a request
// 2. retorna o response
// 3. faz o map dos dados e chama o médodo next() para continuar após o yield
// 4. faz destruturação do primeiro item e retorna ele.
const { default: axios } = require("axios");

const api = axios.create({
  baseURL: "https://swapi.dev/api",
});

async function* apiRequest(endpoint) {
  const response = await api.get(endpoint);
  const planets = yield response;

  const [first] = planets;
  return first;
}

(() => {
  const generator = apiRequest("/planets");

  const { value: response } = await generator.next();
  const { data } = response;

  const planets = data.results.map((item) => {
    const { name, diameter, climate } = item;
    return { name, diameter, climate };
  });

  const result = await generator.next(planets);
  console.log(result);
}())
```

- [Referência](https://www.youtube.com/watch?v=zfdxfiI5wu8&t=685s)