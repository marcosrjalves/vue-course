<template>
	<div id="app">
		<h1>Rotas com VueRouter</h1>
		<!-- <Menu /> -->
		<router-view name="menu" />
		<transition mode="out-in" enter-active-class="animated rotateInDownLeft" leave-active-class="animated zoomOutRight">
			<router-view />
		</transition>
		<router-view name="menuInferior"/>
	</div>
</template>

<script>
export default {

}
</script>

<style>
	#app {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
</style>
