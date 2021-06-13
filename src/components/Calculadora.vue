<!-- @format -->

<template>
	<v-container class="justify-center d-flex">
		<v-card class=" calculator justify-center margin_top_20">
			<p v-if="numero" class="calculator_result">
				{{ display }}
			</p>
			<v-container class="d-flex mobile">
				<v-container class="d-flex row">
					<v-btn
						class="m_4"
						@click="adjuntar(numero)"
						v-for="numero in numeros"
						:key="numero"
						>{{ numero }}</v-btn
					>
				</v-container>
				<v-container class="d-flex row" >
					<v-btn class="m_4" @click="sign">+/-</v-btn>
					<v-btn class="m_4" @click="limpiarCampo">C</v-btn>
					<v-btn class="m_4" @click="porcentaje">%</v-btn>
					<v-btn class="m_4" @click="dividir">÷</v-btn>
					<v-btn class="m_4" @click="multiplicar">x</v-btn>
					<v-btn class="m_4" @click="restar">-</v-btn>
					<v-btn class="m_4" @click="sumar">+</v-btn>
					<v-btn class="m_4" @click="decimal">.</v-btn>
					<v-btn class="m_4" @click="igualar">=</v-btn>
				</v-container>
			</v-container>
		</v-card>
	</v-container>
</template>

<script>
	export default {
		name: 'Calculadora',
		data: () => ({
			numeros: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9'],
			numero: [],
			previous: null,
			display: 0,
			operator: null,
			operatorClicked: false,
		}),

		methods: {
			limpiarCampo() {
				this.display = 0;
			},
			adjuntar(number) {
				if (this.operatorClicked === true) {
					this.display = '';
					this.operatorClicked = false;
				}
				this.display =
					this.display === 0
						? (this.display = number)
						: '' + this.display + number;
			},
			sign() {
				this.display =
					this.display < 0
						? (this.display = this.display - this.display * 2)
						: (this.display = this.display - this.display * 2);
			},
			porcentaje() {
				this.display = this.display / 100;
			},
			decimal() {
				if (this.display.indexOf('.') === -1) {
					this.adjuntar('.');
				}
			},
			dividir() {
				this.operator = (a, b) => a / b;
				this.previous = this.display;
				this.operatorClicked = true;
			},
			multiplicar() {
				this.operator = (a, b) => a * b;
				this.previous = this.display;
				this.operatorClicked = true;
			},
			restar() {
				this.operator = (a, b) => a - b;
				this.previous = this.display;
				this.operatorClicked = true;
			},
			sumar() {
				this.operator = (a, b) => a + b;
				this.previous = this.display;
				this.operatorClicked = true;
			},
			igualar() {
				this.display = this.operator(
					Number(this.previous),
					Number(this.display),
				);
				this.previous = null;
				this.operatorClicked = true;
			},
		},
	};
</script>
<style lang="scss" scoped>
	.calculator {
		width: 450px;
		&_result {
			padding: 20px;
			border: 1px solid rgb(17, 67, 90);
			margin: 5px;
			border-radius: 5px;
		}
		.m_4 {
			margin: 4px;
		}
	}
	.margin_top_20 {
		margin-top: 120px;
	}
	@media screen and (max-width: 400px) {
		.mobile {
			
			flex-flow: column-reverse;
		}
	}
</style>
