<script>
	import { navigation } from '../store/data';
	let isOpen = false;
	const navHandler = () => {
		isOpen = !isOpen;
	};
</script>

<button class="toggle" on:click={navHandler}>
	<span />
	<span />
</button>
{#if isOpen}
	<nav>
		<button on:click={navHandler} class="close">
			<span />
			<span /></button
		>
		<ul>
			{#each navigation as item}
				<li>
					<a href={item.url}>{item.name}</a>
				</li>
			{/each}
		</ul>
	</nav>
{/if}

<style type="scss">
	@import '../scss/mixins.scss';
	@import '../scss/variables.scss';
	.toggle {
		background: none;
		border: none;
		z-index: 10;
		span {
			display: block;
			background: black;
			&:first-child {
				width: 55px;
				margin-bottom: 10px;
			}
			height: 6px;
			border-radius: 15px;
			width: 40px;
		}
	}
	.close {
		position: absolute;
		top: 30px;
		right: 10px;
		background: none;
		border: none;
		z-index: 10;
		span {
			display: block;
			background: black;
			&:first-child {
				width: 45px;
				transform: rotate(45deg) translate(-3px, -6px);
				transform-origin: center;
			}
			&:nth-child(2) {
				transform-origin: center;
				transform: rotate(-45deg) translate(9px, -9px);
			}
			height: 6px;
			border-radius: 15px;
			width: 45px;
		}
	}
	nav {
		position: fixed;
		top: 0;
		bottom: 0;
		height: 100vh;
		right: 0;
		background-color: $white;
		z-index: 10;
		width: min(350px, 50%);
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: flex-start;
		transition: all 0.5s;
	}
	ul {
		margin-top: 50px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		position: relative;
		z-index: 5;
		li {
			list-style: none;
			margin: toRem(10) 0;
			margin-left: -20%;
			a {
				text-decoration: none;
				color: $black;
				font-size: 1.2em;
				padding: toRem(10) toRem(5);

				transition: $transition;
				position: relative;
			}
		}
	}
	@media (min-width: 552px) {
		nav {
			display: none;
		}
		.toggle {
			display: none;
		}
	}
</style>
