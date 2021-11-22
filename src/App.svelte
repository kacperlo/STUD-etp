<script>
	import Tabs from "./Tabs.svelte";
	import Chart from "./Chart.svelte";

	// List of tab items with labels and values.
	let tabItems = [
		{ label: "Zadanie 1", value: 1 },
		{ label: "Zadanie 2", value: 2 },
		{ label: "Zadanie 3", value: 3 }
	];

	// Current active tab
	let currentTab;
</script>

<main>
	<h1>Elektroniczne techniki pomiarowe</h1>

	<Tabs bind:activeTabValue={currentTab} items={tabItems} />

	<code class="language-text"></code>

	{#if 1 === currentTab}
		<h3>Tab 1 content</h3>
		<Chart />
	{/if}

	{#if 2 === currentTab}
		<h3>Tab 2 content</h3>
	{/if}

	{#if 3 === currentTab}
		<h3>Tab 3 content</h3>
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	h3 {
		color: #ff3e00;
		font-size: 2.5em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>