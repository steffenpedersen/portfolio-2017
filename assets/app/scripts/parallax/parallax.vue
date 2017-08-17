<script>
import Vue from 'vue';
import anime from 'animejs';

export default Vue.component('parallax', {
	data() {
		return {
		};
	},
	methods: {
		calc() {
			console.log('lol');
		},
		ani() {
			console.log('lol');
		},
	},
	mounted() {
		this.ani();
		window.addEventListener('resize', this.ani);
	},
});
</script>

<style src='./parallax.scss'></style>
<template src='./parallax.html'></template>
