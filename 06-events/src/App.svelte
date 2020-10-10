<script>
	import Product from './Product.svelte';
	import Modal from './Modal.svelte';

	let products = [
		{id: "p1", title: "A book", price:9.99},
		{id: "p2", title: "Wrench", price:2.29, bestseller:true},
		{id: "p3", title: "Bananas", price:1.50}
	];

	let showModal = false;
	let closable = false;

	function addToCart(event){
		console.log(event.detail);
	}

	function deleteFromCart(event){
		console.log(event.detail);
	}
</script>

{#each products as product (product.id)}
<Product 
	{...product}
	on:add-to-cart="{addToCart}"
	on:delete="{deleteFromCart}"
	/>
{/each}
<button on:click={event => showModal=true}>Show Modal</button>
{#if showModal}
<Modal
	on:cancel="{event => showModal=false}"
	on:close="{event => showModal=false}"
	let:didAgree={closable}>
	<h1 slot="header">Hello</h1>
	<p>It works</p>
	<button slot="footer" on:click={event => showModal=false} disabled={!closable}>confirm</button>
</Modal>
{/if}