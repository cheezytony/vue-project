<template>
	<a :href="href" class="cursor-pointer font-medium text-blue-500 hover:underline">
		<slot />
	</a>
</template>

<script>
export default {
	props: {
		href: {
			type: String,
			default: null
		},
		to: {
			type: String,
			default: null
		}
	}
}
</script>
