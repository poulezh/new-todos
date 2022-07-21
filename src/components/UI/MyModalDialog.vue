<template>
	<div class="dialog" v-if="show" @click.stop="hiddenDialog">
		<div @click.stop class="dialog__content">
			<slot></slot>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'MyModalDialog',
		props: {
			show: {
				type: Boolean,
				default: false

			}
		},
		methods: {
			hiddenDialog () {
				this.$emit('update:show', false)

			}
		}
		
	}
</script>

<style scoped>
.dialog{
	position: fixed;
	top: 0;
	bottom: 0;
	left: 0;
	right: 0;
	background: rgba(0, 0, 0, 0.5);
	display: flex;
}
.dialog__content{
	margin: auto;
	background:  #fff;
	border-radius: 12px;
	min-height: 50px;
	min-width: 300px;

}

</style>