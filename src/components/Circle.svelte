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

	export const innerPlanets = [python, svelte, typescript, nodejs, mongodb];
	export const outerPlanets = [nextjs, react, wordpress, git, figma];
</script>

<div class="circle">
	<div class="introImage">
		<img src={profile} alt="profile" />
	</div>
	<div class="ringCircle inner-planets">
		{#each innerPlanets as planet}
			<img class="planetCircle" src={planet} alt="" />
		{/each}
	</div>
	<div class="ringCircle outer-planets">
		{#each outerPlanets as planet}
			<img class="planetCircle" src={planet} alt="" />
		{/each}
	</div>
</div>

<style type="scss">
	@import '../scss/mixins.scss';
	@import '../scss/variables.scss';
	.circle {
		right: -60px;
		width: 920px;
		height: 940px;
		display: grid;
		place-items: baseline end;
		.introImage {
			position: relative;
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
			.planetCircle {
				width: toRem(46);
				height: toRem(46);
				margin: toRem(10);
				border-radius: 50%;
				padding: toRem(3);
				position: relative;
				z-index: 2;
				transform-origin: center;
				border-radius: 50%;
				box-shadow: 0px 0px 10px 1px rgba(43, 43, 43, 0.3);
				animation: planets 10s linear infinite;
				background-color: $white;
				&:nth-child(1) {
					top: 14%;
					left: 0;
					margin-left: -16.5px;
				}
				&:nth-child(2) {
					top: 43%;
					left: 2%;
					margin-left: 0;
				}
				&:nth-child(3) {
					top: 27%;
					left: 43.5%;
					margin-right: 16.5px;
				}
				&:nth-child(4) {
					top: -44%;
					left: 0;
					margin-left: 16.5px;
				}
				&:nth-child(5) {
					top: -46.5%;
					left: -62%;
					margin-left: -16.5px;
				}
			}
		}
		.outer-planets {
			transform: scale(1.8);
			z-index: 1;
			border-width: 1px;
			animation: wheel2 20s linear infinite;
			.planetCircle {
				width: toRem(46);
				height: toRem(46);
				margin: toRem(10);
				border-radius: 50%;
				padding: toRem(3);
				position: relative;
				z-index: 2;
				transform-origin: center;
				border-radius: 50%;
				box-shadow: 0px 0px 10px 1px rgba(43, 43, 43, 0.3);
				animation: planets 20s linear infinite;
				background-color: $white;
				&:nth-child(1) {
					top: 50%;
					left: 0;
					margin-left: -16.5px;
				}
				&:nth-child(2) {
					top: -3%;
					left: 25%;
					margin-left: -26.5px;
				}
				&:nth-child(3) {
					top: 27%;
					left: 76.5%;
					margin-right: 16.5px;
				}
				&:nth-child(4) {
					top: 91%;
					left: 0;
					margin-left: 16.5px;
				}
				&:nth-child(5) {
					top: 70%;
					left: 48%;
					margin-left: -16.5px;
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
</style>
