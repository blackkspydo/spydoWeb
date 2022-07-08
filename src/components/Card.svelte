<script lang="ts">
	import { each } from 'svelte/internal';
	import type { data as dataType } from '../store/data.d';
	export let data: dataType[] = [];
	export let classname = '';
	export let type = 'foo';
	export let onClick = () => {
		console.log('clicked');
	};
	export let hovered = false;
	export const isArray = (value: any): value is any[] => Array.isArray(value);
</script>

<div class="card {classname}" on:click={() => !hovered && onClick()}>
	<div class="header">
		<span class="buttons" />
		<span class="buttons" />
		<span class="buttons" />
	</div>
	<div class="content">
		<span class="pink">const </span><span class="yellow">{type}</span> <span class="blue"> = </span>
		{`{`}
		<ul>
			{#if data.length >= 1}
				{#each data as item}
					<li>
						{#if item.url}
							<span class="blue">{item.name}</span> :
							<a
								on:mouseover={() => (hovered = true)}
								on:mouseout={() => (hovered = false)}
								on:focus={() => (hovered = true)}
								on:blur={() => (hovered = false)}
								target="_blank"
								href={item.url}
							>
								<span class="green">"{item.value}"</span></a
							>,
						{:else}
							<span class="blue">{item.name}</span> :
							<span class="green">
								{#if isArray(item.value)}
									<div class="flex">
										{#each item.value as value, index}
											<span class="green">
												"{value}"{#if index < item.value.length - 1}
													<span class="white">,</span>
												{/if}
											</span>
											<br />
										{/each}
									</div>
								{:else}
									<span class="green">
										"{item.value}"
									</span>
								{/if}
							</span>,
						{/if}
					</li>
				{/each}
			{:else}
				<li><span class="gray">//data not available</span></li>
			{/if}
		</ul>
		{`}`}
	</div>
</div>

<style type="scss">
	@import '../scss/mixins.scss';
	@import '../scss/variables.scss';
	.flex {
		display: inline-flex;
		flex-direction: column;
		position: relative;
		margin-left: toRem(10);
		&::before {
			content: '[';
			position: absolute;
			left: toRem(-10);
		}
		&::after {
			content: ']';
			position: absolute;
			bottom: 0;
			right: toRem(-10);
		}
	}
	.card {
		// width: toRem(589);
		width: clamp(toRem(589), 90%, toRem(400));
		max-width: toRem(589);
		min-height: toRem(300);
		background: #2a2a32;
		border-radius: toRem(10);
		padding: toRem(15);
		font-family: 'Roboto Mono', monospace;
		font-size: toRem(16);
		font-weight: 300;
		position: absolute;
		transform-origin: bottom right;
		transform: rotateZ(6deg);
		display: flex;
		flex-direction: column;
		pointer-events: none;
		box-shadow: 4px 4px 20px 5px rgba(0, 0, 0, 0.3);
		transition: 0.5s all ease-in-out;
		opacity: 0;
		cursor: pointer;
		.header {
			width: 100%;
			display: flex;
			justify-content: flex-start;
			align-items: center;
			column-gap: toRem(10);
			margin-bottom: toRem(20);
			.buttons {
				width: 12px;
				height: 12px;
				border-radius: 50%;
				display: flex;
				align-items: center;
				font-size: 1.2em;
				color: $black;
				transition: $transition;
				&:hover {
					color: $white;
				}
			}
			.buttons:nth-child(1) {
				background: #ed4040;
			}
			.buttons:nth-child(2) {
				background: #ecb62b;
			}
			.buttons:nth-child(3) {
				background: #24e05a;
			}
		}
		.content {
			&:focus {
				outline: none;
			}
			color: white;
			ul {
				li {
					list-style: none;
					a {
						text-decoration: none;
						font-family: 'Roboto Mono', monospace;
						font-size: toRem(16);
						font-weight: 300;
						pointer-events: auto;
						&:hover {
							span {
								color: $blue2 !important;
							}
						}
					}
				}
			}
			.pink {
				color: $pink;
			}
			.yellow {
				color: $yellow;
			}
			.blue {
				color: $blue;
			}
			.green {
				color: $green;
			}
			.gray {
				color: $gray;
			}
			.white {
				color: $white;
			}
		}
	}
	.active {
		transform-origin: right bottom;
		opacity: 1;
		transform: rotateZ(0deg);
		pointer-events: auto;
	}
	.followed {
		position: absolute;
		top: 0;
		z-index: -1;
		opacity: 0.5;
		height: 200px !important;
		transform: rotate(5deg);
		transform-origin: right bottom;
	}
	.inactive {
		animation: falldown 1s ease-in-out;
		transform-origin: right bottom;
	}
	@keyframes falldown {
		0% {
			opacity: 1;
			transform: rotateZ(0);
		}

		70% {
			opacity: 0.5;
		}

		90% {
			opacity: 0;
			transform: rotateZ(-90deg) scale(0.9);
		}

		100% {
			opacity: 0;
			transform: rotateZ(-90deg) scale(0);
		}
	}
</style>
