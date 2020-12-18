<template>
	<button
		:type="type"
		class="bg-blue-500 duration-300 inline-flex items-center font-medium py-3 px-8 rounded text-sm text-white hover:bg-blue-400 focus:bg-blue-600 focus:outline-none"
		@click="click"
	>
		<slot />
	</button>
</template>

<script>
export default {
	props: {
		to: {
			type: String,
			default: null
		},
		type: {
			type: String,
			default: 'button'
		},
	},
	methods: {
		click (event) {
			if ((event.ctrlKey || event.shiftKey)) {
				if (this.to) {
					let route = this.$router.resolve({ path: this.to });
					window.open(route.href, '_blank');
				}else if (this.href) {
					window.open(this.href, '_blank');
				}
			}else {
				if (this.to) {
					this.$router.push(this.to);
				}else if (this.href) {
					window.location.assign(this.href);
				}
			}
		}
	}
}
</script>
