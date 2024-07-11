<script>
    import '../app.css';
    import { LayoutPanelLeft, TreeDeciduous, Settings } from 'lucide-svelte';
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
		<a href="/settings" class="text-white {path === 'settings' ? 'active' : ''}">
			<Settings class="w-8 h-8" />
		</a>
	</nav>
</header>
<slot />

<style>
	nav a {
		@apply p-4 rounded-full shadow-lg;
		transition: all 0.3s;
	}

	nav a.active {
		@apply bg-white text-primary mb-20;
	}
</style>