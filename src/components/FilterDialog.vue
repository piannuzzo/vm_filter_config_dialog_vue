<template>
	<div class="filter-dialog-wrapper">
		<div class="filter-dialog">
			<div class="fd-header">
				<div class="fd-header-content">
					Filter Configuration
				</div>
			</div>
			<div class="fd-top-controls">
				<filter-dialog-controls-top
					:filterList="filterList"
					:accessLevelList="accessLevelList"
					:saveAsMode="this.saveAsMode"
					v-on:toggleSaveAsMode="toggleSaveAsMode"
					/>
			</div>
			<div class="fd-main-content-outer">
				<div class="fd-main-content">
					<img src="~@/assets/filterDialogContent.png">
				</div>
			</div>
			<div class="fd-footer-controls">
				<filter-dialog-controls-bottom
					v-on:filterDialogOKButton_click="OKButton_click"
					v-on:filterDialogCancelButton_click="cancelButton_click"
					/>
			</div>
		</div>
	</div>
</template>

<script>
import FilterDialogControlsTop from './FilterDialogControlsTop';
import FilterDialogControlsBottom from './FilterDialogControlsBottom';

export default {
	components: { FilterDialogControlsTop, FilterDialogControlsBottom },
	props: [ 'filterList', 'accessLevelList' ],
	data: function() {
		return {
			saveAsMode: false
		}
	},
	methods: {
		buttonClick: function(evt) {
			this.$emit("buttonClick", evt.textContent || evt.target.innerHTML);
		},
		cancelButton_click: function(evt) {
			this.buttonClick(evt);
		},
		OKButton_click: function(evt) {
			this.buttonClick(evt);
		},
		toggleSaveAsMode: function() {
			this.saveAsMode = !this.saveAsMode;
		}
	}
};
</script>

<style type="text/css">

.filter-dialog-wrapper {
	background-color: rgba(0,0,0,.25);
	height: 100%;
	left: 0px;
	position: absolute;
	top: 0px;
	width: 100%;
}

.filter-dialog {
	border: 2px solid #CCC;
	border-radius: 12px;
	left: 110px;
	margin: 100px auto;
	overflow: hidden;
	width: 690px;
}

.fd-header {
	background-color: #DDD;
	border-bottom: 1px solid #CCC;
	padding: .5em 1em;
}

.fd-header-content {
	font-weight: bold;
}

.fd-top-controls {
	background-color: #EEE;
	padding: .75em 1em;
}

.fd-main-content-outer {
	background-color: #FFF;
	overflow: hidden;
}

.fd-main-content {
	border-top: 1px solid #CCC;
	height: 450px;
	overflow-x: hidden;
	overflow-y: scroll;
	padding: 10px;
}

.fd-footer-controls {
	background-color: #EEE;
	border-top: 1px solid #CCC;
	padding: .5em 1em;
}

</style>
