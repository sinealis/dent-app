<template>
	<header>
		<h1>{{ title }}</h1>
		<h2>{{ subtitle }}</h2>
		<Button
			@btn-click="$emit('toggle-add-patient')"
			:text="(showAddPatient ? 'Close' : 'Add Patient')"
			:color="(showAddPatient ? '#333333' : '#b0508d')"
		/>
	</header>
</template>

<script>
import Button from "./Button.vue";

export default {
	name: "Header",
	props: {
		title: String,
		showAddPatient: Boolean,
		subtitle: String,
	},
	components: {
		Button,
	},
	emits: ["toggle-add-patient"],
};
</script>

<style scoped>
header {
	display: flex;
	flex-flow: column wrap;
	justify-content: center;
	align-items: center;
	margin-bottom: 1.25rem; /* 20px */
}
header h1 {
	background: -webkit-linear-gradient(to right, #11998e, #38ef7d);
	background: -moz-linear-gradient(to right, #11998e, #38ef7d);
	background: -o-linear-gradient(to right, #11998e, #38ef7d);
	background: linear-gradient(to right, #11998e, #38ef7d);
	background-clip: text;
	-webkit-background-clip: text;
	-webkit-text-fill-color: transparent;
}
header h2 {
	background: -webkit-linear-gradient(to left, #11998e, #38ef7d);
	background: -moz-linear-gradient(to left, #11998e, #38ef7d);
	background: -o-linear-gradient(to left, #11998e, #38ef7d);
	background: linear-gradient(to left, #11998e, #38ef7d);
	background-clip: text;
	-webkit-background-clip: text;
	-webkit-text-fill-color: transparent;
	margin-bottom: 1.25rem; /* 20px */
}
/* MediaQueries */
@media (max-width: 28.75rem) {
	header h1 {
		font-size: 1.625rem; /* 26px */
	}
	header h2 {
		font-size: 1.25rem; /* 20px */
	}
}
@media (max-width: 36.25rem) {
	header {
		margin-bottom: 1rem;
	}
	header h1 {
		font-size: 1.75rem; /* 28px */
	}
	header h2 {
		font-size: 1.375rem; /* 22px */
		margin-bottom: 0.5rem;
	}
}
</style>