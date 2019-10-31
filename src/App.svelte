<script>
import ExerciseChooser from './ExerciseChooser.svelte';
import FlashCards from './FlashCards.svelte';
let exercise;
</script>

{#if exercise}
	<a href="#back" on:click|preventDefault|stopPropagation={() => exercise = false}>&larr; Menu</a>
	<FlashCards {exercise} />
{:else}
	<ExerciseChooser bind:exercise={exercise} />
{/if}
