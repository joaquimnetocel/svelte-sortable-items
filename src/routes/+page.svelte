<script lang="ts">
	import { MoveIcon, SortableItem } from '$lib';
	import { flip } from 'svelte/animate';

	// STATES
	let arrayUsers = [
		{ id: 1, name: 'John', age: 45 },
		{ id: 2, name: 'Mark', age: 33 },
		{ id: 3, name: 'Jonas', age: 56 },
		{ id: 4, name: 'Mary', age: 76 }
	];
	let numberHoveredItem: number;
	/////
</script>

<svelte:head>
	<!-- MAKE IT WORK ON MOBILE DEVICES -->
	<script src="https://unpkg.com/svelte-drag-drop-touch"></script>
	<!---->
</svelte:head>

<p>MOVE THE <MoveIcon propSize={12} /> ICON TO REORDER ELEMENTS.</p>

{#each arrayUsers as currentUser, numberCounter (currentUser.id)}
	<div animate:flip>
		<SortableItem
			propItemNumber={numberCounter}
			bind:propData={arrayUsers}
			bind:propHoveredItemNumber={numberHoveredItem}
		>
			<div class:classHovered={numberHoveredItem === numberCounter}>
				<MoveIcon propSize={12} />
				{currentUser.name}
			</div>
		</SortableItem>
	</div>
{/each}

<p>{JSON.stringify(arrayUsers)}</p>

<style>
	.classHovered {
		background-color: lightblue;
		color: white;
	}
</style>
