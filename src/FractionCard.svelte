<script>
export let numerator;
export let denominator;
</script>

<main>
	<div class="numerator">{numerator}</div>
	{#if denominator && 1 !== denominator}
		<div class="denominator">{denominator}</div>
	{/if}
</main>

<style>
.numerator, .denominator {
	font-size: 20vh;
	text-align: center;
	width: 25vh;
	margin: 0 auto;
	padding: 2vh;
}

.denominator {
	border-top: 1vw solid #333;
}
</style>