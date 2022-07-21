<template>
	<button class="btn">
		<slot></slot>
	</button>
</template>

<script>
	export default {
		name: 'MyButton'
		
	}
</script>

<style scoped>
.btn {
  padding: 9px 24px;
  /* background: forestgreen; */
  color: #fff;
  font-size: 18px;
  border: none;
  align-self: flex-end;
}

</style>