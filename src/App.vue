<template>
	<div class="container">
		<Header
			@toggle-add-patient="toggleAddPatient"
			title="APP FOR DENTISTS"
			:subtitle="currentDate"
			:showAddPatient="showAddPatient"
		/>
		<div v-show="showAddPatient">
			<AddPatient @add-patient="addPatient" />
		</div>
		<Patients
			@toggle-reminder="toggleReminder"
			@delete-patient="deletePatient"
			:patients="patients"
		/>
	</div>

</template>


<script>
import Header from "./components/Header.vue";
import Patients from "./components/Patients.vue";
import AddPatient from "./components/AddPatient.vue";

export default {
	name: "App",
	components: {
		Header,
		Patients,
		AddPatient,
	},
	data() {
		return {
			patients: [],
			showAddPatient: false,
		};
	},
	methods: {
		toggleAddPatient() {
			this.showAddPatient = !this.showAddPatient;
		},
		addPatient(patient) {
			this.patients = [...this.patients, patient]; //set it to an array, spread across the current patients, and add a new one to it
		},
		deletePatient(id) {
			this.patients = this.patients.filter(
				(patient) => patient.id !== id
			);
		},
		toggleReminder(id) {
			this.patients = this.patients.map((patient) =>
				patient.id === id
					? { ...patient, reminder: !patient.reminder }
					: patient
			);
		},
	},
	computed: {
		currentDate() {
			const today = new Date();
			const currentDay =
				today.getDate() +
				"." +
				(today.getMonth() + 1) +
				"." +
				today.getFullYear();
			return currentDay;
		},
	},
	created() {
		this.patients = [
			{
				id: 1,
				text: "Martina V. - 0901 123 456",
				time: "8:00",
				reminder: true,
			},
			{
				id: 2,
				text: "Milan U. - 0902 123 456",
				time: "8:30",
				reminder: true,
			},
			{
				id: 3,
				text: "Jozef E. - 0903 123 456",
				time: "9:00",
				reminder: true,
			},
			{
				id: 4,
				text: "Veronika J. - 0904 123 456",
				time: "9:30",
				reminder: true,
			},
			{
				id: 5,
				text: "Peter S. - 0905 123 456",
				time: "10:00 h",
				reminder: true,
			},
		];
	},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;400;600&display=swap");
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}
html {
	font-size: 16px;
}
body {
	font-family: "Poppins", Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	background: #11998e;
	background: -webkit-linear-gradient(to right, #11998e, #38ef7d);
	background: linear-gradient(to right, #11998e, #38ef7d);
}
/* --- Loader --- */
.preload {
	width: 100%;
	height: 100vh;
	background-color: #1d976c;
	display: flex;
	justify-content: center;
	align-items: center;
}
.loader {
	width: 3.125em; /* 50px */
	height: 3.125em; /* 50px */
	display: inline-block;
	vertical-align: middle;
	position: relative;
}
.loader-three {
	border-radius: 3.125em; /* 50px */
	border: 3px solid transparent;
	border-top-color: #fff;
	-webkit-animation: spin 1s linear infinite;
	animation: spin 1s linear infinite;
}
.loader-three:after {
	content: "";
	position: absolute;
	top: 0.3125em; /* 5px/16px */
	left: 0.3125em; /* 5px/16px */
	bottom: 0.3125em; /* 5px/16px */
	right: 0.3125em; /* 5px/16px */
	border-radius: 3.125em; /* 50px */
	border: 0.1875em solid transparent; /* 3px */
	border-top-color: #fff;
	opacity: 0.8;
	-webkit-animation: spin 10s linear infinite;
	animation: spin 10s linear infinite;
}
.loader-three:before {
	content: "";
	position: absolute;
	top: 0.75em; /* 12px/16px */
	left: 0.75em; /* 12px/16px */
	bottom: 0.75em; /* 12px/16px */
	right: 0.75em; /* 12px/16px */
	border-radius: 3.125em; /* 50px */
	border: 0.1875em solid transparent;
	border-top-color: #fff;
	opacity: 0.6;
	-webkit-animation: spin 5s linear infinite;
	animation: spin 5s linear infinite;
}
@-webkit-keyframes spin {
	0% {
		-webkit-transform: rotate(0deg);
	}
	100% {
		-webkit-transform: rotate(360deg);
	}
}
@keyframes spin {
	0% {
		transform: rotate(0deg);
	}
	100% {
		transform: rotate(360deg);
	}
}
.container {
	max-width: 37.5rem; /* 600px */
	height: auto;
	margin: 10vh auto;
	overflow: auto;
	border: 0.0625rem solid #fff;
	padding: 1.875rem; /* 30px/16px */
	border-radius: 0.3125rem; /* 5px */
	background: #fafafa;
	transition: opacity 2s ease-in;
}
.btn {
	display: inline-block;
	background: #333;
	color: #f1f1f1;
	border: none;
	padding: 0.625rem 1.25rem; /* 10px 20px */
	margin: 0.625rem auto;
	border-radius: 0.3125rem; /* 5px */
	cursor: pointer;
	text-decoration: none;
	font-size: 0.9375rem; /* 15px */
	font-family: inherit;
}
.btn:hover {
	color: #fff;
	background: #b0508d;
	transform: scale(0.95);
}
.btn:focus {
	outline: none;
	color: #fff;
	background: #b0508d;
	transform: scale(0.95);
}
.btn:active {
	color: #fff;
}
.btn-block {
	display: block;
	width: 50%;
}
/* MediaQueries */
@media (max-width: 23.4375rem) {
	/* 375px */
	.container {
		max-width: 17.1875rem; /* 275px */
		margin: 0 auto;
	}
}
@media (max-width: 28.75rem) {
	/* 460px */
	.container {
		max-width: 21.25rem; /* 340px */
	}
}
@media (max-width: 36.25rem) {
	/* 580px */
	.container {
		max-width: 28.75rem; /* 460px */
		margin: 5vh auto;
		padding: 1.375rem 1rem; /* 22px 16px */
	}
	.btn {
		font-size: 0.875rem; /* 14px */
		padding: 0.5rem 1rem; /* 8px 16px */
	}
}
</style>
