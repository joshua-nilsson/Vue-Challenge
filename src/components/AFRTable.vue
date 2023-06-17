<script setup>
import { ref } from 'vue'
import { AFRRow } from "../components"

const props = defineProps({
	athlete: {
		type: Object,
		required: true
	}
})

const BLOCK = "AFRTable"
const reports = ref(props.athlete?.report)
const gpa = ref(props.athlete?.gpa)
</script>

<template>
	<section :class="BLOCK">
		<table>
			<thead>
				<tr>
					<th class="sticky-column" rowspan="2">School Name</th>
					<th rowspan="2">Athletic Div</th>
					<th rowspan="2">Conference</th>
					<th rowspan="2">
						Ranking*<br />
						<span>(DI NCAA)</span><br />
						<span>(DII & DIII Hero Sports)</span>
					</th>
					<th colspan="5">GPA**</th>
					<th rowspan="2">
						SAT Reading***<br /> 25%-75%
					</th>
					<th rowspan="2">
						SAT Math***<br /> 25%-75%
					</th>
					<th rowspan="2">
						ACT Composite***<br /> 25%-75%
					</th>
				</tr>
				<tr>
					<th colspan="1">Min</th>
					<th colspan="1">25%</th>
					<th colspan="1">50%</th>
					<th colspan="1">75%</th>
					<th colspan="1">Max</th>
				</tr>
			</thead>
			<tbody>
				<AFRRow v-for="(report, index) in reports" v-bind="{ report, gpa }" :key="index" />
			</tbody>
		</table>
	</section>
</template>

<style lang="scss">
.AFRTable {
	table {
		display: block;
		table-layout: fixed;
		width: 100%;
		border-collapse: separate;
		border-spacing: 0;
		overflow-x: auto;
		white-space: nowrap;
	}

	thead {
		background-color: var(--black);
	}

	th {
		padding: 0.25rem 1rem;
		color: var(--white);
		font-size: 1.2rem;
		font-weight: 700;
	}

	th.sticky-column {
		background: var(--black);
	}

	.sticky-column {
		position: sticky;
		left: 0;
		z-index: 999;
		border-right: 1px solid var(--black);
	}

	tbody tr:nth-child(odd) .sticky-column {
		background-color: var(--white);
	}

	tbody tr:nth-child(even),
	tbody tr:nth-child(even) .sticky-column {
		background-color: var(--white-alt);
	}

	@media (min-width: 1325px) {
		table {
			display: table;
			table-layout: initial;
		}

		.sticky-column {
			border: none;
		}
	}
}
</style>