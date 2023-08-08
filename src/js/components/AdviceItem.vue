<template>
	<div class="advice-item">
		<div class="advice-item__icon" v-html="icon"></div>
		<h2>{{ title }}</h2>
		<p>
			{{ text }}
		</p>
	</div>
</template>

<script>
export default {
	props: ["icon", "title", "text"],
};
</script>
