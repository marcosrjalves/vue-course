<template>
    <div class="usuario-detalhe">
        <h3>Usuário Detalhe</h3>
        <hr>
        <p><strong>Código:</strong> {{ id }}</p>
        <!-- <router-link tag="button" primario :to="`/usuario/${id}/editar`">  - acessando o props desse componente-->
        <!-- <router-link tag="button" primario :to="`/usuario/${$route.params.id}/editar`">  - acessando o parametro da rota -->
        <router-link tag="button" primario :to="{name: 'editarUsuario', params: { id: $route.params.id }, query: { completo:true, lingua:'pt' }, hash: '#rodape' }">
            Editar
        </router-link>
    </div>
</template>

<script>
export default {
    beforeRouteEnter(to, from, next) {
        console.log('Dentro do Componente')
        next()
    },
    // data() {
    //     return {
    //         id: this.$route.params.id
    //     }
    // },
    // watch: {
    //     $route(to, from) {
    //         this.id = to.params.id
    //     }
    // },
    props: ['id'],
}
</script>

<style>

</style>