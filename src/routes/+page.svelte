<script lang="ts">
	import { MoveIcon, SortableItem } from '$lib/index.js';
	import { flip } from 'svelte/animate';

	let stateUsers = $state([
		{ id: 1, name: 'John', age: 45 },
		{ id: 2, name: 'Mark', age: 33 },
		{ id: 3, name: 'Jonas', age: 56 },
		{ id: 4, name: 'Mary', age: 76 },
	]);
	let stateHoveredItem = $state<number>(-1);
</script>

<svelte:head>
	<!-- MAKE IT WORK ON MOBILE DEVICES -->
	<script src="https://unpkg.com/svelte-drag-drop-touch"></script>
	<!---->
</svelte:head>

<p>MOVE THE <MoveIcon propSize={12} /> ICON TO REORDER ELEMENTS.</p>

{#each stateUsers as currentUser, numberCounter (currentUser.id)}
	<div animate:flip>
		<SortableItem
			propItemNumber={numberCounter}
			bind:propData={stateUsers}
			bind:propHoveredItemNumber={stateHoveredItem}
		>
			<div class:classHovered={stateHoveredItem === numberCounter}>
				<MoveIcon propSize={12} />
				{currentUser.name}
			</div>
		</SortableItem>
	</div>
{/each}

<p>{JSON.stringify(stateUsers)}</p>

<style>
	.classHovered {
		background-color: lightblue;
		color: white;
	}
</style>
