<template>
    <v-card color="grey lighten-4">
        <v-toolbar>
            <v-toolbar-title class="headline text-uppercase mr-4">
                <span>Stock</span>
                <span class="font-weight-light">Trader</span>
            </v-toolbar-title>
            <v-toolbar-items>
                <v-btn plain to="/">Home</v-btn>
                <v-btn plain to="/portfolio">Portfolio</v-btn>
                <v-btn plain to="/stocks">Stocks</v-btn>
            </v-toolbar-items>

            <v-spacer></v-spacer>

            <v-toolbar-items>
                <v-btn plain @click="endDay">End Day</v-btn>
                <v-menu offset-y>
                    <template v-slot:activator="{ on, attrs }">
                        <v-btn v-bind="attrs" v-on="on" plain >Save & Load</v-btn>
                    </template>
                    <v-list>
                        <v-list-item @click="saveData">
                            <v-list-item-title>Save Data</v-list-item-title>
                        </v-list-item>
                        <v-list-item @click="loadDataLocal">
                            <v-list-item-title>Load Data</v-list-item-title>
                        </v-list-item>
                    </v-list>
                </v-menu>
                <v-layout align-center>
                    <span class="text-uppercase grey--text text--darken-2">
                        Funds: {{ funds | currency }}
                    </span>
                </v-layout>
            </v-toolbar-items>
        </v-toolbar>
    </v-card>
</template>

<script>
import { mapActions } from 'vuex'

export default {
    computed: {
        funds() {
            return this.$store.getters.funds
        }
    },
    methods: {
        ...mapActions(['randomizeStocks', 'loadData']),
        endDay() {
            this.randomizeStocks()
        },
        saveData() {
            const { funds, stockPortfolio, stocks, } = this.$store.getters
            this.$http.put('data.json', { funds, stockPortfolio, stocks })
        },
        loadDataLocal() {
            this.loadData()
        }
    }
}
</script>

<style>

</style>