## Primeiro dia

-   Configure ambient nodejs, yarn and vscode:
	- [Installing Node.js via package manager)](https://nodejs.org/en/download/package-manager/)
	- `cinst nodejs` 
	- `cinst nodejs.install`


-   Learn backend and frontend
```ad-note
💡 Backend:
    
- Regras de negócio.
- Conexão banco de dados.
- Envio de e-mail.
- Cominicação com webservices.
- Autenticação do usuário.
- Criptografia e segurança.
```

```ad-hint
Backend ⇒ JSON ⇒ Frontend web
Backend ⇒ JSON ⇒ Frontend mobile
Backend ⇒ JSON ⇒ Webservices

💡 Frontend: Camada que recebe os dados e renderiza para o usuário.
 ```
    
-   Create project with nodejs
	- `yarn init -y`
	- `yarn add expressjs`
    
-   Learn React and SPA 
```ad-hint
💡 **Abordagem tradicional:** *HTML/CSS/JS ⇒ Resposta(HTML) ⇒ [interface] [interface] ⇒ HTML/CSS/JS
    
Na abordagem tradicional, a cada requisição, o servidor retorna o conteúdo completo da página, contendo todo html e css

Essa abordagem limita o frontend para o browser, jáque o aplicativo mobile ou serviços externos não vão conseguir interpretar o html.*
    
Abordagem moderna (Single Page Application): JS ⇒ Resposta(json) ⇒ [html/css/js] ⇒ requisição ⇒ JS
    
Na abordagem de SPA, as requisições trazem apenas dados como resposta e, com esses dados, o frontend pode preencher as informações em tela.

A página nunca recarrega, otimizando a performance e dando vida ao conceito de SPA, retornando apenas json podemos ter quantos frontends quisermos.

O frontend recebe um json ou array do backend e renderiza os dados.*
```
    
-   Create project with Reactjs
	- `npx create-react-app frontend`
	- `cd frontend`
	- `yarn start`
    
-   Learn React Native & Expo

```ad-hint
💡 **Abordagem tradicional**: *Objective-C and Swift ⇒ .ipa ⇒ mobile Java and Kotlin ⇒ .apk ⇒ mobile

Na abordagem tradicional, criamos uma aplicação para iOS e outra para Android, e nesses casos, o trabalho se torna repetitivo tanto para criação quanto para as alterações no projeto.

Abordagem do React Native**: *React ⇒ iOS and Android
    
Todo código fonte é feito em JavaScript, esse código não é convertido em código nativo, melhor do que isso, o dispositivo passa a entender JavaScript e a interface gerada é totalmente nativa.

JavaScript core é um framework que torna a interpretação do JavaScript possível.
```

# Segundo dia

-   [x] Node.js & express.js
    
    ```jsx
    app.get('/users', (request, response) => {
      const queryParms = request.query
      console.log(queryParms);
      return response.json({
        "name": "Maurício",
      })
    })
    /* request === guarda os dados da requisição */
    /* response === retorna os dados de resposta */
    ```
    
    -   [x] Rotas e recursos
        -   Criar rota é preciso passar um caminho.
        -   /users ≤= recurso
        -   Buscar tabela no banco
    -   [x] Métodos HTTP
        -   GET ⇒ buscar alguma informação do backend
        -   POST ⇒ criar uma informação no backend
        -   PUT ⇒ alterar uma informação no backend
        -   DELETE ⇒ deletar uma informação no backend
    -   [x] Tipos de parâmetros
        -   Query parms
            -   Query parms: São parametros nomeados enviado na rota após a interogação. Servem para páginação, filtros
            -   Query parms: '[http://localhost:3333/users?name=Maurício](http://localhost:3333/users?name=Maur%C3%ADcio)'
            
            ```jsx
            app.get('/users', (request, response) => {
              const queryParms = request.query // query params acessa de query
              return response.json({
                "name": "Maurício",
              })
            })
            ```
            
        -   Route parms
            -   Route parms: Parâmetros utilizados para identificar recursos
            -   '/users/:id'
            -   Buscar dados de um único usuário
            -   Identificar um único recurso
            
            ```jsx
            app.get('/users:id', (request, response) => {
              const params = request.params // route params acessa de params
              console.log(params);
              return response.json({
                "name": "Maurício",
              })
            })
            ```
            
        -   Request body
            -   Corpo da requisição, é utilizado para criar ou alterar recursos
            
            ```jsx
            app.use(express.json()) // use querys in json format
            
            app.post('/users', (request, response) => {
              const body = request.body
              console.log(body);
            
              return response.json({
                "name": "Maurício",
              })
            })
            
            // Insomnia
            POST <http://localhost:3333/users>
            
            {
            	"name": "Fish",
            	"age": 25
            }
            ```

---

-   [x] Configurando nodemon

```bash
yarn add -D nodemon

# in package.json scripts
"scripts": {
    "start": "nodemon ./src/index.js"
 }
```

---

-   [x] Utilizando insomnia
    -   Testar rotas PUT, POST, DELETE
    -   Fazer requisições

---

-   [x] Diferenças entre bancos de dados
    -   SQL        
        -   MySQL, SQLite, PostgreSQL, Oracle, Microsoft SQL Server
        -   Mais estruturado, com regras
        -   Trabalha com relações
        -   Driver
            
            ```sql
      SELECT * FROM users
            ```
            
        -   Query Builder
            
            ```jsx
       table('users').select('*').where()
            ```
            
    -   NOSQL
        -   MongoDB, CouchDB, MariaDB

---

-   [x] Configurando banco de dados

```bash
# install dependecies
yarn add knex
yarn add sqlite3
```

-  Migrations
	- Gerar tabelas no DB
	- Gera um histórico
	
    ```bash
npx knex migrate:make create_ongs // cria uma tabela
    ```

---

-   [x] Pensando nas entidades e funcionalidades
    -   Entidades ⇒ opera o db
        -   Ongs ⇒ vai ter vários casos
        -   Casos (incident)
    -   Funcionalidades
        -   Login da Ong
        -   Cadastro da Ong
        -   Logout Ong
        -   Cadastar novos casos
        -   Deletar casos
        -   Listar casos específicos da Ong
        -   Listar todos os casos
        -   Entrar em contato Ong

---

-   [x] Limpando a estrutura
-   [ ] **Conceitos do React**
    -   [x] **Components**
        -   _Função que retorna html + lógica_
    -   [x] **JSX**
        -   _JavaScript XML_
    -   [x] Propriedades
        -   _props_
        -   _attributes_
        -   _children_
    -   [x] Estado
        -   _O estado serve para reerenderizar components, já que vaviáveis não podem_
    -   [x] Imutabilidade
        -   Dados deve ser reerciados
-   [x] Página de login
-   [x] Configurando rotas
-   [x] Cadastro de ONGs
-   [x] Listagem de casos
-   [x] Cadastro de um novo caso
-   [x] Conectando aplicação à API
-   [x] Enviar ao Github

---

## Passando attributes e pegando props

App.js

```jsx
import React from 'react';
import Header from './components/Header';
// import logo from './logo.svg';

function App() {
  return (
    <div className="App">
      {/* <img src={logo} className="App-logo" alt="logo" /> */}
      <Header title="Semana Omnistack">Week 11</Header>
    </div>
  );
}

export default App;
```

Header.js

```jsx
import React from 'react';

export default function Header({ title }) {
  return (
    <header>
      <h1>{title}</h1>
    </header>
  );
}
// (props) => <h1>{props.title}</h1>
```

## Passando texto, html e pegando props

App.js

```jsx
import React from 'react';
import Header from './components/Header';

export default function App() {
  return (
    <div className="App">
      <Header> Week 11 </Header>
    </div>
  );
}
```

Header.js

```jsx
import React from 'react';

export default function Header({ children }) {
  return (
    <header>
      <h1>{children}</h1>
    </header>
  );
}
// Children é criado automaticamente pelo react
```

## Estados

```jsx
import React, { useState } from 'react';
import Header from './components/Header';

function App() {
  let [counter, setCounter] = useState(0);
  function increment() {
    setCounter(counter++);
  }
  return (
    <div className="App">
      <Header> Contador: {counter} </Header>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

export default App;
```

### NLW

-   Database entidades:
    -   Pontos de coleta
        -   Image
        -   name
        -   e-mail
        -   whatsapp
        -   mapa (latitude e longitude)
        -   city
        -   uf
    -   Itens de coleta
        -   Image
        -   Title
    -   Relacionamento muitos para muitos, ou seja, cada ponto de coleta pode vários itens e os diferentes itens pode estar em diferentes pontos de coleta.
    -   Relacionamento de (N-N) ⇒ Pivot points_items
    -   points_items: point_id and item_id
-   **Knex**
    -   Migrations: histories of database
    -   Migrations: servem para criar tabelas de banco de dados
    -   seeds: enviar dados que precisam estar na aplicação, dados padrão
-   Serialize
    -   Retornar algo para o cliente que não esteja em formato adequado no backend, ai a gente altera

---

### NLW 3

**Databases no back-end**

-   **Driver nativo**
    -   sqlite3.query('SELECT * FROM users')
-   **Query Builder**
    -   knex('users').select('*').where('name')
-   **ORM**
    -   Converte instâncias de uma classe em objeto de relacionamento