### Curiosidades

- No **Svelte**, componentes _child_ são chamados de _slot_

### Props

Para usar props como no React, em vez de passar como atributo do componente, exportamos como variável:

```js
import { onMount } from "svelte";

// exporta a variável para transforma-la em uma prop
export let url = "https://academy.valentinog.com/api/link/";
export let title = "A list of links";
let data = [];

onMount(async function () {
  const response = await fetch(url);
  const json = await response.json();
  data = json;
});

// App.svelte
import Fetch from "./Fetch.svelte";

const props = {
  url: "https://jsonplaceholder.typicode.com/todos",
  title: "A list of todos",
};

// A url padrão será substituida por está
<Fetch {...props} />;
```

---

### Passando dados do componente child para component owner via slot

```jsx
// Fetch component
<script>
import { onMount } from "svelte";

export let url = "https://academy.valentinog.com/api/link/";
let data = [];

onMount(async function() {
  const response = await fetch(url);
  const json = await response.json();
  data = json;
});
</script>

<slot { data } />
```

```jsx
// App component
<script>
import Fetch from "./fetch.svelte";
	
const props = {
  url: "https://jsonplaceholder.typicode.com/todos"
};
</script>

<Fetch {...props} let:data>
  <h1>A list of todos</h1>
  <ul>
    {#each data as link}
      <li>{link.title}</li>
    {/each}
  </ul>
</Fetch>
```

---

### Slot

[Slot](https://svelte.dev/tutorial/slot-props) funciona semelhante ao `children` do React e podemos fazer o fluxo bidirecional de dados, passando dados do componente child para o owner. 

```jsx
// App.svelte
<script>
	import Box from './Box.svelte';
</script>

<Box>
	<h2>Hello!</h2>
	<p>This is a box. It can contain anything.</p>
</Box>

// Box.svelte
<div class="box">
	<slot></slot>
</div>
```


---

### Manipulando eventos e modificadores de eventos

```jsx
// Form component
<script>
  export let handleSubmit = function(event) {
    // faz algo
  };
</script>

// Eventos -> on:event
<form on:submit={handleSubmit}>
  <label for="search">Search:</label>
  <input type="search" id="search" required />
  <button type="submit">Search</button>
</form>
```

```jsx
// App component
<script>
  import Form from "./Form.svelte";
</script>


<Form />
```

**Modificadores de ventos**

- Para usar um modificador de evento, basta utilizar esse operador "|" após a declaração do evento

```jsx
<form on:submit|preventDefault={handleSubmit}>
  <label for="search">Search:</label>
  <input type="search" id="search" required />
  <button type="submit">Search</button>
</form>
```