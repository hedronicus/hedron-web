<script>
	import { page } from '$app/stores';

	export let navItems = [];
	export async function load() {
		return {
			props: {
				navItems
			}
		};
	}
</script>

<nav>
	{#each navItems as navItem}
		<a href={navItem.href} class:active={navItem.href === $page.url.pathname}
			>[&nbsp;{navItem.name}&nbsp;]</a
		>
	{/each}
</nav>

<style>
	nav {
		display: flex;
		flex-flow: row wrap;
		justify-content: space-between;
		align-items: center;
		height: auto;
	}

	nav a {
		line-height: 110%;
		font-weight: 400;
		letter-spacing: 0.05em;
		cursor: pointer;
		opacity: 0.6;
		margin-left: 20px;
	}

	nav a:hover {
		opacity: 0.8;
	}

	.active,
	.active:hover {
		opacity: 1;
	}

	@media only screen and (max-width: 768px) {
		nav {
			width: 100vw;
		}

		nav a {
			margin: 0;
		}
	}
</style>
