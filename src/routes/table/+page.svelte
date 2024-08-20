<script lang="ts">
	import { MoveIcon, SortableItem } from '$lib/index.js';
	import { flip } from 'svelte/animate';

	let stateUsers = $state([
		{ id: 1, name: 'John', age: 45 },
		{ id: 2, name: 'Mark', age: 33 },
		{ id: 3, name: 'Jonas', age: 56 },
		{ id: 4, name: 'Mary', age: 76 },
	]);
	let stateHoveredItem = $state(-1);
</script>

<svelte:head>
	<!-- MAKE IT WORK ON MOBILE DEVICES -->
	<script src="https://unpkg.com/svelte-drag-drop-touch"></script>
	<!---->
	<!-- BOOTSTRAP -->
	<link
		href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css"
		rel="stylesheet"
		integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC"
		crossorigin="anonymous"
	/>
	<!---->
</svelte:head>

<div class="px-4">
	<div>MOVE THE TABLE ROWS TO REORDER:</div>

	<table class="table table-striped w-auto">
		<thead>
			<tr>
				<th></th>
				<th>NAME</th>
				<th>AGE</th>
			</tr>
		</thead>
		<tbody>
			{#each stateUsers as currentUser, numberCounter (currentUser.id)}
				<tr animate:flip class:classHovered={stateHoveredItem === numberCounter}>
					<td>
						<SortableItem
							bind:propData={stateUsers}
							propItemNumber={numberCounter}
							bind:propHoveredItemNumber={stateHoveredItem}
						>
							<MoveIcon propSize={15} />
						</SortableItem>
					</td>
					<td>
						<SortableItem
							bind:propData={stateUsers}
							propItemNumber={numberCounter}
							bind:propHoveredItemNumber={stateHoveredItem}
						>
							{currentUser.name}
						</SortableItem>
					</td>
					<td>
						<SortableItem
							bind:propData={stateUsers}
							propItemNumber={numberCounter}
							bind:propHoveredItemNumber={stateHoveredItem}
						>
							{currentUser.age}
						</SortableItem>
					</td>
				</tr>
			{/each}
		</tbody>
	</table>

	<p>{JSON.stringify(stateUsers)}</p>
</div>

<style>
	.classHovered {
		background-color: lightblue;
		color: white;
	}
</style>
