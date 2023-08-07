<template>
	<div class="form">
		<h2>Enter your details below</h2>

		<!-- Radio Buttons -->
		<div
			class="radio-inputs flex items-center justify-center gap-8 md:gap-28"
		>
			<div class="metric">
				<input
					type="radio"
					id="metric"
					class="radio-btn"
					value="metric"
					name="option"
					v-model="selectedOption"
					checked
				/>
				<label for="metric">Metric</label>
			</div>
			<div class="imperial">
				<input
					type="radio"
					id="imperial"
					class="radio-btn"
					value="imperial"
					name="option"
					v-model="selectedOption"
				/>
				<label for="imperial">Imperial</label>
			</div>
		</div>

		<!-- Inputs -->
		<div
			class="inputs flex flex-col md:flex-row items-center justify-center gap-4"
		>
			<div
				class="height flex flex-col items-start justify-center relative"
			>
				<label for="height">Height</label>
				<input
					type="number"
					id="height"
					v-model="height"
					required
				/>
				<span>{{ heightUnit }}</span>
			</div>
			<div
				class="weight flex flex-col items-start justify-center relative"
			>
				<label for="weight">Weight</label>
				<input
					type="number"
					id="weight"
					v-model="weight"
					required
				/>
				<span>{{ weightUnit }}</span>
			</div>
			<button @click="calcBmi()">Calculate</button>
		</div>

		<!-- Results -->
		<div
			class="results flex flex-col md:flex-row items-center justify-center md:justify-between"
		>
			<div class="results-index">
				<p>{{ bmiTitle }}</p>
				<h2>{{ bmiResult }}</h2>
			</div>
			<div class="results-ideal">
				<p>
					Your BMI suggests you're a healthy weight. Your ideal
					weight is <span>63.3kg.</span>
				</p>
			</div>
		</div>
	</div>
</template>

<script setup>
import { ref, computed } from "vue";

const selectedOption = ref("metric");

const height = ref("");
const weight = ref("");

const bmi = ref("");
const bmiResult = ref("");

const bmiTitle = ref("Welcome");

// Computed

const heightUnit = computed(() => {
	bmiTitle.value = "Welcome";
	bmiResult.value = "";
	return selectedOption.value === "metric" ? "cm" : "in";
});

const weightUnit = computed(() => {
	bmiTitle.value = "Welcome";
	bmiResult.value = "";
	return selectedOption.value === "metric" ? "kg" : "lbs";
});

// Function
function calcBmiMetric() {
	bmi.value = (weight.value / height.value ** 2) * 10000;

	height.value = "";
	weight.value = "";

	bmiResult.value = bmi.value.toFixed(1); // Format the BMI value with one decimal place

	bmiTitle.value = "Your Bmi is...";

	return bmiResult.value;
}

function calcBmiImperial() {
	bmi.value = (weight.value / height.value ** 2) * 703;

	height.value = "";
	weight.value = "";

	bmiResult.value = bmi.value.toFixed(1); // Format the BMI value with one decimal place

	bmiTitle.value = "Your Bmi is...";

	return bmiResult.value;
}

function calcBmi() {
	if (selectedOption.value === "metric") {
		calcBmiMetric();
	} else {
		calcBmiImperial();
	}
}
</script>
