<script lang="ts">
	// PROPS
	type typeData = $$Generic;
	export let propItemNumber: number;
	export let propData: typeData[];
	export let propHoveredItemNumber = 0.000005; // ANY NON-INTEGER NUMBER
	/////
	// FUNCTIONS
	const functionDrop = function (
		parEvent: DragEvent & { currentTarget: EventTarget & HTMLElement },
		parTarget: number
	) {
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
		propHoveredItemNumber = 0.000005; // ANY NON-INTEGER NUMBER
	};
	const functionDragStart = function (
		parEvent: DragEvent & { currentTarget: EventTarget & HTMLElement },
		parIndex: number
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
	class={$$restProps.class || ''}
	draggable="true"
	on:dragstart={(parEvent) => functionDragStart(parEvent, propItemNumber)}
	on:drop|preventDefault={(event) => functionDrop(event, propItemNumber)}
	on:dragover|preventDefault={() => false}
	on:dragenter|preventDefault={() => (propHoveredItemNumber = propItemNumber)}
>
	<slot />
</span>
