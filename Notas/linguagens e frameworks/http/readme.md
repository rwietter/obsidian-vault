# Part 1: Definitions

> Hypertext Transfer Protocol (HTTP) é um protocolo de camada de aplicação para transmissão de documentos hipermídia, como o HTML. Foi desenvolvido para comunicação entre navegadores web e servidores web, porém pode ser utilizado para outros propósitos também. Segue um modelo cliente-servidor clássico, onde um cliente abre uma conexão, executa uma requisição e espera até receber uma resposta. É também um protocolo sem estado ou stateless protocol, que significa que o servidor não mantem nenhum dado entre duas requisições (state). Apesar de ser frequentemente baseado em uma camada TCP/IP, pode ser utilizado em qualquer camada de transporte confiável.

---

## Estrutura de um Pedido

Se dissermos que um cliente e um servidor estão tendo uma conversa, um deles faz uma solicitação e o outro manda uma resposta. Usando uma solicitação HTTP, um cliente está solicitando algo de um servidor. Para realizar uma requisição ou solicitação é necessário informar:

- Method: o método diz ao servidor o que o cliente quer que ele faça.
- URL: a URL informa a ferramenta HTTP para onde enviar a solicitação.
- Protocol: definido pela ferramenta HTTP utilizada.
- Headers: as headers dão ao servidor mais informações sobre a solicitação em si.
- body: se uma solicitação usar um método que envia dados para o servidor, os dados estão incluídos no body, logo após as headers.

Exemplo:

```diff
# [Method] • [Url] • [Protocol]
+ POST https://github.com/users/user /HTTP/2

# [Headers]
- Accept: application/json
- Content-type: application/json
- Content-length: 700

# [body]
+ '{"name": "John Doe"}'
```

## Methods

- [HTTP Cats](https://http.cat/)
- [HTTP Status Dogs](https://httpstatusdogs.com/404-not-found)

```javascript
Create = POST
Read = GET
Update = PUT or PATCH
Delete = DELETE
```

- **POST**: *envia dados para o servidor e resulta em uma alteração. Requer um corpo de dados*.
- **GET**: *solicitações de dados do servidor são enviados de volta via resposta. Ele não tem um corpo*.
- **PUT**: envia dados para o servidor para criar um novo recurso ou substituir um recurso existente. Requer um corpo de dados.
- **PATCH**: envia dados ao servidor para atualizar parte de um recurso existente. Requer um corpo de dados.
- **DELETE**: solicita que um recurso seja excluído. Ele pode ter um corpo de dados se as informações necessárias para identificar o recurso a ser excluído não estiver contida na URL.

## Estrutura de uma Resposta

Depois que um cliente envia uma solicitação HTTP, o servidor envia de volta uma resposta HTTP. Cada resposta envia algumas informações:

- **Protocol**: definido pela ferramenta HTTP que está sendo usada.
- **Status code**: um número correspondente definidos pela RFC 2616, que lhe dirão como foi o processo da solicitação à resposta.
- **Status Text**: uma descrição legível humana que lhe dirá como foi o processo de solicitação de resposta.
- **Headers**: dá ao cliente mais informações sobre a resposta em si.
- **Body**: se a resposta contiver dados do servidor, ele será incluído aqui.

Exemplo:

```diff
# [Protocol] [Status code] [Status text]
+ HTTP/2 200 OK

# [Headers]
- Access-Control-Allow-Origin: *
- Access-Control-Allow-Methods: GET, POST
- Content-type: application/json

# [Body]
+ '{"name": "John"}'
```

## CORS

> CORS - Cross-Origin Resource Sharing (Compartilhamento de recursos com origens diferentes) é um mecanismo que usa cabeçalhos adicionais HTTP para informar a um navegador que permita que um aplicativo Web seja executado em uma origem (domínio) com permissão para acessar recursos selecionados de um servidor em uma origem distinta. Um aplicativo Web executa uma requisição cross-origin HTTP ao solicitar um recurso que tenha uma origem diferente (domínio, protocolo e porta) da sua própria origem.

---

Um exemplo de requisição cross-origin: o código JavaScript frontend de um aplicativo web disponível em http://domain-a.com usa XMLHttpRequest para fazer uma requisição para http://api.domain-b.com/data.json.

---

> Por motivos de segurança, navegadores restringem requisições cross-origin HTTP iniciadas por scripts. Por exemplo, XMLHttpRequest e Fetch API seguem a política de mesma origem (same-origin policy). Isso significa que um aplicativo web que faz uso dessas APIs só poderá fazer solicitações para recursos de mesma origem da qual o aplicativo foi carregado, a menos que a resposta da outra origem inclua os cabeçalhos CORS corretos.

Antes de sua solicitação original ser enviada, http enviará uma solicitação com alguns cabeçalhos como a origem e o método para verificar se a solicitação que você deseja fazer é segura. Em seguida, o servidor envia de volta uma resposta com cabeçalhos CORS como **Access-Control-Allow-Origin** e **Access-Control-Allow-Methods** que dizem ao navegador se a solicitação original é permitida.

---

[Part 2](chapter-2.md)

---

### Referências

- [A Beginner's Guide to HTTP - Part 1: Definitions](https://dev.to/abbeyperini/a-beginners-guide-to-http-part-1-definitions-38m7)
- [HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP)
- [CORS](https://developer.mozilla.org/en-US/docs/Glossary/CORS)