<script>
import Vue from 'vue';

const poem = ['JOHN CAGE', 'Lecture on Nothing'].reverse();

export default Vue.component('words', {
	data() {
		return {
			display: '',
		};
	},
	methods: {
		loadLoop(milliseconds, counter) {
			setTimeout(() => {
				if (counter - 1 === 0) {
					return true;
				} else {
					this.display = poem[counter - 1];
					this.loadLoop(milliseconds, counter - 1);
				}
			}, milliseconds);
		},
	},
	mounted() {
		this.loadLoop(2000, poem.length);
	},
});
</script>

<style src='./words.scss'></style>
<template src='./words.html'></template>
