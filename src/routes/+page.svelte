<script>
	import profil from '$lib/images/profil.jpg';
	import { onMount } from 'svelte';

	let originalTitle = "Développeur Autonome";
	let blurredTitle = "Oh déjà parti ?";
	let isBlurred = false;

	// Fonction pour mettre à jour le titre de l'onglet
	function updatePageTitle() {
		document.title = isBlurred ? blurredTitle : originalTitle;
	}

  // Détecter la perte de focus de la page
  onMount(() => {
    window.addEventListener('blur', () => {
      isBlurred = true;
      updatePageTitle();
    });

    window.addEventListener('focus', () => {
      isBlurred = false;
      updatePageTitle();
    });

    // Nettoyer les écouteurs d'événements lorsque le composant est détruit
    return () => {
      window.removeEventListener('blur', updatePageTitle);
      window.removeEventListener('focus', updatePageTitle);
    };
  });

</script>

<svelte:head>
	<title>Développeur autonome</title>
	<meta name="description" content="Jérôme Albrecht CV" />
</svelte:head>

<section>
	<h1 class="wave-text">
		I'm Full Stack Developer
	</h1>

	<span class="welcome">
		<picture>
			<source srcset={profil} type="image/jpeg" />
			<img src={profil} alt="Welcome" />
		</picture>
	</span>

	<h2>
		try ME 
	</h2>

</section>

<style>

	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	picture {
		display: flex;
		justify-content: center;
	}

	.welcome {
		display: flex;
		width: 100%;
		max-width: 800px;
	}

	.welcome img {
		width: 40%;
		height: auto;
		border-radius: 50%;
	}

	h2 {
		font-size: 1rem;
		color: var(--cadet-gray);
	}

	@keyframes wave {
    0% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-5px);
    }
    100% {
      transform: translateY(0);
    }
  }

  .wave-text:hover {
    animation: wave 0.4s ease-in-out infinite;
  }
</style>
