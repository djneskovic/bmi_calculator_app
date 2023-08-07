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
				<input type="number" id="height" required />
				<span>cm</span>
			</div>
			<div
				class="weight flex flex-col items-start justify-center relative"
			>
				<label for="weight">Weight</label>
				<input type="number" id="weight" required />
				<span>kg</span>
			</div>
			<button>Calculate</button>
		</div>

		<!-- Results -->
		<div
			class="results flex flex-col md:flex-row items-center justify-center md:justify-between"
		>
			<div class="results-index">
				<p>Your BMI is...</p>
				<h2>23.4</h2>
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
