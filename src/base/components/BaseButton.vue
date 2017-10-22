<template>
	<button
		class="dc-button"
		@click="handleClick"
		:autofocus="autofocus"
		:class="[
			size ? 'dc-button-' + size : '',
			{
				'disabled': disabled,
				'loading': loading
			}
		]"
	>
		<i class="dc-icon-loading" v-if="loading" @click="stopPropagation"></i>
		<i :class="icon" v-if="icon && !loading" @click="stopPropagation"></i>
		<slot></slot>
	</button>
</template>

<script>
	const name = 'DCButton';

	export default {
		name: name,
		props: {
			autofocus: {
				type: Boolean,
				default: false
			},
			size: {
				type: String,
				default: 'normal'
			},
			disabled: {
				type: Boolean,
				default: false
			},
			loading: {
				type: Boolean,
				default: true
			},
			icon: {
				type: String,
				default: ''
			}
		},

		methods: {
			handleClick(e) {
				this.$emit('click', e);
			},
			stopPropagation(e) {
				this.disabled && e.stopPropagation();
			}
		}
	}	
</script>