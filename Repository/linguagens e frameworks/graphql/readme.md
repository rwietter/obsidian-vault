# GraphQL

GraphQL é uma estrutura que permite personalizar nossas chamadas HTTP, evitando under-fetching e over-fetching. O GraphQL permite que nós façamos três tipos de operações:

- **Query** -> Buscar dados
- **mutations** -> PUT, DELETE, PATCH
- **Subscriptions** -> executar uma operação quando acontecer um evento

```graphql
query Article {
  articles(
    filters: {
      slug: {
        eq: "fluxo-bidirecional-no-react-com-o-hook-use-imperative-handle"
      }
    }
  ) {
    data {
      attributes {
        slug
        title
        content
        category {
          data {
            attributes {
              slug
              name
            }
          }
        }
        image {
          data {
            attributes {
              url
            }
          }
        }
      }
    }
  }
}
```