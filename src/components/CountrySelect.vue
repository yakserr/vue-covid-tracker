<template>
	<select
		@change="onChange()"
		v-model="selected"
		class="form-select mt-10 block w-full border p-3 rounded"
	>
		<option value="0">Selected Country</option>
		<option v-for="(country, index) in countries" :value="country.ID">
			{{ index + 1 }} {{ country.Country }}
		</option>
	</select>
</template>

<script>
export default {
	name: "CountrySelect",
	props: ["countries"],
	data() {
		return {
			selected: 0,
		};
	},
	methods: {
		onChange() {
			const country = this.countries.find(
				(item) => item.ID === this.selected
			);

			console.log(country);

			this.$emit("get-country", country);
		},
	},
};
</script>