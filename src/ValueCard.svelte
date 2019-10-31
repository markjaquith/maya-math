<script>
export let value;
export let suffix = '';
</script>

<main>
	<div class="value">{value}{suffix}</div>
</main>

<style>
.value {
	font-size: 20vw;
	text-align: center;
	max-width: 80%;
	margin: 0 auto;
	padding: 2vw;
}
</style>