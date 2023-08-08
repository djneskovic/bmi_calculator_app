<template>
	<main id="limitation">
		<div class="container">
			<div
				class="limitation w-full flex flex-col items-center lg:items-center justify-center"
			>
				<div
					class="limitation-context flex flex-col items-center justify-center"
				>
					<h2>Limitation of BMI</h2>
					<p>
						Although BMI is often a practical indicator of
						healthy weight, it is not suited for every person.
						Specific group should carefully consider their BMI
						outcomes and in certain cases, the measurment may
						not be beneficial to use.
					</p>
				</div>

				<LimitationItems />
			</div>
		</div>
	</main>
</template>

<script setup>
import LimitationItems from "../components/LimitationItems.vue";
</script>
