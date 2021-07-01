<template>
	<form
		@submit="onSubmit"
		action="/"
		class="add-form"
	>
		<div class="form-control">
			<label for="">Patient</label>
			<input
				v-model="text"
				type="text"
				name="text"
				placeholder="Add Patient"
			>
		</div>
		<div class="form-control">
			<label for="">Time</label>
			<input
				v-model="time"
				type="text"
				name="time"
				placeholder="Add Time"
			>
		</div>
		<div class="form-control form-control-check">
			<label for="">Set Reminder</label>
			<input
				v-model="reminder"
				type="checkbox"
				name="reminder"
			>
		</div>
		<input
			type="submit"
			value="Save Patient"
			class="btn btn-block"
		>
	</form>
</template>

<script>
export default {
	name: "AddPatient",
	data() {
		return {
			text: "",
			time: "",
			reminder: false,
		};
	},
	methods: {
		onSubmit(e) {
			e.preventDefault();
			if (!this.text) {
				alert("Please add a patient");
				return;
			}
			const newPatient = {
				id: Math.floor(Math.random() * 100000),
				text: this.text,
				time: this.time,
				reminder: this.reminder,
			};
			this.$emit("add-patient", newPatient);

			(this.text = ""), (this.time = ""), (this.reminder = false);
		},
	},
};
</script>

<style scoped>
.add-form {
	margin-bottom: 2.5rem; /* 40px */
}
.form-control {
	margin: 1.25rem 0.3125rem; /* 20px 5px */
}
.form-control label {
	display: block;
	color: #11998e;
	margin-bottom: 0.3125rem; /* 5px */
	font-weight: 600;
}
.form-control input {
	width: 100%;
	height: 2.5rem; /* 40px */
	padding: 0.1875rem 0.4375rem; /* 3px 7px */
	font-size: 1rem;
	border: 0.0625rem solid #11998e; /* 1px */
	border-radius: 0.3125rem; /* 5px */
}
.form-control input::placeholder {
	font-size: 0.875rem; /* 14px */
	color: #11998e;
	opacity: 0.8;
}
.form-control-check {
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.form-control-check label {
	flex: 1;
}
.form-control-check input {
	height: 1.25rem; /* 20px */
	flex: 2;
	border: 0.0625rem solid #11998e;
}
.form-control-check input:checked {
	color: #11998e;
}

/* MediaQueries */
@media (max-width: 36.25rem) {
	/* 580px */
	.add-form {
		margin-bottom: 2rem; /* 32px */
	}
	.form-control {
		margin: 1rem 0.3125rem; /* 16px 5px */
	}
	.form-control input {
		height: 2.25rem; /* 36px */
		padding: 0.1875rem 0.4375rem; /* 3px 7px */
		font-size: 0.9375rem; /* 15px */
	}
	.form-control-check input {
		height: 1.125rem; /* 18px */
	}
}
</style>