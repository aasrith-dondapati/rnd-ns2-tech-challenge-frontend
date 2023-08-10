<script lang="ts">
    import SideMenu from './SideMenu.svelte';
import Users from './lib/Users.svelte';
let isMenuOpen = false;
</script>

<style>

:root {
    --grid-gap: 5px;
    --square-aspect-ratio: 1; /* Change this if you want a different aspect ratio */
  }

  .full-page-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 100vw;
    width: 65vw;
    flex-direction: column;
  }

  .responsive-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: var(--grid-gap);
    padding: var(--grid-gap);
    width: 100vw;
    height: 100vw;
    display: flex;
    max-width: 100%;
    /* justify-items: center; */
    justify-content: space-evenly;
  }

  .square {
    background-color: lightblue;
    width: 100%;
    /* height: 50vh; */
    /* padding-bottom: 50%; Create a square aspect ratio */
  }

  .sub-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    gap: 5px;
    width: 100vw;
    height: 100%;
    /* justify-items: center; */
    justify-content: space-between;

  }

  /* .sub-square {
    background-color: lightblue;
    width: 50%;
    padding-bottom: 100%; 
  } */

  /* Add media query for smaller screens */
  @media (max-width: 768px) {
    .responsive-grid {
      grid-template-columns: repeat(auto-fit, minmax(200px, 2fr));
    }
  }
</style>

<div class="full-page-container">
    <aside class="sidebar {isMenuOpen ? '' : 'collapsed'}">
   <SideMenu />
   </aside>
    <div class="responsive-grid">
        <div class="sub-grid">
        <!-- <div class="square"> -->
            <div class="square"></div>
            <div class="square"></div>
            <!-- <div class="sub-square"></div>
            <div class="sub-square"></div> -->
        <!-- </div> -->
        </div>
        <div class="sub-grid">
            <div class="square"></div>
            <div class="square"></div>
        </div>
    </div>
</div>