<script setup>
const BLOCK = "AFRDisclaimer"
</script>

<template>
	<footer :class="BLOCK">
		<small>* Rankings for Division I schools based on NCAA data (www.ncaa.com) and rankings for Division II & III
			schools
			are based on data from Hero Sports (<a href="https://www.herosports.com/rankings"
				aria-label="Visit Hero Sports Rankings" title="Hero Sports Rankings" target="_blank"
				rel="external">www.herosports.com/rankings</a>)
		</small>
		<small>** GPA is based on SportsRecruits members who have shown interest in (favorited) the school and have provided
			their GPA on their profile</small>
		<small>*** SAT and ACT scores based on national data provided by the National Center of Education Statistics-
			<a href="https://www.herosports.com/rankings" aria-label="Visit National Center for Education Statistics IPEDS"
				title="National Center for Education Statistics IPEDS" target="_blank" rel="external">
				https://nces.ed.gov/ipeds/
			</a>
		</small>
	</footer>
</template>

<style scoped lang="scss">
.AFRDisclaimer {
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	gap: 0 0 1rem;
	margin-top: 4rem;

	@media (min-width: 768px) {
		margin-top: 8rem;
	}

	@media (min-width: 1024px) {
		margin-top: 12rem;
	}

	small {
		display: block;
		font-size: 1.3rem;

		&:not(:first-of-type) {
			margin-top: 1rem;
		}

	}

	a {
		color: var(--blue);
	}
}
</style>