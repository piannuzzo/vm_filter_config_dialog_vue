<template>
	<div class="buttons-outer-container">
		<div class="buttons-left-container">
			<button>Clear</button>
			<button>Reset</button>
		</div>
		<div class="buttons-right-container">
			<button>Apply</button>
			<button v-on:click="filterDialogOKButton_click">OK</button>
			<button v-on:click="filterDialogCancelButton_click">Cancel</button>
		</div>
	</div>
</template>

<script type="text/javascript">
	export default {
		methods: {
			filterDialogCancelButton_click: function(evt) {
				this.$emit("filterDialogCancelButton_click", evt);
			},
			filterDialogOKButton_click: function(evt) {
				this.$emit("filterDialogOKButton_click", evt);
			}
		}
	};
</script>

<style type="text/css">
.buttons-outer-container {
	display: inline-block;
	width: 100%;
}

.buttons-left-container {
	float: left;
}

.buttons-right-container {
	float: right;
}
</style>
