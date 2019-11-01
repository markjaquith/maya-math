<script>
import { scale } from 'svelte/transition';
export let showingAnswer = false, from, to;

const scaleOut = {
	duration: 200,
};

const scaleIn = {
	...scaleOut,
	delay: 200,
}
</script>
	
<div in:scale={scaleIn} out:scale={scaleOut}>
	{#if showingAnswer}
		<h1>The Answer</h1>
		<h2>Tap anywhere for next card</h2>
	{:else}
		<h1>Convert the&nbsp;{from} to&nbsp;a&nbsp;{to}</h1>
		<h2>Tap anywhere to see answer</h2>
	{/if}
	<slot />
</div>

<style>
* {
	text-align: center;
}

div {
	background: white;
}

h2 {
	background: #ddd;
	color:#999;
	margin: 0 1em;
	padding: 0.5em;
}
</style>