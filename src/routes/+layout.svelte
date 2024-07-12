<script>
	import '../app.css';
	import { LayoutPanelLeft, TreeDeciduous, MessageCircle, Settings } from 'lucide-svelte';
	import { page } from '$app/stores';
	import { setupViewTransition } from 'sveltekit-view-transition';

	setupViewTransition();

	let path;
	$: path = $page.url.pathname.split('/').pop();
</script>

<header class="fixed bottom-0 left-0 h-[80px] w-full bg-primary">
	<nav class="flex h-full items-center justify-around">
		<a href="/home" class="text-white {path === 'home' ? 'active' : ''}">
			<LayoutPanelLeft class="h-8 w-8" />
		</a>
		<a href="/tree" class="text-white {path === 'tree' ? 'active' : ''}">
			<TreeDeciduous class="h-8 w-8" />
		</a>
		<a href="/chat" class="text-white {path === 'chat' ? 'active' : ''}">
			<MessageCircle class="h-8 w-8" />
		</a>
		<a href="/settings" class="text-white {path === 'settings' ? 'active' : ''}">
			<Settings class="h-8 w-8" />
		</a>
	</nav>
</header>
<main class="p-5">
	<slot />
</main>

<style>
	nav {
		z-index: 10;
	}

	nav a {
		@apply rounded-full p-4 shadow-lg;
		transition: all 0.3s;
	}

	nav a.active {
		@apply mb-16 bg-white text-primary;
	}

	main {
		width: 100%;
		height: calc(100vh - 80px);
	}
</style>
