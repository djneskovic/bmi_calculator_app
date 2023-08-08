<template>
	<main id="advice">
		<div class="container">
			<div class="advice">
				<div
					class="advice-items flex flex-col md:flex-row md:gap-6 items-center justify-center"
				>
					<AdviceItem
						v-for="item in adviceItems"
						:key="item.id"
						:icon="item.icon"
						:title="item.title"
						:text="item.text"
					/>
				</div>
			</div>
		</div>
	</main>
</template>

<script setup>
import AdviceItem from "../components/AdviceItem.vue";

const adviceItems = [
	{
		id: 1,
		icon: `<i class="fas fa-hamburger pink"></i>`,
		title: "Healthy eating",
		text: "Healthy eating promotes weight control, disease prevention, better digestion, immunity, mental clarity and mood.",
	},
	{
		id: 2,
		icon: `<i class="fas fa-moon blue"></i>`,
		title: "Adequate sleep",
		text: "Sleep enhances mental clarity, emotional stability and physical wellness, promoting overall restoration and rejuvenation.",
	},
	{
		id: 3,
		icon: `<i class="fas fa-dumbbell yellow"></i>`,
		title: "Regular exercise",
		text: "Exercise improves fitness, aids weight control, elevates mood and reduces disease risk, fostering wellness and longevity.",
	},
];
</script>
