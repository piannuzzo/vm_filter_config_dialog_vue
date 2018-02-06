<template>
	<div class="view-resize-wrapper" v-resize="onResize">
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
	</div>
</template>

<script>
import ReconConsoleToolbar from "./ReconConsoleToolbar";
import FilterDialog from "./FilterDialog";
//var resize = require("vue-resize-directive");
import resize from 'vue-resize-directive';

export default {
	components: {ReconConsoleToolbar, FilterDialog},
	directives: {
		resize
	},
	mounted: function() {
		//window.addEventListener('resize.', this.fitToContainer.bind(this, this.$el));
		//this.fitToContainer(this.$el);
	},
	beforeDestroy: function() {
		//window.removeEventListener('resize', this.fitToContainer);
	},
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
		},
		fitToContainer: function(el) {
			var elHorizontalBorderWidth = el.offsetWidth - el.clientWidth,
				elVerticalBorderWidth = el.offsetHeight - el.clientHeight;

			el.style.width = el.parentNode.clientWidth - elHorizontalBorderWidth + "px";
			el.style.height = el.parentNode.clientHeight - elVerticalBorderWidth + "px";
		},
		onResize: function(el) {
			this.fitToContainer(el.querySelector(".view-wrapper"));
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

.view-resize-wrapper {
	height: 100%;
	width: 100%;
}
.view-wrapper {
	border: 2px solid #888;
	height: 100%;
}
.view-wrapper .bordered-container {
	border-color: #888;
	border-width: 2px;
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
