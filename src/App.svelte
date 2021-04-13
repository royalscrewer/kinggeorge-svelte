
<script>

	import Router from 'svelte-spa-router';
	import Layout from "./Layout.svelte"
	import routes from './routes';
</script>

<Layout>
	<Router {routes} />
</Layout>

<style>

</style>
