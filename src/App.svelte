<script>
    import ContactCard from "./ContactCard.svelte";

	export let name;
	export let age;
	let title = "";
	let description = "";
	let image;

	$: uppercaseName = name.toUpperCase();

	function incrementAge(){
	    age += 1;
    }

    function changeName(){
	    name = 'That Guy';
    }

    function nameInput(event){
	    const enteredValue = event.target.value;
	    name = enteredValue;
    }
</script>

<style>
	h1 {
		color: #800080;
	}
</style>

<h1>Hello {uppercaseName}, my age is {age}!</h1>
<button on:click={incrementAge}>Change Age</button>
<!--<button on:click={changeName}>Change Name</button>-->
<!--<input type="text" value={name} on:input={nameInput}>-->
<input type="text" bind:value={name}/>
<input type="text" bind:value={title}/>
<input type="text" bind:value={image}/>
<textarea rows="3" bind:value={description}></textarea>

<!--Notice {description} is not paired. This is an allowed shortcut thru Svelte because the local variable and associated-->
<!--variable have the same name.-->
<ContactCard
        userName="{name}"
        jobTitle="{title}"
        {description}
        userImage="{image}"
/>