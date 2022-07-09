<script>
	import Navigation from './Navigation.svelte';
	import MobNavigation from './MobileNavigation.svelte';
</script>

<header class="flex-container">
	<a href="/"><h2>Blackk Spydo</h2></a>
	<Navigation />
	<MobNavigation />
</header>

<style type="scss">
	.flex-container {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		width: 90%;

		position: relative;
		top: 30px;

		right: 0;

		a {
			text-decoration: none;
			color: #000;
			position: relative;
			z-index: 10;
		}
	}
	@media (max-width: 552px) {
		.flex-container {
			top: 20px;
			margin: 0 auto;
			left: 0;
		}
	}
	@media (min-width: 552px) {
		.flex-container {
			max-width: min(1000px,calc(100% - 700px));
			margin-right: auto;
			justify-content: space-between;
			left: 5%;
		}
	}
</style>
