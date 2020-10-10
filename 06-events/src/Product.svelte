<script>
    import {createEventDispatcher} from 'svelte';

    export let title;
    export let price;
    export let id;
    export let bestseller = false;

    const dispatch = createEventDispatcher();

    function addToCart(){
        dispatch('add-to-cart', {id: id});
    }
    function deleteProduct(){
        dispatch('delete', {id: id});
    }
</script>
<article>
    <h1>{title}</h1>
    <h2>${price}</h2>
    {#if bestseller}
        <h3>BEST SELLER</h3>
    {/if}
    <button on:click ={addToCart}>Add to Cart</button>
    <button on:click ={deleteProduct}>Delete</button>
</article>