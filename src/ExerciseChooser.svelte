<script>
export let exercise;

function chooseExercise(choice) {
	return () => exercise = choice;
}
</script>

<h1>Maya &times; Math</h1>
<h2>What do you want to practice?</h2>

<ul>
	<li><a href="#f2d" on:click|preventDefault={chooseExercise(['fraction', 'decimal'])}>Fraction to Decimal</a></li>
	<li><a href="#f2p" on:click|preventDefault={chooseExercise(['fraction', 'percent'])}>Fraction to Percent</a></li>
	<li><a href="#d2p" on:click|preventDefault={chooseExercise(['decimal', 'percent'])}>Decimal to Percent</a></li>
	<li><a href="#d2f" on:click|preventDefault={chooseExercise(['decimal', 'fraction'])}>Decimal to Fraction</a></li>
	<li><a href="#p2d" on:click|preventDefault={chooseExercise(['percent', 'decimal'])}>Percent to Decimal</a></li>
	<li><a href="#p2f" on:click|preventDefault={chooseExercise(['percent', 'fraction'])}>Percent to Fraction</a></li>
</ul>

<style>
* {
	box-sizing: border-box;
	text-align: center;
}

ul {
	list-style: none;
	display: flex;
	flex-wrap: wrap;
	justify-content: space-evenly;
	padding: 0;
}
li {
	width: calc(46vw - 8px);
	max-width: 400px;
	height: calc(20vw);
	margin: 2vw;
	box-sizing: border-box;
}
a {
	width: 100%;
	height: 100%;
	padding: 2vw;
	display: flex;
	justify-content: center;
	align-items: center;
	background: #eee;
	border: 2px solid #ddd;
	font-size: 4vw;
}
a:hover {
	text-decoration: none;
	background: #ddd;
	border-color: #aaa;

}
</style>
