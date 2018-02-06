<template>
	<div class="toolbar">
		<button @click="displayFilterDialog_click">Filter</button>
	</div>
</template>

<script>
	export default {
		methods: {
			displayFilterDialog_click: function() {
				this.$emit("displayFilterDialog_click");
			}
		}

	};
</script>

<style>
.toolbar {
	background-color: #CCC;
	padding: 5px;
}
</style>