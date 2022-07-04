<template>
	<button class="btn" @click="getAdvice()">
		<img src="../assets/icon-dice.svg" alt="dice" class="btn__img" />
	</button>
</template>

<script>
export default {
	computed: {
		get() {
      return this.data;
    },
	},
	data() {
		return {
			data: {},
		};
	},
	methods: {
		async getAdvice() {
			console.log("yes");
			try {
				const response = await fetch("https://api.adviceslip.com/advice");
				const data = await response.json();
				if (!response.ok)
					throw new Error(`No advice found (${response.status})`);
				const slip  = data;
				// return slip;
				// console.log(slip);
				this.data = slip;
			} catch (err) {
				// advice.textContent = `💥💥💥Something went wrong ${err.message}. Try again!`;
				console.log(err);
			}
		},

		send(){
      this.$emit("send", this.data);
    }
	},
};
</script>

<style lang="scss" scoped>
@import "../styles/global.scss";
.btn {
	border: none;
	background-color: $NeonGreen;
	padding: 1.2em;
	border-radius: 50%;
	position: absolute;
	bottom: -2.2em;
	left: 50%;
	transform: translateX(-50%);
	cursor: pointer;

	&:hover {
		box-shadow: 0px 2px 18px $NeonGreen;
	}
}
</style>
