<script>
    import Nav from '../components/Nav.svelte';
    import ComponentWithStore from '../components/ComponentWithStore.svelte';
    import {mystore, setSession} from '../myStore.js'

	export let segment;

    let session = setSession("A_SESSION"); // here comes the session

    const unsubscribeMyStore = mystore.subscribe(value => {
        session = session;
    });
</script>

<style>
	main {
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}
</style>

<Nav {segment}/>

<ComponentWithStore bind:session={$mystore}/>

<main>
	<slot></slot>
</main>
