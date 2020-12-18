<template>
	<button
		:type="type"
		class="bg-blue-100 duration-300 inline-flex items-center font-medium py-3 px-8 rounded text-sm text-blue-500 hover:bg-blue-400 hover:text-white focus:bg-blue-600 focus:outline-none focus:text-white"
		@click="click"
	>
		<slot />
	</button>
</template>

<script>
import ButtonPrimary from './ButtonPrimary';

export default {
	extends: ButtonPrimary
}
</script>
