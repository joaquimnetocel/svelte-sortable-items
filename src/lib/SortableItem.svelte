<script lang="ts">
	import type { Snippet } from 'svelte';

	let {
		propItemNumber,
		propData = $bindable(),
		propHoveredItemNumber = $bindable(-1), // ANY NON-INTEGER NUMBER
		children,
		...propRest
	}: {
		propItemNumber: number;
		propData: unknown[];
		propHoveredItemNumber?: number;
		children: Snippet;
	} = $props();

	// FUNCTIONS
	const functionDrop = function (
		parEvent: DragEvent & { currentTarget: EventTarget & HTMLElement },
		parTarget: number,
	) {
		parEvent.preventDefault();
		if (parEvent.dataTransfer === null) return;
		parEvent.dataTransfer.dropEffect = 'move';
		const start = parseInt(parEvent.dataTransfer.getData('text/plain'));
		const newTracklist = propData;

		if (start < parTarget) {
			newTracklist.splice(parTarget + 1, 0, newTracklist[start]);
			newTracklist.splice(start, 1);
		} else {
			newTracklist.splice(parTarget, 0, newTracklist[start]);
			newTracklist.splice(start + 1, 1);
		}
		propData = newTracklist;
		propHoveredItemNumber = -1; // ANY NON-INTEGER NUMBER
	};
	const functionDragStart = function (
		parEvent: DragEvent & { currentTarget: EventTarget & HTMLElement },
		parIndex: number,
	) {
		if (parEvent.dataTransfer === null) return;
		parEvent.dataTransfer.effectAllowed = 'move';
		parEvent.dataTransfer.dropEffect = 'move';
		const start = parIndex;
		parEvent.dataTransfer.setData('text/plain', start.toString());
	};
	/////
</script>

<span
	role="list"
	{...propRest}
	draggable="true"
	ondragstart={(parEvent) => functionDragStart(parEvent, propItemNumber)}
	ondrop={(event) => functionDrop(event, propItemNumber)}
	ondragover={(parEvent: DragEvent & { currentTarget: EventTarget & HTMLElement }) => {
		parEvent.preventDefault();
		return false;
	}}
	ondragenter={(parEvent: DragEvent & { currentTarget: EventTarget & HTMLElement }) => {
		parEvent.preventDefault();
		propHoveredItemNumber = propItemNumber;
	}}
>
	{@render children()}
</span>
