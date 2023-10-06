<template>
	<div class="modal">
		<div class="modal-content">
			<button @click="closeModal" class="close-button">
				<img src="/assets/images/close.svg" alt="Close" />
			</button>
			<slot></slot>
			<div v-if="showValidationMessage" class="error-message">
				<div class="alert alert-danger" role="alert">
					Wszystkie pola formularza są wymagane
				</div>
			</div>
			<form @submit.prevent="submitForm">
				<div class="row">
					<div class="form-group">
						<label for="name">Imię:</label>
						<input class="form-control" type="text" id="name" v-model="name" />
					</div>
				</div>
				<div class="row">
					<div class="form-group">
						<label for="surname">Nazwisko:</label>
						<input class="form-control" type="text" id="surname" v-model="surname" />
					</div>
				</div>
				<div class="row">
					<div class="form-group">
						<label for="email">Email:</label>
						<input class="form-control" type="email" id="email" v-model="email" />
					</div>
				</div>
				<div class="row">
					<div class="form-group">
						<label><input type="checkbox" v-model="accept" /> Akceptuję regulamin</label>
					</div>
				</div>
				<div class="text-center">
					<button class="btn btn-primary" type="submit">Wyślij wiadomość</button>
				</div>
			</form>
		</div>
	</div>
</template>

<script>
	import './ContactForm.scss';
	export default {
		data() {
			return {
				name: '',
				surname: '',
				email: '',
				accept: false,
				showValidationMessage: false,
			};
		},
		methods: {
			closeModal() {
				this.$emit('close');
			},
			submitForm() {
				if (!this.name || !this.surname || !this.email || !this.accept) {
					this.showValidationMessage = true;
					return;
				}

				const formData = {
					name: this.name,
					surname: this.surname,
					email: this.email,
					accept: this.accept,
				};

				const formDataJSON = JSON.stringify(formData);
				console.log(formDataJSON);

				this.closeModal();
			},
		},
	};
</script>

<style scoped>
	.error-message {
		color: red;
		margin-top: 10px;
	}

	.modal {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0, 0, 0, 0.5);
		display: flex;
		justify-content: center;
		align-items: center;
		z-index: 1999;
		padding: 0px 100px;

		.modal-content {
			background: #fff;
			padding: 20px;
			border-radius: 5px;
			box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);

			.close-button {
				position: absolute;
				top: 10px;
				right: 10px;
				background: none;
				border: none;
				cursor: pointer;

				img {
					width: 20px;
					height: 20px;
				}
			}
		}
	}
</style>