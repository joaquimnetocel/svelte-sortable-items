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

- [REPL: BOOTSTRAP 5 TABLE EXAMPLE](https://svelte-5-preview.vercel.app/#H4sIAAAAAAAACu1VXW_bNhT9K5w2IAlgiU0dd5siGXNirXUaW4vtpRiqPtASLbGRSIKknDmC_vtAfUXW1pc9DnsxzHsPz-U95D0qjD1JsTTsz4VBUYYN25hxbowMdeR6IQ84VdgYGZLlItQRR4aCcAVSRGM3MJQMjGlAA0UyzoQCBViyA16EjI7AhgmFdileKJyBEuwFy8BZzWjKJmcShTN5dn1CsU8JH2yAiJIMKVwhaaBSrIBUSOHfJRYSuOCHanX-WScDVQAS2eByBHRTNji7Ywk9GwEUYxtcTUA56sPedrAlEk8tbDwewMY9Nopki5u8G-Cu-nTHFvZjC_tycX3SwAd2wAJHlUhdG-alRjmwFlsLTJ1aCDvBKKoUd74zTbCcffTAYgs--euPwF-BpX-zuPfA3Htc3HobYJo1tLk0KUI3MBKluLQhzCl_iq2QZbC5lEig2IwE46ZieZgExrR_gqpgS6hr3_j-drNdz37ryqSEPtVSJALve6XCiFpfZYRTchAWxQpSnsEdY0oqgfgvE-uN9RZGRCoYSvmasDJCrVDKwKhZBU7dwJDqmGKZYKzaOKEKx4Koo84maPzTlek9brYPqzFEL1y8v5zRbPwwj_nd_SL7eYXYmz9eLl9U-LB9_lXyaHycv5s8siTheX7rZ_ezzdfbljoUTEomSEyoGxiIMnrMWN6cCJ7q4sDBHVEnIgcQpkhKNzD4n-ZVMy06Pl36jx7YfvDAdnZz74G1_2kDtj5Ye_567q1tB2pQ_dydalg6pnpVD5BUgnAcgWcT5Yo1_HpH91Dqpej-V8mpA1UyCK1mS-8fwrP3p1EHdmQ6_lrGUTsWHTtc8T1GYdIfUyRBmAuBqdLrEaB5tsPiluVUYQHOezmLRBdl_xgCNA5gV-5QKWFXv80AucXfx8l1T0uUvc40aXSyDpTTt6zTVKB2hEY2F4zPkUJNtaqtcojUIM2wqmq7xekZvsnbO3q7c9jSYPN0yOW07gs04Ya8YLe4nJQADhuF_U5PVYEDWf6DMhX9l6bNuvxfnm_Jg-J_r07PKQJVQG0HZWccnVc4sCJrrY5Pi7uNv7K0sdGY7I_nryJdlA7kldO23uhUX4OKx-rbASjqQjsUPsWC5TQyQ5YyYYOUxInapTm-bhy-Dj8nRNWhsnLyhtYYGRmLyJ7gyLCVyHH5pfwLBn1atDYJAAA=)
- [REPL: BASIC EXAMPLE](https://svelte-5-preview.vercel.app/#H4sIAAAAAAAACnWSW2-bQBCF_8p0W8m2BEa5tRIBpDRBipPYSLabPoQ8rGGNV4FdtDu4chH_veKWYEd9Qdqdbw8z50xJtjxlmtgvJRE0Y8QmN3lODIKHvD7oPUuREYNoWaiovnF0pHiOkFKRuCFBHRIvFCHyLJcKoYS53LNZJIUBK6mQblI2Q5ZBBVslMxi1iqbuaiZHlunR9ZHENuX5yQOLCp5RZA0pQkwZgkaK7JdmSoML35rT-KUuhlgCj204M6AeyobRg9yJkQE0YTZcXkFlDLHzd2xO1VuPXVycYBcDNUF1z119P-Euh3KHHvvRY6-T66MB7uWeKRY3JvVjOKLINkx5Y_Osph2rNb02WjitIfaO0bhx3vlimjC_efRhtobfwfIRggXMg5-zJx_u_OfZrb8C02zRLjytIjckO8Rc25ZViPwtmUYys7pwYkUTM1YyN1EW0S4k3rCD5oeNoGOd9CKc3JsHzz6s731w-k2AXMl8xf8ytzw7r8DyYHYbLGAdwNIPlnf-Evwnf-4v1qupY-WNTvmV0Wg3TJhqiAqlmMD6bEDr0K0sBDIF40FtyuNJ1fQZ8z10e2PXO-W1MTnDxWyvQqx7rM-LRtctj_SrntpwEds1ekeRuuVHf5-JQa695mne3SOvf9s0HKVUa7v5dujnh-C67rED1btIiP83_oMph4bV6_o-gGPFfN87ZQ2tasPvyqVVJ1R1oZcPq2Ax1ai4SPj2MP4wZlL1mToaDylrRKbD8aBsf7ah0VuiZCFiM5KpVDakPNnhJi3YdUt01392HNurqtnBTpYYJJMx33IWExtVwarX6h-goru64AQAAA==)

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
