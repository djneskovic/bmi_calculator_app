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
					{{ bmiText }}
					<span>{{ idealWeight }}{{ idealUnit }}</span>
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
const bmiText = ref(
	"Enter your weight and height and you'll see your BMI result here."
);

const idealWeight = ref("");
const idealUnit = ref("");

const minIdealBMI = 18.5;
const maxIdealBMI = 24.9;

// Computed

const heightUnit = computed(() => {
	bmiTitle.value = "Welcome";
	bmiResult.value = "";
	bmiText.value =
		"Enter your weight and height and you'll see your BMI result here.";
	idealWeight.value = "";
	idealUnit.value = "";

	return selectedOption.value === "metric" ? "cm" : "in";
});

const weightUnit = computed(() => {
	bmiTitle.value = "Welcome";
	bmiResult.value = "";
	bmiText.value =
		"Enter your weight and height and you'll see your BMI result here.";
	idealWeight.value = "";
	idealUnit.value = "";

	return selectedOption.value === "metric" ? "kg" : "lbs";
});

const resultText = computed(() => {
	if (bmiResult.value < 18.5) {
		return (bmiText.value =
			"Your BMI suggests you're a underweight. Your ideal weight is ");
	} else if (bmiResult.value >= 18.5 && bmiResult.value < 24.9) {
		return (bmiText.value =
			"Your BMI suggests you're a normal weight. Your ideal weight is ");
	} else if (bmiResult.value >= 24.9 && bmiResult.value < 29.9) {
		return (bmiText.value =
			"Your BMI suggests you're a overweight. Your ideal weight is ");
	} else if (bmiResult.value >= 29.9) {
		return (bmiText.value =
			"Your BMI suggests you're a obese. Your ideal weight is ");
	}
});

// Function
function calcBmiMetric() {
	bmi.value = (weight.value / height.value ** 2) * 10000;

	bmiResult.value = bmi.value.toFixed(1);

	bmiTitle.value = "Your Bmi is...";

	bmiText.value = resultText.value;

	const minIdealWeight = (minIdealBMI * height.value ** 2) / 10000;
	const maxIdealWeight = (maxIdealBMI * height.value ** 2) / 10000;

	idealWeight.value = `${minIdealWeight.toFixed(
		1
	)} - ${maxIdealWeight.toFixed(1)}`;

	idealUnit.value = "kg";

	height.value = "";
	weight.value = "";

	return bmiResult.value;
}

function calcBmiImperial() {
	bmi.value = (weight.value / height.value ** 2) * 703;

	bmiResult.value = bmi.value.toFixed(1);

	bmiTitle.value = "Your Bmi is...";

	bmiText.value = resultText.value;

	const minIdealWeight = (minIdealBMI * height.value ** 2) / 703;
	const maxIdealWeight = (maxIdealBMI * height.value ** 2) / 703;

	idealWeight.value = `${minIdealWeight.toFixed(
		1
	)} - ${maxIdealWeight.toFixed(1)}`;

	idealUnit.value = "lbs";

	height.value = "";
	weight.value = "";

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
