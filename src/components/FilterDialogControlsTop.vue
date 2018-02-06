<template>
	<div class="FilterControlsComponent">
		<div class="controlsLeft">
			<label><span>Name:</span>
				<select v-model="selectedFilter.desc">
					<option v-for="filter in filterList" :value="filter.desc">{{filter.desc}}<span v-if="filter.default === true"> (def.)</span></option>
				</select>
			</label>
			<a href="javascript:void(0);" v-on:click="toggleSaveAsMode">{{saveAsMode ? "Cancel new filter" : "Save as new filter"}}</a>
			<br />
			<label><span>Default:</span><input class="defaultCheckbox" type="checkbox" /></label>
			<br />
			<label v-accessLevelLabel class="access-level-label"><span>Access:</span>
				<select class="accessLevelList">
					<option v-for="accessLevel in accessLevelList">{{accessLevel.desc}}</option>
				</select>
			</label>
		</div>
		<div class="controlsRight">
			<div class="buttonContainer">
				<button>Save</button>
				<button :disabled="selectedFilter.desc === 'Standard'">Delete</button>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		props: ['filterList', 'accessLevelList', 'saveAsMode'],
		data() {
			return {
				selectedFilter: {
					desc: ""
				}
			}
		},
		methods: {
			toggleSaveAsMode: function() {
				this.$emit("toggleSaveAsMode");
			}
		},
		watch: {
			saveAsMode: function(val) {
				document.getElementsByClassName("access-level-label")[0].style.visibility = val ? "visible" : "";
			}
		},
		directives: {
			accessLevelLabel: {
				inserted: function(el) {
				}
			}
		}
	};
</script>

<style>
.FilterControlsComponent {
	position: relative;
	width: 100%;
}

.controlsLeft a {
	color: #555;
	font-size: .9em;
	margin-left:10px;
}

button {
	margin-right: 5px;
}

label {
	display: inline-block;
	line-height: 1.6em;
	white-space: nowrap;
}

label span {
	display: inline-block;
	white-space: nowrap;
	padding-right: 5px;
	text-align: left;
	width: 75px;
}

input[type='text'], select {
	width: 200px;
}

input[type='checkbox'] {
	vertical-align: middle;
}

.access-level-label {
	visibility: hidden;
}

.controlsRight {
	bottom: 0px;
	display: inline-block;
	position: absolute;
	right: 0px;
}

.buttonContainer button:last-child {
	margin-right: 0px;
}
</style>
