<script setup>
import AthleteData from "./assets/data.json"
import AcademicFitReport from "./components/AcademicFitReport.vue"
</script>

<template>
	<AcademicFitReport :athlete="AthleteData?.data[0]" />
</template>

<style scoped></style>