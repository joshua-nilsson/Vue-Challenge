<script setup>
import { AFRProfile, AFRTitle, AFRTable, AFRDisclaimer } from "../components"
import AthleteData from "../assets/data.json"

const BLOCK = "AFR"
const athlete = AthleteData?.data[0]
</script>

<template>
	<main :class="BLOCK">
		<section :class="`${BLOCK}-Overview`">
			<AFRProfile v-bind="{ athlete }" />
			<AFRTitle />
		</section>
		<AFRTable v-bind="{ athlete }" />
	</main>
	<AFRDisclaimer />
</template>

<style scoped lang="scss">
.AFR {
	max-width: 1440px;
	margin: 0 auto;

	&-Overview {
		display: flex;
		flex-direction: column;

		@media (min-width: 1024px) {
			flex-direction: row;
			justify-content: space-between;
		}
	}
}
</style>