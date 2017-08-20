<script>
import Vue from 'vue';
import anime from 'animejs';

export default Vue.directive('menu-open', {
	inserted(el) {
		function open() {
			const menu = document.body.getElementsByClassName('menu');
			const relativeOffset = anime.timeline();

			document.body.style.overflowY = 'hidden';

			relativeOffset
				.add({
					targets: '.menu',
					translateY: [
						{ value: -500 },
						{ value: 0 },
					],
					opacity: [
						{ value: 0 },
						{ value: 1 },
					],
					easing: 'easeInQuad',
					complete() {
						menu[0].style.pointerEvents = 'auto';
					},
				})
				.add({
					targets: '.menu-overlay',
					translateY: [
						{ value: -500 },
						{ value: 0 },
					],
					opacity: [
						{ value: 0 },
						{ value: 0.95 },
					],
					easing: 'easeInQuad',
					offset: '-=1000',
				})
				.add({
					targets: '.menu-about',
					opacity: [
						{ value: 0 },
						{ value: 1 },
					],
					easing: 'easeOutExpo',
					offset: '-=300',
				})
				.add({
					targets: '.menu-work',
					opacity: [
						{ value: 0 },
						{ value: 1 },
					],
					easing: 'easeOutExpo',
					offset: '-=900',
				});
		}

		el.addEventListener('click', open);
	},
});

</script>
