<script>
	import Tabs from "./Tabs.svelte";

	// List of tab items with labels and values.
	let tabItems = [
		{ label: "Zadanie 1", value: 1 },
		{ label: "Zadanie 2", value: 2 },
		{ label: "Zadanie 3", value: 3 }
	];

	// Current active tab
	let currentTab;
</script>

<Tabs bind:activeTabValue={currentTab} items={tabItems} />

<code class="language-text"></code>

{#if 1 === currentTab}
	<h3>Tab 1 content</h3>
{/if}

{#if 2 === currentTab}
	<h3>Tab 2 content</h3>
{/if}

{#if 3 === currentTab}
	<h3>Tab 3 content</h3>
{/if}