<script>
import Vue from 'vue';
import anime from 'animejs';

export default Vue.directive('menu-close', {
	inserted(el) {
		function close() {
			const menu = document.body.getElementsByClassName('menu');
			const relativeOffset = anime.timeline();

			document.body.style.overflowY = 'visible';

			relativeOffset
				.add({
					targets: '.menu-work',
					opacity: [
						{ value: 1 },
						{ value: 0 },
					],
					easing: 'easeOutExpo',
				})
				.add({
					targets: '.menu-about',
					opacity: [
						{ value: 1 },
						{ value: 0 },
					],
					easing: 'easeOutExpo',
					offset: '-=800',
				})
				.add({
					targets: '.menu-overlay',
					translateY: [
						{ value: 0 },
						{ value: -500 },
					],
					opacity: [
						{ value: 0.95 },
						{ value: 0 },
					],
					easing: 'easeOutExpo',
					offset: '-=600',
				})
				.add({
					targets: '.menu',
					translateY: [
						{ value: 0 },
						{ value: -500 },
					],
					opacity: [
						{ value: 1 },
						{ value: 0 },
					],
					easing: 'easeInQuad',
					offset: '-=1200', // Starts 600ms before the previous animation ends
					complete() {
						menu[0].style.pointerEvents = 'none';
					},
				});
		}

		el.addEventListener('click', close);
	},
});

</script>
