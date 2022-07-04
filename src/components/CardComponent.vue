<template>
	<div class="card">
		<h6 class="heading">
			<span>Advice</span>
			<span
				>#<span class="id">{{ id }}</span></span
			>
		</h6>
		<p class="advice">
			<q class="adv">{{ quote }}</q>
		</p>
		<div class="divider"></div>
		<button class="btn" @click="getAdvice()">
			<img src="../assets/icon-dice.svg" alt="dice" class="btn__img" />
		</button>
	</div>
</template>

<script>
import axios from "axios";
import gsap from "gsap";

export default {
	computed: {
		quote() {
			return this.advice && this.advice.slip
				? this.advice.slip.advice
				: `It is easy to sit up and take notice, what's difficult
						is getting up and taking action`;
		},
		id() {
			return this.advice && this.advice.slip ? this.advice.slip.id : 117;
		},
	},
	data() {
		return {
			advice: {},
		};
	},
	methods: {
		async getAdvice() {
			try{
				const response = await axios.get("https://api.adviceslip.com/advice");
				this.advice = response.data
			} catch(err){
				this.advice = `Something went wrong ${err.message}`
			}
		},
	},
	mounted() {
		
		this.getAdvice();
		
		let tl = gsap.timeline();
		tl.from(".card",{
			x: 100,
			autoAlpha: 0,
			ease: "back",
			duration: 1,
		})
	},
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
	margin: 1em 0;
	align-self: end;
}
.heading {
	color: $NeonGreen;
	text-transform: uppercase;
	letter-spacing: 4px;
	font-weight: 600;
}
.advice {
	font-size: $fs;
	font-weight: $fw;
	margin: 0.8em 0 0;
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
@media (min-width: 900px) {
	.divider {
		background-image: url(../assets/pattern-divider-desktop.svg);
	}
}
</style>
