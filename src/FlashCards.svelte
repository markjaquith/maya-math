<script>
import numbers from './numbers';
import FractionCard from './FractionCard.svelte';
import ValueCard from './ValueCard.svelte';
export let exercise;
let showingAnswer = false;
$: if (exercise) { showingAnswer = false; }
$: problem = pickRandom(numbers);
$: [from, to] = exercise;
$: [numerator, denominator] = problem;
$: typeToShow = showingAnswer ? to : from;

function next() {
	console.log('next');
	if (showingAnswer) {
		newProblem();
	}
	showingAnswer = !showingAnswer;
}

function newProblem() {
	const oldProblem = problem;
	while(oldProblem === problem) {
		problem = pickRandom(numbers);
	}
}

function round(num, power = 4) {
	const multiplier = Math.pow(10, power);
	return Math.round((num + Number.EPSILON) * multiplier ) / multiplier;
}

function fraction([numerator, denominator]) {
	return numerator + (denominator ? ` / ${denominator}` : '');
}

function decimal([numerator, denominator]) {
	return round(numerator /(denominator || 1));
}

function percent([numerator, denominator]) {
	return round(numerator /(denominator || 1) * 100 + Number.EPSILON, 2);
}

function pickRandom(items) {
	return items[Math.floor(Math.random()*items.length)];
}
</script>

<main on:click={next}>
{#if showingAnswer}
	<h1>The Answer</h1>
	<h2>Tap anywhere for next card</h2>
{:else}
	<h1>Convert the&nbsp;{from} to&nbsp;a&nbsp;{to}</h1>
	<h2>Tap anywhere to see answer</h2>
{/if}

{#if typeToShow === 'fraction'}
	<FractionCard {numerator} {denominator} />
{:else if typeToShow === 'percent'}
	<ValueCard value={percent(problem)} suffix="%" />
{:else if typeToShow === 'decimal'}
	<ValueCard value={decimal(problem)} />
{/if}
</main>

<style>
* {
	text-align: center;
}

main {
	width: 100%;
	height: 100%;
}

h2 {
	background: #ddd;
	color:#999;
	margin: 0 1em;
	padding: 0.5em;
}
</style>