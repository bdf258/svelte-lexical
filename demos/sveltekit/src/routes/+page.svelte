<script lang="ts">
  import { LexicalEditor } from 'lexical';
  import '../global.css';

</script>

<main>
  <img src="images/logo.svg" alt="Svelte Lexical!" />
  <p>
    Welcome to <a href="https://github.com/umaranis/svelte-lexical/">
      svelte-lexical
    </a>
    demo built using
    <a href="https://kit.svelte.dev">SvelteKit</a>
  </p>
  <div>
    <button style="margin-bottom: 1em; background: black; color: white;">Click me</button>
  </div>
    <div>
  <div style="text-align: left;">
    <LexicalEditor />
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: none;
    margin: 0 auto;
  }

  img {
    margin: 2em;
    max-width: 800px;
  }
</style>
