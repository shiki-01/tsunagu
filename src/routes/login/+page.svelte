<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	import Input from '$lib/components/ui/input/input.svelte';
	import Title from '$lib/Title.svelte';

    let workspaceName = '';
    let email = '';
    let password = '';

    function createAccount() {
        if (typeof window !== 'undefined') window.location.href = '/create';
    }
</script>

<Title class="mb-[50px]">ログイン</Title>

<Card.Card class="relative">
	<Card.Header>
		<Card.Title>ログイン</Card.Title>
	</Card.Header>
	<Card.Content class="flex flex-col gap-4">
        <div class="flex flex-col gap-4">
            <p class="w-[100px]">ワークスペース名</p>
            <Input placeholder="ワークスペース名" bind:value={workspaceName} />
        </div>
		<div class="flex flex-col gap-4">
			<p class="w-[100px]">メールアドレス</p>
			<Input placeholder="メールアドレス" type="email" bind:value={email} />
		</div>
		<div class="flex flex-col gap-4">
			<p class="w-[100px]">パスワード</p>
			<Input placeholder="パスワード" type="password" bind:value={password} />
		</div>
	</Card.Content>
    <Card.Footer>
        <button class="bg-primary
            text-white
            rounded-md
            py-2
            px-4
            w-full
            text-center
            cursor-pointer">ログイン</button>
    </Card.Footer>
</Card.Card>

<div class="text-center mt-5">
    <button on:click={createAccount} class="mt-4"><u>アカウントをお持ちでない場合はこちら</u></button>
</div>