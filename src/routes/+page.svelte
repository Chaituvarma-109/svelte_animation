<script>
	import { fade, blur, slide, fly } from 'svelte/transition'
	import { onMount } from 'svelte';

    import {custom} from '../lib/custom'
    import {alert} from '../lib/alert'
    import Nav from '../lib/components/Nav.svelte';
    import Toast from '../lib/components/Toast.svelte';

	onMount({intro:true})

	export let data;
	let isReady = false;
    let isNavopen = false;

    function toggleNav() {
        isNavopen = !isNavopen
    }

    function toggleAlert() {
        alert.set({
            isActive: true,
            text: 'New Alert'
        })
    }
</script>

<!-- fade - 0 to 1 -->
<!-- Blue - opacity and blur -->
<!-- fly - x and y along with opacity -->
<!-- slide - height -->
<!-- scale - start: scale, opacity -->
<!-- Draw - draw svgs -->
<!-- slide - height -->

{#if isNavopen}
    <Nav {toggleNav}/>
{/if}

<main>
	<!-- Mounting and Unmounting animations -->
	<!-- <button on:click={() => isReady = !isReady}>Fade</button> -->
	<button on:click={toggleNav}>Menu</button>
	<button on:click={toggleAlert}>Alert</button>
	{#if isReady}
	<!-- <h1 transition:fade={{delay: 1000, duration: 2000}}>Hello {data.name}!</h1> -->
	<!-- <h1 transition:blur={{ amount: 200}}>Hello {data.name}!</h1> -->
	<!-- <h1 transition:slide>Hello {data.name}!</h1> -->
	<!-- <h1 transition:fly={{ y: 200, x: 100}}>Hello {data.name}!</h1> -->
	<!-- <h1 in:fly={{ y: 200}} out:fade>Hello {data.name}!</h1> -->
	<h1 transition:custom={{delay: 2000}}>Hello {data.name}!</h1>
	{/if}
	
</main>

<Toast />

<!-- <style>
	.hidden {
		opacity: 0;
		transition: 0.3 ease opacity;
	}
</style> -->

