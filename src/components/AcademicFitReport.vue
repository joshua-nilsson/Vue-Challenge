<script setup>
defineProps({
	athlete: {
		type: Object,
		required: true
	}
})
</script>

<template>
	<main>
		<div class="wrapper">
			<img v-if="athlete?.profile_image" :src="athlete.profile_image" class="logo"
				:alt="`${athlete?.name ? `${athlete.name}\'s` : 'Athlete\'s'} Profile Picture`" />
		</div>
		<div class="info">
			<h2>{{ athlete?.name }}</h2>
			<ul>
				<li>
					<label>Sport:</label>
					<span>{{ athlete?.sport }}</span>
				</li>
				<li>
					<label>Class:</label>
					<span>{{ athlete?.grad_year }}</span>
				</li>
				<li>
					<label>Club:</label>
					<span>{{ athlete?.club?.name }}</span>
				</li>
				<li>
					<label>High School:</label>
					<span>{{ athlete?.high_school?.name }}</span>
				</li>
				<li>
					<label>GPA:</label>
					<span>{{ athlete?.gpa }}</span>
				</li>
				<li>
					<label>Desired Major:</label>
					<span>{{ athlete?.major }}</span>
				</li>
			</ul>
		</div>
	</main>
</template>

<style scoped></style>