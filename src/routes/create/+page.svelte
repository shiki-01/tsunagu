<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	import Input from '$lib/components/ui/input/input.svelte';
	import Title from '$lib/Title.svelte';
    import Icon from '@iconify/svelte';

    let workspaceName = '';
    let email = '';
    let password = '';
    let passwordConfirm = '';

    function logIn() {
        if (typeof window !== 'undefined') window.location.href = '/login';
    }

    function createAccount() {
        if (workspaceName === '' || email === '' || password === '') {
            alert('全ての項目を入力してください');
            return;
        }
        if (password !== passwordConfirm) {
            alert('パスワードが一致しません');
            return;
        }
        if (password.length < 6) {
            alert('パスワードは6文字以上である必要があります');
            return;
        }
        if (typeof window !== 'undefined') window.location.href = '/home';
    }
</script>

<Title class="mb-[50px]">新規アカウント</Title>

<Card.Card class="relative">
	<Card.Header>
		<Card.Title>新規アカウント</Card.Title>
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
        <div class="flex flex-col gap-4">
            <p class="w-[100px]">パスワード確認</p>
            <Input placeholder="パスワード確認" type="password" bind:value={passwordConfirm} />
        </div>
	</Card.Content>
    <Card.Footer class="flex flex-col gap-4">
        <button class="bg-primary
            text-primary-foreground
            rounded-md
            py-2
            px-4
            w-full
            text-center
            cursor-pointer"
            on:click={createAccount}
            >作成</button>
        <button class="bg-primary-foreground
            text-primary
            border
            border-primary
            rounded-md
            py-2
            px-4
            w-full
            text-center
            cursor-pointer"
            on:click={logIn}
            >
            <Icon icon="logos:google-icon" class="h-5 w-5 inline-block mr-2" />
            Google アカウントで作成</button>
    </Card.Footer>
</Card.Card>

<div class="text-center mt-5">
    <button on:click={logIn} class="mt-4"><u>アカウントをお持ちの場合はこちら</u></button>
</div>