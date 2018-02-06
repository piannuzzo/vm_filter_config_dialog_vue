<template>
	<div id="app">
		<main-view v-bind:filterList="this.filterList" v-bind:accessLevelList="this.accessLevelList" />
	</div>
</template>

<script>
import MainView from "./components/MainView";

export default {
	components: { MainView },
	data() {
		return {
			filterList: [
				{"desc": "Standard", "default": true, "access": "Public"},
				{"desc": "My Custom Filter 01", "default": false, "access": "Public"},
				{"desc": "My Custom Filter 02", "default": false, "access": "Private"}
			],
			accessLevelList: [
				{"desc": "Public"},
				{"desc": "Private"}
			]
		};
	}
}
</script>

<style>

HTML, BODY, #app {
	height: 100%;
	margin: 0px;
	padding: 0px;
	width: 100%;
	overflow: hidden;
}

</style>
