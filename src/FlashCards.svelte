<script>
import numbers from './numbers';
import FractionCard from './FractionCard.svelte';
import ValueCard from './ValueCard.svelte';
import Card from './Card.svelte';
export let exercise;
let showingAnswer = false;
$: if (exercise) { showingAnswer = false; }
$: problem = pickRandom(numbers);
$: [from, to] = exercise;
$: [numerator, denominator] = problem;
$: typeToShow = showingAnswer ? to : from;

function next() {
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

{#if typeToShow === 'fraction'}
	<Card {showingAnswer} {from} {to}>
		<FractionCard {numerator} {denominator} />
	</Card>
{:else if typeToShow === 'percent'}
	<Card {showingAnswer} {from} {to}>
		<ValueCard value={percent(problem)} suffix="%" />
	</Card>
{:else if typeToShow === 'decimal'}
	<Card {showingAnswer} {from} {to}>
		<ValueCard value={decimal(problem)} />
	</Card>
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
</style>