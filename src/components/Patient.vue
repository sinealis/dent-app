<template>
	<div
		@dblclick="$emit('toggle-reminder', patient.id)"
		:class="[patient.reminder ? 'reminder' : '', 'patient']"
	>
		<i
			@click="onDelete(patient.id)"
			class="fas fa-times"
		></i>
		<h3>{{ patient.text }}</h3>
		<p>{{ patient.time }}</p>
	</div>
</template>

<script>
export default {
	name: "Patient",
	props: {
		patient: Object,
	},
	methods: {
		onDelete(id) {
			this.$emit("delete-patient", id);
		},
	},
};
</script>

<style scoped>
.patient {
	padding: 1rem 1.25rem; /* 16px 20px */
	margin: 0.3125rem; /* 5px */
	background: #eaeaea;
	cursor: pointer;
}
.patient.reminder {
	border-left: 0.3125rem solid #b0508d;
}
.patient h3 {
	display: flex;
	align-items: center;
	justify-content: space-between;
	color: #632d4f;
}
.patient p {
	color: #632d4f;
}
.patient i {
	display: flex;
	flex-flow: row wrap;
	align-items: center;
	justify-content: flex-end;
	color: #632d4f;
}
/* MediaQueries */
@media (max-width: 28.75rem) {
	/* 460px */
	.patient {
		padding: 0.5rem 0.625rem; /* 8px 10px */
	}
	.patient.reminder {
		border-left: 0.1875rem solid #b0508d; /* 3px */
	}
	.patient h3 {
		font-size: 1rem;
	}
	.patient p {
		font-size: 0.9375rem; /* 15px */
	}
}
@media (max-width: 36.25rem) {
	/* 580px */
	.patient {
		padding: 0.75rem 1rem; /* 12px 16px */
	}
	.patient h3 {
		font-size: 1.125rem; /* 18px */
	}
}
</style>