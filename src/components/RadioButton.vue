<template>
	<div>
		<div class="radio_box" v-for="(item, idx) in items" :key="idx">
			<input
				type="radio"
				:name="name"
				:id="item.nm"
				class="radio_check"
				:checked="idx === selected"
				:value="item.nm"
				@change="radioCheck"
			/>
			<label :for="item.nm" class="radio_type"> {{ item.nm }} </label>
		</div>
	</div>
</template>

<script>
export default {
	name: 'RadioButton',
	props: {
		name: {
			type: String,
			required: true,
		},
		items: {
			type: Array,
			default: () => {},
		},
		selected: {
			type: Number,
			default: 0,
		},
	},
	methods: {
		radioCheck(e) {
			this.$emit('check', e.target.value)
		},
	},
}
</script>

<style lang="scss">
@import './src/assets/styles/Form.scss';
</style>
