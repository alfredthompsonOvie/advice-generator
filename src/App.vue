<template>
	<div class="container">
		<Card />
		<div class="attribution">
			Challenge by
			<a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
				>Frontend Mentor</a
			>. Coded by
			<a href="https://www.linkedin.com/in/alfredthompsonovie/" target="_blank"
				>Alfred Thompson Ovie</a
			>.
		</div>
	</div>
</template>

<script>
import Card from "./components/CardComponent.vue";

export default {
	name: "App",
	components: {
		Card,
	},
};
</script>

<style lang="scss">
@import "./styles/global.scss";
</style>
