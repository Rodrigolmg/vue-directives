<template>
	<div id="app">
		<h1>Diretivas (Desafio)</h1>
		<hr>
		<label :style="numberColor">{{ labelTextNumber }}</label>
		<div>
			<button v-when="changeValue">Mudar valor</button>
		</div>
		<!-- Exercício -->
		<!-- Escreva uma diretiva que funcione com o v-on (escute eventos) -->
	</div>
</template>

<script>
	export default {
		directives: {
			when: {
				bind(el, binding){
					el.onclick = function(){
						binding.value()
					}
				}
			}
		},
		data() {
			return {
				labelTextNumber: 0.0,
				numberColor: {},
				even: 0,
				odd: 0
			}
		},
		methods: {
			changeValue(){
				this.labelTextNumber = Math.round(Math.random() * 100)
				let nColor = 'black'
				if(this.labelTextNumber % 2 == 0){
					nColor = 'orange'
					this.even++
				} else {
					nColor = 'lightblue'
					this.odd++
				}

				this.numberColor = {
					color: nColor
				}
				
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

button {
	margin: 10px 0px;
	padding: 10px 20px;
	font-size: 1.4rem;
	border-radius: 5px;
	color: #FFF;
	background-color: #2196F3;
}

.painel {
	display: column;
}
</style>
