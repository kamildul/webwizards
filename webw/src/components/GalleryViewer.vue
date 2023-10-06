<template>
	<div class="carousel-container">
		<div class="custom-button-prev" @click="slidePrev"><img src="/assets/images/arrow-left.svg" alt="Prev" /></div>
		<div class="custom-button-next" @click="slideNext"><img src="/assets/images/arrow-right.svg" alt="Next" /></div>
		<div class="swiper-container">
			<div class="swiper-wrapper">
				<div class="swiper-slide" v-for="(item, index) in items" :key="index">
					<div class="image-container">
						<img :src="item.image" :alt="'Zdjęcie ' + (index + 1)" class="carousel-image" />
					</div>
				</div>
			</div>
		</div>
		<div class="swiper-pagination"></div>
	</div>
</template>
<script>
	import Swiper, { Pagination } from 'swiper';
	Swiper.use([Pagination]);
	import './GalleryViewer.scss';
	export default {
		data() {
			return {
				items: [
					{ image: '/assets/images/slider1.png' },
					{ image: '/assets/images/slider2.png' },
					{ image: '/assets/images/slider3.png' },
					{ image: '/assets/images/slider4.png' },
				],
				swiper: null,
			};
		},
		mounted() {
			this.initSwiper();
		},
		methods: {
			initSwiper() {
				this.swiper = new Swiper('.swiper-container', {
					navigation: {
						nextEl: '.custom-button-next',
						prevEl: '.custom-button-prev',
					},
					pagination: {
						el: '.swiper-pagination',
						clickable: true,
					},
				});
			},
			slidePrev() {
				if (this.swiper) {
					this.swiper.slidePrev();
				}
			},
			slideNext() {
				if (this.swiper) {
					this.swiper.slideNext();
				}
			},
		},
	};
</script>
<style scoped>
	.carousel-container {
		:global(.swiper-pagination-bullet) {
			width: 18px;
			height: 18px;
			background: #afafaf;
			opacity: 1;
		}
		:global(.swiper-pagination-bullet-active) {
			background: #FF4359;
			width: 24px;
			height: 24px;
		}
	}
</style>