<script>
// @ts-nocheck

  import Nested from "./lib/Nested.svelte";
  import Info from "./lib/Info.svelte";
  import { marked } from 'marked';

  let name = "yulongbb";
  let src = "/src/assets/svelte.svg";

  const pkg = {
    name: "svelte",
    version: 3,
    speed: "blazing",
    website: "https://svelte.dev",
  };

  let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];


  import Thing from './lib/Thing.svelte';

	let things = [
		{ id: 1, name: 'apple' },
		{ id: 2, name: 'banana' },
		{ id: 3, name: 'carrot' },
		{ id: 4, name: 'doughnut' },
		{ id: 5, name: 'egg' },
	];

	function handleClick() {
		things = things.slice(1);
	}

	let value = `Some words are *italic*, some are **bold**`;
</script>

<h1><img {src} alt="logo" /> {name.toUpperCase()} BlogTemplate</h1>

<p>This is a title.</p>
<Nested answer={"42"} />
<Nested />

<Info {...pkg} />


<h1>The Famous Cats of YouTube</h1>

<ul>
	{#each cats as { id, name }, i}
		<li><a target="_blank" href="https://www.youtube.com/watch?v={id}" rel="noreferrer">
			{i + 1}: {name}
		</a></li>
	{/each}
</ul>


<button on:click={handleClick}>
	Remove first thing
</button>

{#each things as thing (thing.id) }
	<Thing name={thing.name}/>
{/each}


{@html marked(value)}

<textarea bind:value></textarea>


<style>
  p {
    color: purple;
    font-family: "Comic Sans MS", cursive;
    font-size: 2em;
  }

  textarea { width: 100%; height: 200px; }

</style>
