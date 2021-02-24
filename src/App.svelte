<script>
	export let name;
	export let age;

	function incrementAge(){
	    age += 1;
    }
</script>

<style>
	h1 {
		color: #800080;
	}
</style>

<h1>Hello {name}, my age is {age}!</h1>
<button on:click={incrementAge}>Change Age</button>
