<script>
    import '../app.css';
    import { LayoutPanelLeft, TreeDeciduous, MessageCircle, Settings } from 'lucide-svelte';
    import { page } from '$app/stores';

    let path;
    $: path = $page.url.pathname.split('/').pop();
</script>

<header class="fixed bottom-0 left-0 w-full h-[80px] bg-primary">
	<nav class="flex justify-around items-center h-full">
		<a href="/home" class="text-white {path === 'home' ? 'active' : ''}">
			<LayoutPanelLeft class="w-8 h-8" />
		</a>
		<a href="/tree" class="text-white {path === 'tree' ? 'active' : ''}">
			<TreeDeciduous class="w-8 h-8" />
		</a>
		<a href="/chat" class="text-white {path === 'chat' ? 'active' : ''}">
			<MessageCircle class="w-8 h-8" />
		</a>
		<a href="/settings" class="text-white {path === 'settings' ? 'active' : ''}">
			<Settings class="w-8 h-8" />
		</a>
	</nav>
</header>
<main class="">
	<slot />
</main>

<style>
	nav {
		z-index: 10;
	}

	nav a {
		@apply p-4 rounded-full shadow-lg;
		transition: all 0.3s;
	}

	nav a.active {
		@apply bg-white text-primary mb-16;
	}

	main {
		width: 100%;
		height: calc(100vh - 80px);
	}
</style>