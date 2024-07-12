<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	import Input from '$lib/components/ui/input/input.svelte';
	import Textarea from '$lib/components/ui/textarea/textarea.svelte';
	import * as Avatar from '$lib/components/ui/avatar';
	import Title from '$lib/Title.svelte';
    import { User, ImageUp } from 'lucide-svelte';

    function imageChange() {
        console.log('imageChange');
    }
</script>

<Title class="mb-[50px]">設定</Title>

<Card.Card class="relative">
	<Card.Header>
		<div class="absolute top-[-40px]">
			<Avatar.Root class="rerative h-[100px] w-[100px] overflow-visible">
				<Avatar.Image src="https://github.com/shadcn.png" alt="@shadcn" class="rounded-full"/>
				<Avatar.Fallback>
                    <User />
                </Avatar.Fallback>
                <div class="absolute bottom-0 right-0 bg-white rounded-full p-2" on:click={imageChange}>
                    <ImageUp class="h-5 w-5" />
                </div>    
			</Avatar.Root>
		</div>
		<Card.Title class="text-end">アカウント</Card.Title>
	</Card.Header>
	<Card.Content class="flex flex-col gap-4">
		<div class="flex flex-col gap-4">
			<p class="w-[100px]">表示名</p>
			<Input placeholder="表示名" />
		</div>
		<div class="flex flex-col gap-4">
			<p class="w-[100px]">ステータス</p>
			<Input placeholder="ステータス" />
		</div>
		<div class="flex flex-col gap-4">
			<p class="w-[100px]">自己紹介</p>
			<Textarea placeholder="自己紹介" class="resize-none" />
		</div>
	</Card.Content>
</Card.Card>
