<script>
  import { PUBLIC_API_URL } from "$env/static/public";
  let todos = $state([]);

  const fetchTodos = async () => {
    const response = await fetch(`${PUBLIC_API_URL}/api/todos`);
    const data = await response.json();
    todos = data;
  };

  $effect(() => {
    fetchTodos();
  });
</script>

<h1>Todos</h1>

<ul>
  {#each todos as todo}
    <li>{todo.name}</li>
  {/each}
</ul>

<nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
    <li><a href="/contact">Contact</a></li>
  </ul>
</nav>