<script>
	import Header from '../components/Header.svelte';
	import Cards from '../components/Cards.svelte';
	import Circle from '../components/Circle.svelte';
	import Footer from '../components/Footer.svelte';
</script>

<Header />
<main class="flex">
	<Cards />
	<Circle />
</main>
<Footer />

<style type="scss">
	.flex {
		display: flex;
		justify-content: space-between;
		align-items: center;
		max-width: 1700px;
		margin-left: auto;
		padding-top: 3.5rem;
        overflow-x: clip;
	}
	@media (max-width: 1150px) {
		.flex {
			flex-direction: column;
			&:first-child {
				order: 2;
			}
		}
	}
</style>
