<template>
	<div id="app">
		<Header/>
		<Section/>
	</div>
</template>

<script>
  import Header from "./components/Header.vue";
  import Section from "./components/Section";

  export default {
    name: "App",
    components: {
      Section,
      Header
    },
  };
</script>

<style lang="scss">
	@import '~bootstrap/scss/bootstrap';
	@import './assets/scss/fonts';
	
	body {
		margin: 0;
		padding: 0;
		font-family: 'Roboto-Regular';
	}
	
	ul {
		list-style: none;
	}
	
	@media (min-width: 1600px) {
		.container {
			max-width: 2085px;
		}
	}

</style>
