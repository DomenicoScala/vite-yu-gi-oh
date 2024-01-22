<script>
    import AppHeader from './components/AppHeader.vue'
    import AppMain from './components/AppMain.vue'
    import AppFooter from './components/AppFooter.vue'
    import axios from 'axios'
    import { store } from './store.js'

    export default{
        data(){
            return{
                store
            };
        },
        methods:{

        },
        components:{
            AppHeader,
            AppMain,
            AppFooter
        },
        created(){
            axios
            .get ('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
            .then((response) =>{
                console.log(response.data)
                this.store.cards = response.data;

                console.log(this.cards)
                console.log(this.store)
            })
        }
    }
</script>

<template>
        <AppHeader/>

        <AppMain/>

        <AppFooter/>
</template>

<style lang="scss">
    @use "assets/scss/main.scss" as *;
    @use "assets/scss/partials/reset.scss" as *;
</style>
