
<script>
    import Header from './Header.svelte';
    import SideMenu from './SideMenu.svelte';
    import MainContent from './MainContent.svelte';
    import AddUser from './AddUser.svelte';
    import Users from './Users.svelte';
  
    let isMenuOpen = false;
  </script>
  
  <style>
    .app {
      /* display: flex;
      justify-content: space-between; */
      /* flex-direction: column; */
      width: 100vw;
      max-width: 350px;
      
    }
  
    .sidebar {
      width: 200px; /* Fixed width for simplicity */
      transition: transform 0.3s;
      transform: translateX(0);
    }
  
    .sidebar.collapsed {
      transform: translateX(-100%);
    }
  
    .content {
      flex-grow: 1;
    }
  </style>
  
  <div class="app">
    <main class="content">
        <SideMenu />
        <AddUser />
        <Users />
      <MainContent />
    </main>
  </div>