<template>
	<div id="app">
		<h1>Diretivas</h1>
		<p v-text="'Usando diretiva text'"></p>
		<p v-html="'Usando diretiva <strong>v-html</strong>'"></p>
		<hr>
		<p v-highlights.atrasar="'red'">Usando diretiva personalizada com valor da cor de fundo <strong>VERMELHA</strong></p>
		<p v-highlights.atrasar="cor">Usando diretiva personalizada com valor da cor de fundo <strong>AZUL</strong></p>

		<!-- Anatomia de diretivas:
			<tag v-nomeDiretiva:argumento.mod1.mod2="valor"></tag> -->
	</div>
</template>

<script>
export default {
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
