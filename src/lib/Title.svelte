<script lang="ts">
    import type { HTMLAttributes } from "svelte/elements";
	import { cn } from "$lib/utils.js";

	type $$Props = HTMLAttributes<HTMLDivElement>;

    let className: $$Props["class"] = undefined;
    export { className as class };
</script>

<div class={cn("flex justify-between items-center text-lg", className)}>
    <h1><strong><slot /></strong></h1>
</div>