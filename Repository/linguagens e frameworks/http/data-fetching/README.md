### SSR: renderização do lado do servidor

Se você exportar uma função chamada `getServerSideProps` (Server-Side Rendering) de uma página, o Next.js irá **pré-renderizar esta página em cada solicitação** usando os dados retornados por `getServerSideProps`.

```tsx
export async function getServerSideProps(context) {
  return {
    props: {}, // will be passed to the page component as props
  }
}
```

`getServerSideProps` só é executado no lado do servidor, então:

- Quando você solicita esta página diretamente, `getServerSideProps` é executada no momento da solicitação, e esta página será pré-renderizada com os adereços retornados.
- Quando você solicita esta página nas transições da página do lado do cliente por next/linkou next/router, o Next.js envia uma solicitação de API ao servidor, que executa `getServerSideProps`

`getServerSideProps` **retorna JSON que será usado para renderizar a página**. Todo esse trabalho será tratado automaticamente pelo Next.js

`getServerSideProps` **só pode ser exportado de uma página**. Você não pode exportá-lo de arquivos que não sejam de página.

Você deve usar `getServerSideProps` apenas se precisar **renderizar uma página cujos dados devem ser buscados no momento da solicitação**. Isso pode ser devido à natureza dos dados ou propriedades da solicitação (como **authorization** cabeçalhos ou **localização geográfica**). As páginas usando `getServerSideProps` serão **renderizadas no lado do servidor no momento da solicitação** e somente serão armazenadas em cache se os cabeçalhos de **controle de cache** estiverem configurados.

```tsx
function Page({ data }) {
  // Render data...
}

// This gets called on every request
export async function getServerSideProps() {
  // Fetch data from external API
  const res = await fetch(`https://.../data`)
  const data = await res.json()

  // Pass data to the page via props
  return { props: { data } }
}

export default Page
```


### SSG: geração de site estático

**getStaticPaths**

Se uma página tem Rotas Dinâmicas e usa `getStaticProps`, ela precisa definir uma lista de caminhos a serem gerados estaticamente. Quando você exporta uma função chamada `getStaticPaths` (Static Site Generation) de uma página que usa rotas dinâmicas, o Next.js pré-renderiza estaticamente todos os caminhos especificados por `getStaticPaths`.

```tsx
export async function getStaticPaths() {
  return {
    paths: [
      { params: { slug: data.slug } }
    ],
    fallback: true // false or 'blocking'
  };
}
```

Você deve usar `getStaticPaths` se estiver pré-renderizando estaticamente páginas que usam rotas dinâmicas e:

- Os dados vêm de um CMS headless
- Os dados vêm de um banco de dados
- Os dados vêm do sistema de arquivos
- Os dados podem ser armazenados em cache publicamente (não específicos do usuário)
- A página deve ser pré-renderizada (para SEO) e ser muito rápida — `getStaticProps` gera HTML e JSON arquivos, ambos podem ser armazenados em cache por um CDN para desempenho.

- `getStaticProps` é executado durante next build para qualquer paths retornado durante a compilação;
- `getStaticProps` é executado em segundo plano ao usar `fallback: true`;
- `getStaticProps` é chamado antes da renderização inicial ao usar `fallback: blocking`.

**getStaticProps**

Se você exportar uma função chamada `getStaticProps` (Static Site Generation) de uma página, o Next.js irá pré-renderizar esta página no momento da compilação usando as props retornadas por `getStaticProps`.

`getStaticProps` **sempre é executado no servidor e nunca no cliente. Ele nem será incluído no pacote JS do navegador, para que você possa escrever consultas diretas ao banco de dados sem que elas sejam enviadas aos navegadores.**

- `getStaticProps` sempre funciona durante `next build`;
- `getStaticProps` é executado em segundo plano ao usar `revalidate`;
- `getStaticProps` é executado sob demanda em segundo plano ao usar `unstable_revalidate`.

```tsx
export async function getStaticProps(context) {
  return {
    props: {}, // will be passed to the page component as props
  }
}
```

Você deve usar `getStaticProps` se:

- Os dados necessários para renderizar a página estão disponíveis no tempo de criação antes da solicitação de um usuário;
- Os dados vêm de um CMS headless;
- Os dados podem ser armazenados em cache publicamente (não específicos do usuário);
- A página deve ser pré-renderizada (para SEO) e ser muito rápida — `getStaticProps` gera HTML e JSON, ambos podem ser armazenados em cache por um CDN para desempenho.

### CSR: renderização do lado do cliente

A busca de dados do lado do cliente é útil quando sua página não requer indexação de SEO, quando você não precisa pré-renderizar seus dados ou quando o conteúdo de suas páginas precisa ser atualizado com frequência. Ao contrário das APIs de renderização do lado do servidor, você pode usar a busca de dados do lado do cliente no nível do componente.

Se feito no nível da página, os dados são buscados em tempo de execução e o conteúdo da página é atualizado à medida que os dados são alterados. Quando usado no nível do componente, os dados são buscados no momento da montagem do componente e o conteúdo do componente é atualizado à medida que os dados são alterados.

É importante observar que usar a busca de dados do lado do cliente pode afetar o desempenho de seu aplicativo e a velocidade de carregamento de suas páginas. Isso ocorre porque a busca de dados é feita no momento da montagem do componente ou das páginas e os dados não são armazenados em cache.

Para fazer CSR, é recomendado utilizar uma library de cache e revalidação, como o useSWR. Ele lida com cache, revalidação, rastreamento de foco, rebusca em intervalos e muito mais. O SWR armazenará automaticamente os dados em cache para nós e revalidará os dados se ficarem obsoletos.

```tsx
import useSWR from 'swr'

const fetcher = (...args) => fetch(...args).then((res) => res.json())

function Profile() {
  const { data, error } = useSWR('/api/profile-data', fetcher)

  if (error) return <div>Failed to load</div>
  if (!data) return <div>Loading...</div>

  return (
    <div> <h1>{data.name}</h1> <p>{data.bio}</p> </div>
  )
}
```

### ISR: Regeneração Estática Incremental

O Next.js permite que você crie ou atualize páginas estáticas depois de criar seu site. A Regeneração Estática Incremental (ISR) permite que você use a geração estática por página, sem precisar reconstruir todo o site. Com o ISR, você pode manter os benefícios da estática enquanto escala para milhões de páginas.

Para usar o ISR, adicione o `revalidate` prop a `getStaticProps`:

```tsx
function Blog({ posts }) {
  return (
    <ul> {posts.map((post) => (
        <li key={post.id}>{post.title}</li>
      ))} </ul>
  )
}

// This function gets called at build time on server-side.
// It may be called again, on a serverless function, if
// revalidation is enabled and a new request comes in
export async function getStaticProps() {
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  return {
    props: {
      posts,
    },
    // Next.js will attempt to re-generate the page:
    // - When a request comes in
    // - At most once every 10 seconds
    revalidate: 10, // In seconds
  }
}

// This function gets called at build time on server-side.
// It may be called again, on a serverless function, if
// the path has not been generated.
export async function getStaticPaths() {
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // Get the paths we want to pre-render based on posts
  const paths = posts.map((post) => ({
    params: { id: post.id },
  }))

  // We'll pre-render only these paths at build time.
  // { fallback: blocking } will server-render pages
  // on-demand if the path doesn't exist.
  return { paths, fallback: 'blocking' }
}

export default Blog
```

* Com `fallback: true`, o Next irá buscar na API caso um dado não exista de forma estática, nesse caso devemos utilizar um loading até que os dados buscados na API retornem, podemo utilizar o `isFallback` do `useRouter` para verificar. Fallback é um "plano alternativo ou de emergência" para se recuperar de um erro.

```tsx
export async function getStaticPaths() {
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  const paths = posts.map((post) => ({
    params: { id: post.slug },
  }))

  return { paths, fallback: true }
}

// Component
export const Article = ({ article }) => {
  const router = useRouter();

  if(router.isFallback) return <p>Loading...</p>

  return (
    <div>
      {article?.map(art => <p>{ article.slug }</p>)}
    </div>
  )
}
```

Quando uma solicitação é feita para uma página que foi pré-renderizada em tempo de compilação, ela inicialmente mostrará a página em cache.

- Quaisquer solicitações à página após a solicitação inicial e antes de 10 segundos também são armazenadas em cache e instantâneas.
- Após a janela de 10 segundos, a próxima solicitação ainda mostrará a página em cache (obstante).
- Next.js aciona uma regeneração da página em segundo plano.
- Depois que a página for gerada com sucesso, o Next.js invalidará o cache e mostrará a página atualizada. - Se a regeneração do plano de fundo falhar, a página antiga ainda permanecerá inalterada.

Quando uma solicitação é feita para um caminho que não foi gerado, o Next.js renderiza a página pelo servidor na primeira solicitação. Solicitações futuras servirão o arquivo estático do cache. O ISR no Vercel mantém o cache globalmente e lida com reversões.

Se você definir um revalidatetempo de 60, todos os visitantes verão a mesma versão gerada do seu site por um minuto. A única maneira de invalidar o cache é de alguém visitando essa página após o minuto ter passado.

Tratamento de erros:

Se houver um erro interno `getStaticProps` ao lidar com a regeneração do plano de fundo ou se você gerar um erro manualmente, a última página gerada com êxito continuará a ser exibida. Na próxima solicitação subsequente, Next.js tentará chamar novamente `getStaticProps`.

```tsx
export async function getStaticProps() {
  // If this request throws an uncaught error, Next.js will
  // not invalidate the currently shown page and
  // retry getStaticProps on the next request.
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  if (!res.ok) {
    // If there is a server error, you might want to
    // throw an error instead of returning so that the cache is not updated
    // until the next successful request.
    throw new Error(`Failed to fetch posts, received status ${res.status}`)
  }

  // If the request was successful, return the posts
  // and revalidate every 10 seconds.
  return {
    props: {
      posts,
    },
    revalidate: 10,
  }
}
```