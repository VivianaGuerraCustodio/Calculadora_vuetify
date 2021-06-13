<!-- @format -->

<template>
	<v-app>
		<v-app-bar app color="blue accent-3">
			<div class="d-flex align-center">
				<v-img
					alt="Vuetify Name"
					class="shrink mt-1 hidden-sm-and-down"
					contain
					min-width="500"
					src="./assets/title.png"
					width="200"
				/>
			</div>

			<v-spacer></v-spacer>

			<v-btn
				href="https://github.com/VivianaGuerraCustodio"
				target="_blank"
				text
			>
				<v-img
					alt="logo de github"
					contain
					src="./assets/iu-github.png"
					width="40"
				/>
			</v-btn>
		</v-app-bar>

		<v-main>
			<Calculadora />
		</v-main>
	</v-app>
</template>

<script>
	import Calculadora from './components/Calculadora';

	export default {
		name: 'App',

		components: {
			Calculadora,
		},

		data: () => ({
			//
		}),
	};
</script>
<style lang="scss" scoped>
	html,
	#app {
		background: radial-gradient(
				41.48% 11.48% at 2.38% 8.52%,
				#8a8a8e 0%,
				rgba(255, 255, 255, 0) 100%
			),
			linear-gradient(135deg, #37e7ee 0%, #111133 100%);
		overflow: hidden !important;
		overflow-y: hidden !important;
	}
</style>
