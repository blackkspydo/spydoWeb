<script lang="ts">
	const year = new Date().getFullYear();
	//@ts-ignore
	import Icon from '@iconify/svelte';

	const social = [
		{
			tooltip: 'Telegram',
			icon: 'bxl:telegram',
			url: 'https://t.me/blackkspydo'
		},
		{
			tooltip: 'Mail',
			icon: 'cib:gmail',
			url: 'mailto:work@blackkspydo.com'
		},
		{
			tooltip: 'Twitter',
			icon: 'bxl:linkedin-square',
			url: 'https://twitter.com/blackkspydo'
		},
		{
			tooltip: 'Github',
			icon: 'bxl:github',
			url: 'https://github.com/blackkspydo'
		},
		{
			tooltip: 'Twitter',
			icon: 'bxl:twitter',
			url: 'https://www.linkedin.com/in/blackkspydo/'
		}
	];
</script>

<footer>
	<div class="copyright">
		<p>Copyright &copy {year}; Blackkspydo. All rights reserved</p>
	</div>
	<div class="social">
		<span>Connect: </span>
		{#each social as social}
			<a href={social.url} target="_blank">
				<Icon icon={social.icon} />
				<span class="tooltip">{social.tooltip}</span>
			</a>
		{/each}
	</div>
</footer>

<style type="scss">
	@import '../scss/mixins.scss';
	@import '../scss/variables.scss';

	footer {
		position: absolute;
		right: 0;
		left: 0;
		background: #000;
		color: #fff;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1px 30px;
		.social {
			display: flex;
			justify-content: center;
			align-items: center;
			column-gap: 15px;

			a {
				color: #fff;
				text-decoration: none;
				font-size: 23px;
				position: relative;
				&:hover {
					.tooltip {
						opacity: 1;
					}
				}
				.tooltip {
					position: absolute;
					top: -30px;
					left: 0;
					font-size: 12px;
					background: $black;
					color: $white;
					padding: 5px 10px;
					border-radius: 5px;
					opacity: 0;
					transition: $transition;
				}
			}
		}
	}
	@media (max-width: 670px) {
		footer {
			padding: 33px 30px;
			flex-direction: column;
			.copyright {
				order: 1;
				text-align: center;
			}
		}
	}
</style>
