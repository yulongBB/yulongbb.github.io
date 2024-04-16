<script>
	import { onDestroy } from "svelte";

	const emojis = {
		angular: "🍎",
		flutter: "🍌",
		svelte: "🥕",
		Nestjs: "🍩",
	};

	// the name is updated whenever the prop value changes...
	export let name;

	// ...but the "emoji" variable is fixed upon initialisation of the component
	const emoji = emojis[name];

	// observe in the console which entry is removed
	onDestroy(() => {
		console.log("thing destroyed: " + name);
	});
</script>

<span> {name} {emoji}</span>

<style>
	span {
		display: inline-block;
		padding: 0.2em 1em 0.3em;
		margin: 1em;
		text-align: center;
		border-radius: 0.2em;
		background-color: #ffdfd3;
	}
</style>
