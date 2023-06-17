<script setup>
import { ref } from 'vue';

const props = defineProps({
	athlete: {
		type: Object,
		required: true
	}
})

const BLOCK = "Profile"
const athlete = ref(props.athlete)
const avatarColor = ref('')
const pattern = new RegExp(/^[A-Z]/)
const alphabet = ['ABCD', 'EFGH', 'IJKL', 'MNOP', 'QRSTU', 'VWXYZ']

/**
 * Gets the initials of an athlete's first and last name
 * @param {string} name Athlete's name
 * @returns {string[]} First initial, Last initial
 */
const getInitials = name => {
	// if (typeof name !== "string") return ['?', '?']
	const initials = name.split(' ').map(char => char.charAt(0).toUpperCase() || '')
	return [initials[0], initials[initials.length - 1]]
}

const [firstInitial, lastInitial] = getInitials(athlete.value.name)

// If the last initial matches any character from A-Z, assign the respective color class
// Else assign a random color class
if (lastInitial?.match(pattern)) {
	const index = alphabet.findIndex(elem => elem.includes(lastInitial))
	avatarColor.value = alphabet[index].toLowerCase()
} else {
	avatarColor.value = alphabet[Math.floor(Math.random() * alphabet.length)].toLowerCase()
}
</script>

<template>
	<div :class="BLOCK">
		<div :class="`${BLOCK}-Avatar`">
			<img v-if="atdhlete?.profile_image" :src="athlete.profile_image"
				:alt="`${athlete?.name ? `${athlete.name}\'s` : 'Athlete\'s'} Profile Picture`" />
			<div v-else :class="avatarColor">
				<span>{{ firstInitial }}</span>
				<span>{{ lastInitial }}</span>
			</div>
		</div>
		<div :class="`${BLOCK}-Info`">
			<h1>{{ athlete?.name }}</h1>
			<div>
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
		</div>
	</div>
</template>

<style scoped lang="scss">
.Profile {
	display: flex;
	flex-direction: column;
	order: 1;
	margin: 4rem 0;

	@media (min-width: 425px) {
		flex-direction: row;
	}

	@media (min-width: 650px) {
		margin: 4rem 0 3rem;
	}

	@media (min-width: 1024px) {
		width: 100%;
		order: 0;
		margin: 0 0 7rem;
	}

	&-Avatar {
		margin-bottom: 1rem;

		@media (min-width: 425px) {
			margin-bottom: 0;
		}

		img,
		div {
			width: 10rem;
			height: 10rem;
			border-radius: 50%;
		}

		div {
			display: flex;
			justify-content: center;
			align-items: center;
		}

		.abcd {
			background-color: var(--avatar-placeholder-1);
		}

		.efgh {
			background-color: var(--avatar-placeholder-2);
		}

		.ijkl {
			background-color: var(--avatar-placeholder-3);
		}

		.mnop {
			background-color: var(--avatar-placeholder-4);
		}

		.qrstu {
			background-color: var(--avatar-placeholder-5);
		}

		.vwxyz {
			background-color: var(--avatar-placeholder-6);
		}

		span {
			color: var(--white);
			font-size: 2.2rem;
			font-weight: 700;
		}
	}

	&-Info {
		width: 100%;

		@media (min-width: 425px) {
			margin: 0 1.5rem;
		}

		@media (min-width: 1024px) {
			width: 75%;
		}

		div {
			display: flex;
			justify-content: space-between;
			gap: 3rem;
		}

		h1 {
			color: var(--blue);
			font-size: 2.2rem;
			font-weight: 700;
		}

		ul {
			display: flex;
			flex-direction: column;
			gap: 1rem 4rem;
			margin: 1rem 0 0;
			padding: 0;
			list-style: outside;
			list-style-type: none;

			@media (min-width: 650px) {
				flex-wrap: wrap;
				gap: 1rem 6rem;
				width: 75%;
				height: 9rem;
				order: 0;
			}

			@media (min-width: 1024px) {
				width: 50%;
			}

			@media (min-width: 1440px) {
				width: 35%;
			}
		}

		li {
			font-size: 1.6rem;
		}

		label {
			margin-right: 0.5rem;
			font-weight: 700;
		}
	}
}
</style>