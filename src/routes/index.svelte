<script lang="ts">
	import { browser } from '$app/env';
	import { Map, View } from 'ol';
	import { OSM } from 'ol/source';
	import { Tile } from 'ol/layer';
    import "ol/ol.css"
	import { onMount } from 'svelte';

	let target: HTMLDivElement;
	let map: Map;

	onMount(() => {
		if (browser) {
			const view = new View({ center: [0, 0], zoom: 2 });
			const layers = [new Tile({ source: new OSM() })];
			map = new Map({ target, view, layers });
		}
	});
</script>

<div class="ol-container" bind:this={target} />

<style>
	:global(html, body, #svelte),
	div {
		width: 100%;
		height: 100%;
        margin: 0;
        padding: 0;
	}
</style>
