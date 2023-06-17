<script setup>
const BLOCK = "AFRTitle"
</script>

<template>
	<div :class="BLOCK">
		<img src="sr-insights.png" alt="SportsRecruits Insights Logo">
		<h2>Academic Fit Report</h2>
	</div>
</template>

<style scoped lang="scss">
.AFRTitle {
	order: 0;
	text-align: left;

	@media (min-width: 1024px) {
		width: 25%;
		order: 1;
		text-align: right;
	}

	h2 {
		margin-top: 1rem;
		font-size: 2rem;
	}
}
</style>