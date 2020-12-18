<template>
	<div
		class="bg-gray-100 duration-300 flex flex-row hover:bg-gray-200 focus-within:bg-white"
		:class="{ [cursor]: true }"
		@click="generalClick"
	>
		<span
			class="duration-300 flex items-center max-w-24 min-w-24 pl-10 pr-3 text-2xl text-gray-600 w-24"
			:class="{ 'hover:bg-gray-300': isControlInput }"
		>
			<template v-if="isControlInput">
				<ion-icon v-if="isChecked" name="checkbox"></ion-icon>
				<ion-icon v-else name="square-outline"></ion-icon>
			</template>
			<ion-icon v-else :name="iconName"></ion-icon>
		</span>
		<span
			v-if="isControlInput"
			class="bg-transparent duration-300 items-center flex pl-3 pr-10 h-14 text-sm text-gray-600 w-full"
		>
			<slot>{{ label }}</slot>
		</span>
		<input
			v-else
			:type="type"
			:placeholder="placeholder"
			class="bg-transparent duration-300 pl-3 pr-10 py-4 h-14 text-sm w-full hover:bg-gray-300 focus:bg-white focus:outline-none"
		>
	</div>
</template>

<script>
export default {
	props: {
		iconName: {
			type: String,
			default: ''
		},
		label: {
			type: String,
			default: ''
		},
		placeholder: {
			type: String,
			default: ''
		},
		type: {
			type: String,
			default: 'text'
		}
	},
	data () {
		return {
			isChecked: false
		}
	},
	computed: {
		cursor () {
			switch (this.type) {
				case 'checkbox':
				case 'radio':
				case 'switch':
					return 'cursor-pointer';
				default:
					return '';
			}
		},
		isControlInput () {
			return this.type?.match(/checkbox|radio|switch/)
		},
		isLink () {
			return this.type?.match(/link/)
		}
	},
	methods: {
		generalClick (event) {
			switch (this.type) {
				case 'checkbox':
				case 'radio':
				case 'switch':
					this.isChecked = !this.isChecked;
					break;
			}
		}
	}
}
</script>
