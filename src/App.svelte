<script>
	// @ts-nocheck

	import { marked } from "marked";

	let name = "yulongbb";
	let src = "/src/assets/svelte.svg";

	let cats = [
		{ id: "1", name: "离线地图" },
		{ id: "2", name: "PDF预览" },
	];
	let title = cats[1].name;

	import Thing from "./lib/Thing.svelte";

	let things = [
		{ id: 1, name: "angular" },
		{ id: 2, name: "flutter" },
		{ id: 3, name: "svelte" },
		{ id: 4, name: "Nestjs" },
	];

	function handleClick(event) {
		console.log(event);
		title = event;

	}

	let value = `Some words are *italic*, some are **bold**`;
</script>

<h1><img {src} alt="logo" /> 学习笔记</h1>

{#each things as thing (thing.id)}
	<Thing name={thing.name} />
{/each}

<main>
	<div class="left">
		<h1>目录</h1>

		<ul>
			{#each cats as { id, name }, i}
				<li>
					<button on:click={() => handleClick(name)}>
						{i + 1}: {name}
					</button>
				</li>
			{/each}
		</ul>
	</div>
	<div class="right">
		<p>{title}</p>


		{@html marked(value)}
	</div>
</main>

<style>
	main {
		display: flex;
		height: 500px;
		flex-flow: row nowrap;
	}
	.left {
		width: 200px;
		background: #fff;
	}
	.right {
		flex: 1;
		background: #f6f8fa;
	}
	/* p {
		color: purple;
		font-family: "Comic Sans MS", cursive;
		font-size: 2em;
	}

	textarea {
		width: 100%;
		height: 200px;
	} */
</style>
