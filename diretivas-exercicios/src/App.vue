<template>
	<div id="app">
		<h1>Diretivas</h1>
		<p v-text="'Usando diretiva text'"></p>
		<p v-html="'Usando diretiva <strong>v-html</strong>'"></p>
		<hr>
		<p v-highLocal.delay.alter="{firstColor: 'green', secondColor: 'red', delay: 2000, interval: 200}">Usando diretiva personalizada com valor da cor de fundo <strong>VERMELHA</strong></p>
		<p v-highLocal.delay.alter="{firstColor: 'green', delay: 5000}">Usando diretiva personalizada com valor da cor de fundo <strong>AZUL</strong></p>

		<!-- Anatomia de diretivas:
			<tag v-nomeDiretiva:argumento.mod1.mod2="valor"></tag> -->
	</div>
</template>

<script>
export default {
	directives:{
		'highLocal': {
			bind(el, binding){

				const applyColor = color => {
					if(binding.arg === 'fundo'){
						el.style.backgroundColor = color
					} else {
						el.style.color = color
					}
				}

				let delay = 0;

				if(binding.modifiers['delay']) delay = binding.value.delay

				const firstColor = binding.value.firstColor
				const secondColor = binding.value.secondColor
				let currentColor = firstColor

				setTimeout(() => {
					if(binding.modifiers['alter']) {
						setInterval(() =>{
							currentColor = currentColor === firstColor ? secondColor : firstColor
							applyColor(currentColor)
						}, binding.value.interval)
					}
					applyColor(firstColor)
				}, delay)

				// el.style.backgroundColor = 'lightgreen'
			}
		}
	},
	data(){
		return {
			cor: 'lightblue'
		}
	}
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
	font-size: 2.5rem;
}
</style>
