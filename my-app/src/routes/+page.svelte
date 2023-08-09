<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	
	let count = 0
	$: doubled = count * 2

	$: if(count >= 10) {
		alert('카운트가 10을 넘었습니다. ')
		count = 9
	}

	$: {
		console.log( count )
		console.log( doubled )
	}

	function handleClick() {
		// 이벤트 코드
		count += 1
	}
</script>

<button on:click={handleClick}>
  클릭수 { count } {count === 1 ? 'time' : 'times'}
</button>

<p>{count} 두배는 {doubled} <p/>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcome_fallback} alt="Welcome" />
			</picture>
		</span>

		to your new<br />SvelteKit app
	</h1>

	<h2>
		try editing <strong>src/routes/+page.svelte</strong>
	</h2>

	<Counter />
</section>

<style lang="postcss">
	:global(html) {
		background-color: theme(colors.gray.100)
	} 
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
