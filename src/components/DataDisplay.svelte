<!-- src/DataDisplay.svelte -->
<script>
  import { onMount } from 'svelte';
  
  let posts = [];

  async function fetchData() {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts');
      const json = await response.json();
      posts = json;
  }

  onMount(fetchData);
</script>

{#if posts.length > 0}
  <ul>
      {#each posts as post}
          <li>
              <h3>{post.title}</h3>
              <p>{post.body}</p>
          </li>
      {/each}
  </ul>
{:else}
  <p>Loading...</p>
{/if}
