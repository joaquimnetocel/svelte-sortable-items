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
				<th />
				<th>NAME</th>
				<th>AGE</th>
			</tr>
		</thead>
		<tbody>
			{#each arrayUsers as currentUser, numberCounter (currentUser.id)}
				<tr animate:flip class:classHovered={numberHoveredItem === numberCounter}>
					<td>
						<SortableItem
							bind:propData={arrayUsers}
							propItemNumber={numberCounter}
							bind:propHoveredItemNumber={numberHoveredItem}
						>
							<MoveIcon propSize={15} />
						</SortableItem>
					</td>
					<td>
						<SortableItem
							bind:propData={arrayUsers}
							propItemNumber={numberCounter}
							bind:propHoveredItemNumber={numberHoveredItem}
						>
							{currentUser.name}
						</SortableItem>
					</td>
					<td>
						<SortableItem
							bind:propData={arrayUsers}
							propItemNumber={numberCounter}
							bind:propHoveredItemNumber={numberHoveredItem}
						>
							{currentUser.age}
						</SortableItem>
					</td>
				</tr>
			{/each}
		</tbody>
	</table>

	<p>{JSON.stringify(arrayUsers)}</p>
</div>

<style>
	.classHovered {
		background-color: lightblue;
		color: white;
	}
</style>
