<script lang="ts">
	import figma from '../assets/figma.svg';
	import git from '../assets/git.svg';
	import mongodb from '../assets/mongodb.svg';
	import nextjs from '../assets/nextjs.svg';
	import nodejs from '../assets/nodejs.svg';
	import python from '../assets/python.svg';
	import svelte from '../assets/svelte.svg';
	import typescript from '../assets/typescript.svg';
	import react from '../assets/react.svg';
	import wordpress from '../assets/wordpress.svg';
	import profile from '../assets/profile.jpg';

	const inner = [
		{
			planet: python,
			name: 'Python'
		},
		{
			planet: svelte,
			name: 'Svelte'
		},
		{
			planet: typescript,
			name: 'TypeScript'
		},
		{
			planet: nodejs,
			name: 'Node.js'
		},
		{
			planet: mongodb,
			name: 'MongoDB'
		}
	];

	const outer = [
		{
			planet: nextjs,
			name: 'Next.js'
		},
		{
			planet: react,
			name: 'React'
		},
		{
			planet: wordpress,
			name: 'WordPress'
		},
		{
			planet: git,
			name: 'Git'
		},
		{
			planet: figma,
			name: 'Figma'
		}
	];
</script>

<div class="circle">
	<div class="introImage">
		<img src={profile} alt="profile" />
	</div>
	<div class="ringCircle inner-planets">
		{#each inner as planet}
			<div class="planetCircle">
				<img src={planet.planet} alt="" />
				<span class="tooltip">{planet.name}</span>
			</div>
		{/each}
	</div>
	<div class="ringCircle outer-planets">
		{#each outer as planet}
			<div class="planetCircle">
				<img src={planet.planet} alt="" />
				<span class="tooltip">{planet.name}</span>
			</div>
		{/each}
	</div>
</div>

<style type="scss">
	@import '../scss/mixins.scss';
	@import '../scss/variables.scss';
	.circle {
		right: -60px;
		width: 661px;
		height: 900px;
		display: grid;
		place-items: baseline end;
		position: relative;
		.introImage {
			position: absolute;
			z-index: 3;
			max-width: 100%;
			max-width: 500px;
			height: auto;
			border: 6px solid #e4e4e4;
			border-radius: 50%;
			filter: drop-shadow(0px 0px 20px rgba(0, 0, 0, 0.4));
			transform-origin: center;
			animation: twiddle 5s linear infinite alternate;
			img {
				width: 100%;
				height: 100%;
				border-radius: 50%;
			}
		}

		@keyframes twiddle {
			from {
				transform: rotateZ(-2deg);
			}

			to {
				transform: rotateZ(2deg);
			}
		}
		.ringCircle {
			position: absolute;
			width: 500px;
			height: 500px;
			transform-origin: center;
			border: 2px solid rgba(19, 20, 33, 0.5);
			border-radius: 50%;
		}
		.inner-planets {
			transform: scale(1.3);
			z-index: 2;
			display: flex;
			justify-content: space-between;
			align-items: center;
			animation: wheel 10s linear infinite;
			img {
				width: 100%;
				height: 100%;
				border-radius: 50%;
			}
			&:hover {
				animation-play-state: paused;
				.planetCircle {
					animation-play-state: paused;
				}
			}
			.planetCircle {
				width: toRem(46);
				height: toRem(46);
				margin: toRem(10);
				border-radius: 50%;
				padding: toRem(3);
				position: absolute;
				z-index: 2;
				transform-origin: center;
				border-radius: 50%;
				box-shadow: 0px 0px 10px 1px rgba(43, 43, 43, 0.3);
				animation: planets 10s linear infinite;
				background-color: $white;
				.tooltip {
					position: absolute;
					top: -30px;
					left: 50%;
					transform: translateX(-50%);
					font-size: 11px;
					font-weight: 300;
					background: rgba(0, 0, 0, 0.833);
					color: $white;
					padding: 2px 5px;
					border-radius: 5px;
					opacity: 0;
					transition: $transition;
					z-index: 8;
				}
				&:hover .tooltip {
					opacity: 1;
				}
				&:nth-child(1) {
					top: 29%;
					left: -5%;
				}
				&:nth-child(2) {
					top: 83%;
					left: 14%;
				}
				&:nth-child(3) {
					top: -6.5%;
					left: 43.5%;
				}
				&:nth-child(4) {
					top: 17%;
					left: 86%;
				}
				&:nth-child(5) {
					top: 75.5%;
					right: 5%;
				}
			}
		}
		.outer-planets {
			transform: scale(1.8);
			z-index: 1;
			border-width: 1px;
			animation: wheel2 20s linear infinite;
			&:hover {
				animation-play-state: paused;
				.planetCircle {
					animation-play-state: paused;
				}
			}
			.planetCircle {
				img {
					width: 100%;
					height: 100%;
					border-radius: 50%;
				}
				.tooltip {
					position: absolute;
					top: -30px;
					left: 50%;
					transform: translateX(-50%);
					font-size: 11px;
					font-weight: 300;
					background: rgba(0, 0, 0, 0.833);
					color: $white;
					padding: 2px 5px;
					border-radius: 5px;
					opacity: 0;
					transition: $transition;
					z-index: 8;
				}
				&:hover .tooltip {
					opacity: 1;
				}
				width: toRem(46);
				height: toRem(46);
				margin: toRem(10);
				border-radius: 50%;
				padding: toRem(3);
				position: absolute;
				z-index: 2;
				transform-origin: center;
				border-radius: 50%;
				box-shadow: 0px 0px 10px 1px rgba(43, 43, 43, 0.3);
				animation: planets 20s linear infinite;
				background-color: $white;
				&:nth-child(1) {
					top: 50%;
					left: -6%;
				}
				&:nth-child(2) {
					top: 5%;
					left: 11%;
				}
				&:nth-child(3) {
					top: 4%;
					left: 74%;
				}
				&:nth-child(4) {
					top: 57%;
					left: 91.5%;
				}
				&:nth-child(5) {
					bottom: -6.5%;
					left: 47%;
				}
			}
		}
	}
	@keyframes wheel {
		from {
			transform: scale(1.3) rotateZ(0);
		}

		to {
			transform: scale(1.3) rotateZ(360deg);
		}
	}
	@keyframes wheel2 {
		from {
			transform: scale(1.8) rotateZ(0);
		}

		to {
			transform: scale(1.8) rotateZ(360deg);
		}
	}
	@keyframes planets {
		from {
			transform: rotateZ(0deg);
		}

		to {
			transform: rotateZ(-360deg);
		}
	}
	@media (max-width: 552px) {
		.circle {
			pointer-events: none;
		}
	}
</style>
