<template>
	<div class="view-wrapper">
		<div class="header-wrapper bordered-container">
		</div>
		<div class="body-wrapper bordered-container">
			<div class="left-nav-wrapper bordered-container"></div><div class="body-content-wrapper bordered-container">
				<recon-console-toolbar
					v-on:displayFilterDialog_click="displayFilterDialog2"
					/>
			</div>
		</div>
		<div class="footer-wrapper bordered-container"></div>
		<transition name="fade">
		<keep-alive>
			<filter-dialog
				v-bind:filterList="filterList"
				v-bind:accessLevelList="accessLevelList"
				v-if="displayFilterDialog"
				v-on:buttonClick="filterDialogButton_click"
				/>
		</keep-alive>
		</transition>
	</div>
</template>


<script>
import ReconConsoleToolbar from "./ReconConsoleToolbar";
import FilterDialog from "./FilterDialog";

export default {
	components: {ReconConsoleToolbar, FilterDialog},
	props: [ 'filterList', 'accessLevelList' ],
	data: function() {
		return {
			displayFilterDialog: false
		}
	},
	methods: {
		displayFilterDialog2: function(evt) {
			this.displayFilterDialog = true;
		},
		filterDialogButton_click: function(button) {
			switch (button) {
				case "Cancel":
				case "OK":
					this.displayFilterDialog = false;
					break;
				default:
					break;
			}
		}
	}
}
</script>

<style>

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.view-wrapper {
	height: 100%;
}
.view-wrapper .bordered-container {
	border-color: #888;
	border-width: 1px;
}

.header-wrapper {
	border-bottom-style: solid;
	height: 10%;
}

.body-wrapper {
	height: 80%;
	overflow-x: hidden;
	position: relative;
	white-space: nowrap;
}

.left-nav-wrapper {
	border-right-style: solid;
	display: inline-block;
	height: 100%;
	position: relative;
	vertical-align: top;
	width: 15%;
}

.body-content-wrapper {
	display: inline-block;
	height: 100%;
	position: relative;
	vertical-align: top;
	width: 85%;
}

.footer-wrapper {
	border-top-style: solid;
	height: 10%;
}
</style>
