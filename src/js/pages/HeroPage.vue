<template>
	<main id="hero">
		<div class="container">
			<div
				class="hero flex flex-col lg:flex-row items-center justify-center lg:justify-between"
			>
				<div
					class="hero-context flex flex-col items-center justify-center"
				>
					<div class="hero-context__logo">
						<img src="/images/logo.png" alt="" />
					</div>
					<h1 class="hero-context__title text-center">
						Body Mass Index Calculator
					</h1>
					<p class="hero-context__text">
						Better understand your weight in relation to your
						height using our body mass index (BM) calculator.
						While BMI is not the sole determinant of a healthy
						weight, it offers a valuable starting point to
						evaluate your overall health and well-being,
					</p>
				</div>

				<BmiForm />
			</div>
		</div>
	</main>
</template>

<script setup>
import BmiForm from "../components/BmiForm.vue";
</script>
