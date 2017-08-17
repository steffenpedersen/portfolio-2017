<script>
import Vue from 'vue';
import anime from 'animejs';

export default Vue.directive('age', {
	inserted(el) {
		const ageObj = {
			ageProp: 0,
		};

		const ageAni = anime({
			targets: ageObj,
			ageProp: 27,
			easing: 'linear',
			duration: 1500,
			round: 1,
			update() {
				el.innerHTML = ageObj.ageProp.valueOf();
			},
		});
	},
});

</script>
