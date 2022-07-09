<script>
	import Header from '../components/Header.svelte';
	import Cards from '../components/Cards.svelte';
	import Circle from '../components/Circle.svelte';
</script>

<Header />
<div class="flex">
	<Cards />
	<Circle />
</div>

<style type="scss">
    .flex {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

</style>
