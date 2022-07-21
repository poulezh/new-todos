<template>
	<input :value="modelValue" @input="updateInput" class="input" type="text">
</template>

<script>
export default {
	name: 'MyInput',
	props: {
		modelValue: [String, Number]
	},
	methods: {
		updateInput(event) {
			this.$emit('update:modelValue', event.target.value)
		}
	}
}
</script>

<style scoped>
.input {
	border: 1px solid forestgreen;
	padding: 16px;
	margin: 0 16px;
}
</style>