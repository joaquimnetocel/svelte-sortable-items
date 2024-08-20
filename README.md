# svelte-sortable-items

![GITHUB VERSION](https://img.shields.io/github/package-json/v/joaquimnetocel/svelte-sortable-items?label=github%20version&logo=github&color=lightgray) ![NPM VERSION](https://img.shields.io/npm/v/svelte-sortable-items?color=red&logo=npm&label=npm%20version) ![NPM Downloads](https://img.shields.io/npm/dw/svelte-sortable-items?color=red&label=npm%20downloads&logo=npm) ![NPM License](https://img.shields.io/npm/l/svelte-sortable-items?color) [![Twitter](https://img.shields.io/twitter/follow/:twitterHandle.svg?style=social&label=@joaquimnetocel)](https://twitter.com/joaquimnetocel)

svelte-sortable-items is a svelte/sveltekit package to create sortable drag-and-drop items. This package allows you to relate a javascript array to sortable HTML elements.

<p style="display:flex;align-items:center;justify-content:center;gap:30px;">
  <img alt='TABLE' src="./table.gif" />
  <img alt='SKELETON' src="./skeleton.gif" />
</p>

## VERSIONS

- VERSION 1.0.0 OR ABOVE WORKS WITH SVELTE 5 ONLY (NEWER AND RECOMMENDED VERSIONS WITH IMPROVEMENTS!)
- PREVIOUS VERSIONS WORKS WITH SVELTE 3, 4 AND 5.

## WHY ANOTHER SVELTE PACKAGE FOR SORTING?

**svelte-sorting-items** differs from other svelte sorting packages by not committing to a specific html structure (like "ul/li" lists). Furthermore, it promotes sorting from the child elements only, instead of sorting the children of a parent element. This allows a non-opinionated structure/styling and, consequently, the ordering of more flexible structures, such as the lines of a table for example.

## FEATURES

- NON-OPINIONATED STYLING.
- NON-OPINIONATED HTML STRUCTURE.
- WORKS ON MOBILE. YOU JUST HAVE TO LOAD [svelte-drag-drop-touch](https://github.com/rozek/svelte-drag-drop-touch)
- TYPESCRIPT SUPPORT.

## DEMOS

- [REPL: BOOTSTRAP 5 TABLE EXAMPLE](https://svelte.dev/repl/b6ac15d832194ccca959961269434d7f)
- [REPL: BASIC EXAMPLE](https://svelte.dev/repl/f00d587a19af40899cdfccfb9a733f23)

## INSTALLATION

```bash
npm install svelte-sortable-items
```

## BASIC EXAMPLE

```svelte
<script lang="ts">
	import { MoveIcon, SortableItem } from 'svelte-sortable-items';
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
```

## MORE EXAMPLES

To run the examples from `/src/routes`:

```bash
git clone https://github.com/joaquimnetocel/svelte-sortable-items.git
cd svelte-sortable-items
npm install
npm run dev
```

## COMPONENT STRUCTURE

- `SortableItem`: A component to create sortable html elements.
- `MoveIcon`: An icon commonly used to sort items.

## PROPS

- PROPS OF `SortableItem`:

| PROP                               | DESCRIPTION                                                                   | TYPE        | REQUIRED | DEFAULT     |
| ---------------------------------- | ----------------------------------------------------------------------------- | ----------- | -------- | ----------- |
| `propData` (bindable)              | AN ARRAY WITH THE DATA.                                                       | `unknown[]` | YES      | -           |
| `propItemNumber`                   | THE INITIAL POSITION OF THE ITEM.                                             | `number`    | YES      | `undefined` |
| `propHoveredItemNumber` (bindable) | THE HOVERED ITEM NUMBER (GENERALY USED TO DO SPECIFIC STYLING WHEN HOVERING). | `number`    | NO       | `-1`        |

- PROPS OF `MoveIcon`:

| PROP       | DESCRIPTION           | TYPE     | REQUIRED | DEFAULT |
| ---------- | --------------------- | -------- | -------- | ------- |
| `propSize` | SIZE OF THE SORT ICON | `number` | NO       | 12      |
