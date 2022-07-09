<script lang="ts">
	import Card from './Card.svelte';
	import { skills, social, personalInfo } from '../store/data';
	const cardData = [
		{
			id: 0,
			data: personalInfo,
			title: 'Person',
			state: 'active'
		},
		{
			id: 1,
			title: 'Skills',
			data: skills,
			state: 'followed'
		},
		{
			id: 2,
			title: 'SocialLinks',
			data: social,
			state: ''
		},
		{
			id: 3,
			title: 'SocialLinks2',
			data: social,
			state: ''
		}
	];
	const handleCardChange = (id: number) => {
		cardData.forEach((item, i) => {
			if (item.id === id) {
				item.state = 'inactive';
				cardData[(id + 1) % cardData.length].state = 'active';
				cardData[(id + 2) % cardData.length].state = 'followed';
			}
		});
	};
	export let classname = '';
</script>

<div class="cards {classname}">
	{#each cardData as card, index}
		<Card
			data={card.data}
			classname={card.state}
			type={card.title}
			onClick={() => {
				handleCardChange(card.id);
			}}
		/>
	{/each}
</div>

<style type="scss">
	@import '../scss/mixins.scss';
	@import '../scss/variables.scss';
	.cards {
		height: 410px;
		max-width: 580px;
		position: relative;
		top: toRem(-100);
		left: toRem(30);
		width: min(589px, 90%);
	}
	@media (max-width: 1150px) {
		.cards {
			margin: 0 auto;
			left: -1%;
			order: 2;
		}
	}
</style>
