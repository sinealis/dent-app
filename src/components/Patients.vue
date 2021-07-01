<template>
	<div
		v-for="patient in patients"
		:key="patient.id"
	>
		<Patient
			@toggle-reminder="$emit('toggle-reminder', patient.id)"
			@delete-patient="$emit('delete-patient', patient.id)"
			:patient="patient"
		/>
	</div>
</template>

<script>
import Patient from "./Patient.vue";

export default {
	name: "Patients",
	props: {
		patients: Array,
	},
	components: {
		Patient,
	},
	emits: ["delete-patient", "toggle-reminder"],
};
</script>
