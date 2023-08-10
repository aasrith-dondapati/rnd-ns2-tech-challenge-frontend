
<script>
    import Header from './components/Header.svelte';
    import SideMenu from './components/SideMenu.svelte';
    import MainContent from './components/MainContent.svelte';
    import AddUser from './components/AddUser.svelte';
    import Users from './components/Users.svelte';
    import { Router, Route } from '@sveltejs/kit';
    import Home from './routes/Home.svelte';
  
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
  
  <!-- <div class="app">
    <main class="content">
        <SideMenu />
        <AddUser />
        <Users />
      <MainContent />
    </main>
  </div> -->

  <div class="app">
    <main class="content">
      <Router>
        <Route path="/" component={SideMenu} />
        <!-- <Route path="/" component={AddUser} />
        <Route path="/" component={Users} /> -->
        <Route path="/" component={Home} />
      </Router>
    </main>
  </div>