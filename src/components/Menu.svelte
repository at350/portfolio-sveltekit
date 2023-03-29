<script>
    import { fade } from 'svelte/transition';

    let showWritingDropdown = false;

    function toggleWritingDropdown() {
      showWritingDropdown = !showWritingDropdown;
    }

    function navigateTo(path) {
      window.location.href = path;
    }
  </script>  

  <div class="menu">
    <div class="name">Alan Tai</div>
    <nav class="nav-items">
      <a href="/" class="nav-link">Home</a>
      <div class="nav-item" on:mouseenter="{toggleWritingDropdown}" on:mouseleave="{toggleWritingDropdown}">
        <a href="/writing" class="nav-link">Writing</a>
        {#if showWritingDropdown}
          <div class="dropdown" transition:fade="{{ duration: 200 }}">
            <a href="/features" class="nav-link dropdown-item">Features</a>
            <a href="/opinion" class="nav-link dropdown-item">Opinion</a>
            <a href="/sports" class="nav-link dropdown-item">Sports</a>
            <a href="/news" class="nav-link dropdown-item">News</a>
            <a href="/ae" class="nav-link dropdown-item">A&E</a>
            <a href="/misc" class="nav-link dropdown-item">Misc</a>
          </div>
        {/if}
      </div>
      <a href="/photography" class="nav-link">Photography</a>
      <a href="/design" class="nav-link">Design</a>
      <a href="/multimedia" class="nav-link">Multimedia</a>
    </nav>
  </div>
  
  <style>
    .menu {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background-color: #f0f0f0;
      padding: 1rem;
      font-family: 'Roboto', sans-serif;
    }
  
    .name {
      font-size: 2rem;
      text-transform: uppercase;
      flex: 1;
      text-align: center;
      font-family: 'Inter', sans-serif;
      color: #333;
    }
  
    .nav-items {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
  
    .nav-item {
      position: relative;
    }
  
    .nav-link {
      text-decoration: none;
      color: #333;
      padding: 0.5rem 1rem;
      position: relative;
      transition: color 0.3s;
    }
  
    .nav-link::before {
      content: "";
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      height: 2px;
      background-color: #333;
      transform: scaleX(0);
      transform-origin: left;
      transition: transform 0.3s;
    }
  
    .nav-link:hover {
      color: #555;
    }
  
    .nav-link:hover::before {
      transform: scaleX(1);
    }
  
    .dropdown {
      position: absolute;
      top: 100%;
      left: 0;
      min-width: 150px;
      background-color: #f0f0f0;
      padding: 1rem;
      box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
      z-index: 100;
    }
  
    .dropdown-item {
      display: block;
      padding: 0.25rem 0;
      transition: color 0.3s;
    }
  
    .dropdown-item:hover {
      color: #555;
    }
  </style>