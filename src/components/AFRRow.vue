<script setup>
import { ref } from 'vue';
import { AFRGPA } from "../components"

const props = defineProps({
	report: {
		type: Object,
		required: true
	},
	gpa: {
		type: Number,
		required: true
	}
})

const BLOCK = "AFRRow"
const reports = ref(props.report)
</script>

<template>
	<tr :class="BLOCK">
		<td class="sticky-column text-left">{{ reports?.school }}</td>
		<td>{{ reports?.division }}</td>
		<td class="text-left">{{ reports?.conference }}</td>
		<td>{{ reports?.ranking }}</td>
		<td>{{ reports?.gpa?.min?.toFixed(2) }}</td>
		<td>{{ reports?.gpa?.['25%']?.toFixed(2) }}</td>
		<AFRGPA :schoolGPA="reports?.gpa?.['50%']" v-bind="{ gpa }" />
		<td>{{ reports?.gpa?.['75%']?.toFixed(2) }}</td>
		<td>{{ reports?.gpa?.max?.toFixed(2) }}</td>
		<td>{{ reports?.sat?.reading?.['min'] }} - {{ reports?.sat?.reading?.['max'] }}</td>
		<td>{{ reports?.sat?.math?.['min'] }} - {{ reports?.sat?.math?.['max'] }}</td>
		<td>{{ reports?.act?.['min'] }} - {{ reports?.act?.['max'] }}</td>
	</tr>
</template>

<style scoped lang="scss">
.AFRRow {
	td {
		padding: 0.75rem;
		text-align: center;
		font-size: 1.2rem;
	}

	.text-left {
		text-align: left;
	}
}
</style>