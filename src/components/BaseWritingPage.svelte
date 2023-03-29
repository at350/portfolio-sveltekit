<script>
    import Menu from "../components/Menu.svelte";
    export let coverImage = "";
    export let articles = [];
  </script>
  
  <Menu />
  <section>
    <img src="{coverImage}" alt="Cover" class="cover-image" />
    <div class="articles-grid">
      {#each articles as article}
        <div class="article">
          <h2>{article.title}</h2>
          <p>{article.description}</p>
        </div>
      {/each}
    </div>
  </section>
  
  <style>
    .cover-image {
      width: 100%;
      height: auto;
    }
  
    .articles-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 1rem;
    }
  
    .article {
      background-color: #f0f0f0;
      padding: 1rem;
      border-radius: 5px;
    }
  </style>
  