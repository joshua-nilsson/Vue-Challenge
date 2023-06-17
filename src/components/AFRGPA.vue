<script setup>
import { ref, computed } from 'vue';

const props = defineProps({
	schoolGPA: {
		type: Number,
		required: true
	},
	gpa: {
		type: Number,
		required: true
	}
})

const BLOCK = "AFRGPA"
const schoolGPA = ref(props.schoolGPA)
const gpa = ref(props.gpa)

const gpaDiff = Math.round(100 * (schoolGPA.value - gpa.value)) / 100

const getGPAColor = computed(() => {
	switch (true) {
		case gpaDiff > 0.1:
			return 'gpa-1'
		case gpaDiff > 0 && gpaDiff <= 0.1:
			return 'gpa-2'
		case gpaDiff === 0:
			return 'gpa-3'
		case gpaDiff < 0 && gpaDiff >= -0.1:
			return 'gpa-4'
		case gpaDiff <= -0.1:
			return 'gpa-5'
		default:
			return null
	}
})

const gpaColor = ref(getGPAColor);

</script>

<template>
	<td :class="`${BLOCK} ${gpaColor}`">{{ schoolGPA?.toFixed(2) }}</td>
</template>

<style scoped lang="scss">
.AFRGPA {
	text-align: center;

	&.gpa-1 {
		background-color: var(--school-gpa-level-1);
	}

	&.gpa-2 {
		background-color: var(--school-gpa-level-2);
	}

	&.gpa-3 {
		background-color: var(--school-gpa-level-3);
	}

	&.gpa-4 {
		background-color: var(--school-gpa-level-4);
	}

	&.gpa-5 {
		background-color: var(--school-gpa-level-5);
	}
}
</style>