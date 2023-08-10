<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
  </script>
  
  <button on:click={() => dispatch('toggleMenu')}>Toggle Menu</button>
  <!-- <h1>My App</h1> -->