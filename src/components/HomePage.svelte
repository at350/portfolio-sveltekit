<script>
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';
    import ContactForm from './ContactForm.svelte';
    import SpaceBackground from './SpaceBackground.svelte';
    import ProfileImage from './ProfileImage.svelte';
  
    let visible = false;
    let titleIndex = 0;
    const titles = ['Journalist', 'Student'];
  
    function enter() {
      visible = true;
    }
  
    function changeTitle() {
    titleIndex = (titleIndex + 1) % titles.length;
  }

    onMount(() => {
    enter();
        const interval = setInterval(changeTitle, 3000);
        return () => clearInterval(interval);
    });
</script>
  
  <style>
    .home-container {
      display: flex;
      min-height: 100vh;
    }
  
    .left, .right {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 2rem;
    }
  
    .left {
      background-color: #222;
      color: #fff;
      flex: 1;
      z-index: 0;
      position: relative;
    }
  
    .right {
      background-color: #fff;
      color: #222;
    }
  
    .profile-image {
        width: auto;
        height: 200px;
        border-radius: 50%;
        margin-top: 1.5rem;
    }
  
    .description {
      max-width: 600px;
      text-align: center;
      margin-top: 1rem;
    }
  
    .contact-container {
      margin-top: 1rem;
    }
  
    h1 {
      font-size: 3rem;
      margin-bottom: 0.5rem;
    }
  
    h2 {
      font-size: 2rem;
      margin-top: 0;
    }

    .title-container {
        position: relative;
        height: 1rem;
        overflow: hidden;
        padding-bottom: 1.5rem;
  }

  .sliding-title {
    position: absolute;
    width: 100%;
    opacity: 0;
    transition: opacity 0.5s, transform 0.5s;
  }

  .sliding-title.active {
    opacity: 1;
    transform: translateY(0);
  }

  .sliding-title.next {
    transform: translateY(100%);
  }
  </style>

<div class="home-container">
    <div class="left">
      <SpaceBackground />
      {#if visible}
        <div in:fade="{{ delay: 250, duration: 1000 }}">
          <h1>Alan Tai</h1>
          <div class="title-container">
            {#each titles as title, index}
              <h2
                class="sliding-title {index === titleIndex ? 'active' : ''} {index === (titleIndex + 1) % titles.length ? 'next' : ''}"
              >
                {title}
              </h2>
            {/each}
          </div>
        </div>
        <ProfileImage />
      {/if}
    </div>
    <div class="right">
      {#if visible}
        <div class="content-container" in:fade="{{ delay: 500, duration: 1000 }}">
          <p class="description">
            A brief description about yourself goes here. You can talk about your skills, interests, and background.
          </p>
          <div class="contact-container">
            <ContactForm />
          </div>
        </div>
      {/if}
    </div>
  </div>