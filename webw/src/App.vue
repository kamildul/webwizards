<template>
	<nav class="navbar navbar-expand-lg navbar-light bg-light sticky-top">
		<div class="container-fluid">
			<a href="#" class="navbar-brand" title="Logoipsum"><img src="/assets/images/LOGO_Placeholder.svg" alt="Logoipsum" /></a>
			<button type="button" class="navbar-toggler" data-bs-toggle="collapse" data-bs-target="#navbarCollapse">
				<span class="navbar-toggler-icon"></span>
			</button>
			<div class="collapse navbar-collapse" id="navbarCollapse">
				<div class="navbar-nav">
					<a @click="scrollToSection('#home')" class="nav-item nav-link" title="Start">Start</a>
					<a @click="scrollToSection('#about')" class="nav-item nav-link" title="O mnie">O mnie</a>
					<a @click="scrollToSection('#gallery')" class="nav-item nav-link" title="Galeria">Galeria</a>
					<a @click="showContactForm" class="nav-item nav-link" title="Kontakt">Kontakt</a>
				</div>
				<div class="navbar-nav ms-auto">
				<a href="#" class="nav-item nav-link">Login</a>
			</div>
			</div>
		</div>
	</nav>
	<div id="home"></div>
	<div class="container-fluid">
		<section id="about">
			<div class="row">
				<div class="col-md-7">
					<img class="img-fluid" src="/assets/images/aboutus.png" alt="About us" />
				</div>
				<div class="col-md-5 section-content">
					<div class="section-heading">
						<h2>O mnie</h2>
					</div>
					<div class="row section-text">
						<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
						<p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
						<p>Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt.</p>
						<p>Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam.</p>
					</div>
				</div>
			</div>
		</section>
		<section id="gallery">
			<div class="row">
				<div class="col-md-12 section-content">
					<div class="row justify-content-center">
						<div class="col-12 col-md-10 col-lg-3">
							<div class="section-heading">
								<h2>Galeria</h2>
							</div>
						</div>
					</div>
				</div>
				<div class="col-md-12">
					<div class="row justify-content-center">
						<div class="col-10 col-md-10 col-lg-10"><GalleryViewer></GalleryViewer></div>
					</div>
				</div>
			</div>
		</section>
	</div>
	<footer>
		&copy; 2003 Kamil Dul (kamil.dul@gmail.com)
	</footer>
    <ContactForm v-if="isModalVisible" @close="hideModal">
      <h2>Kontakt</h2>
    </ContactForm>
</template>
<script>
	import './App.scss';
	import GalleryViewer from '@/components/GalleryViewer.vue';
	import ContactForm from '@/components/ContactForm.vue';
	export default {
		name: 'App',
		components: {
			GalleryViewer,
			ContactForm,
		},
		data() {
			return {
				isModalVisible: false,
			};
		},
		methods: {
			showContactForm() {
				this.isModalVisible = true;
			},
			hideModal() {
				this.isModalVisible = false;
			},
			scrollToSection(sectionId) {
				if (sectionId === '#home') {
					window.scrollTo({
						top: 0,
						behavior: 'smooth'
					});
				} else {
					const element = document.querySelector(sectionId);
					if (element) 
					{
					element.scrollIntoView({ behavior: 'smooth' });
					}
				}
			},
		},
	}
</script>
