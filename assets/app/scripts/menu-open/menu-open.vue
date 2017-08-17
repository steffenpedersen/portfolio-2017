<script>
import Vue from 'vue';
import anime from 'animejs';

export default Vue.directive('menu-open', {
	inserted(el) {
		function open() {
			// open menu
			const menu = document.body.getElementsByClassName('menu');
			const relativeOffset = anime.timeline();

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
					targets: '.topic-web',
					translateY: [
						{ value: -250 },
						{ value: 0 },
					],
					opacity: [
						{ value: 0 },
						{ value: 1 },
					],
					easing: 'easeOutExpo',
					offset: '-=300',
				})
				.add({
					targets: '.topic-design',
					translateY: [
						{ value: -250 },
						{ value: 0 },
					],
					opacity: [
						{ value: 0 },
						{ value: 1 },
					],
					easing: 'easeOutExpo',
					offset: '-=900',
				})
				.add({
					targets: '.topic-writing',
					translateY: [
						{ value: -250 },
						{ value: 0 },
					],
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
