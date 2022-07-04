<template>
	<div class="card">
		<slot name="title" />
		<slot name="advice" class="advice" />
		<div class="divider"></div>
		<Button @send="data" />
	</div>
</template>


<template #title>
        <h6 class="heading">
					<span>Advice</span>
					<span>#<span class="id">{{ id }}</span></span>
				</h6>
      </template>
      <template #advice>
        <p class="advice">
					<q class="adv"
						>{{ advice }}</q
					>
				</p>
      </template>


<script>
import Button from "./ButtonComponent.vue";
export default {
	components: {
		Button,
	},
	// data() {
	// 	return {
	// 		slip: {},
	// 	};
	// },
  methods: {
    data(value){
      console.log(value);
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../styles/global.scss";

.card {
	max-width: 480px;
	background-color: $DarkGrayishBlue;
	border-radius: 10px;
	padding: 3em 2em;
	text-align: center;
	position: relative;
}
.divider {
	display: block;
	margin: 2em 0 1em;
	padding-top: 16px;
	background-image: url(../assets/pattern-divider-mobile.svg);
	background-position: center;
	background-repeat: no-repeat;
	background-size: contain;
	background-size: 100%;
}
@media (min-width: 900px) {
	.divider {
		background-image: url(../assets/pattern-divider-desktop.svg);
	}
}
</style>
