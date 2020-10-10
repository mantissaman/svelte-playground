<script>
	import ContactCard from "./ContactCard.svelte"

	let name ="Neil Sharma";
	let title = "Chief Fruit Bat";
	let description="He sleeps hanging upside down on a tree branch.";
	let imageUrl="https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSspEcuCTEmrhRcNwf6JsErEWt_lWxQNuxIVpu3rcrSRv_MEAK5-G-AYWFUZXEAlH_WMTwleNf-YMgTjSlI9T7aIbGgWIAw1RqD7Q&usqp=CAU&ec=45695924";
	let age = 7;

	// **** REACTIVITY ****
	//labelled statements (valid JS) - Calculated fields
	//Svelte has hihjacked the syntax
	$: uppercaseName = name.toUpperCase();
	$: console.log(name);
	$: if(name==="Diya"){
		age =10;
	}

	const incrementAge = ()=>{
		age=age+1;
	}

	const changeName =() =>{
		
		name = "Diya";
	}
	const nameInput =(event) =>{
		name = event.target.value;
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello I am {uppercaseName}, my age is {age}!</h1>
<button on:click="{incrementAge}">Change Age</button>
<!-- <button on:click="{changeName}">Change Name</button> -->
<!-- <input type="text" value={name} on:input="{nameInput}"/> -->
<input type="text" bind:value="{name}"/>
<input type="text" bind:value="{title}"/>
<input type="text" bind:value="{imageUrl}"/>
<textarea rows="3" bind:value="{description}"></textarea>

<ContactCard 
	userName="{name}" 
	jobTitle="{title}" 
	{description}
	userImage="{imageUrl}"/>