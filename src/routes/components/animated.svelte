<script>
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';

  export let words = ["Autonome", "Autodidacte", "Solver"];

  let currentWord = "";

  onMount(() => {
    let currentIndex = 0;

    const interval = setInterval(() => {
      currentWord = words[currentIndex];
      currentIndex = (currentIndex + 1) % words.length;
    }, 1200);

    return () => clearInterval(interval);
  });
</script>

<style>
  h2 span {
    font-size: 15px;
    margin-left: 15px;
  }

  .message {
    background-color: yellow;
    color: #333;
    display: block;
    font-weight: 900;
    position: relative;
    padding-left: 0.5rem;
    width: 0;
    text-indent: 0;
    animation: openclose 5s ease-in-out infinite;
  }

  .word {
    font-family: tahoma;
    display: inline-block;
  }

  @keyframes openclose {
    0%, 5%, 33%, 35%, 38%, 66%, 71%, 95%, 98%, 100% {
      top: 0.2rem;
      width: 0;
    }
    15% {
      width: 0;
    }
    30%, 48%, 62%, 86% {
      top: 0.2rem;
      width: 0;
    }
  }
</style>

<h2>
  <div class="message">
    {#each currentWord as letter}
      <span class="word">{letter}</span>
    {/each}
  </div>
</h2>

