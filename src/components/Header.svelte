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
		margin: 0 auto;
		position: relative;
		top: 30px;
		left: 0;
		right: 0;

		a {
			text-decoration: none;
			color: #000;
            position:  relative;
            z-index: 10;
		}
	}
</style>
