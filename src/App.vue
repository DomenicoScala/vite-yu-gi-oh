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
            getAllCards() {
                if(this.store.selectArchetipe == ''){
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                .then((res) => {
                    this.store.cards = res.data.data;
                })
                }else{
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0', {
                    params:{
                        archetype: this.store.selectArchetipe,
                    }
                })
                .then((res) => {
                    this.store.cards = res.data.data;
                })
            }

            },
            
            getAllArchetypes(){
                axios
                .get('https://db.ygoprodeck.com/api/v7/archetypes.php')
                .then((responseArchetipe)=>{
                    for(let i = 0; i < responseArchetipe.data.length; i++){
                       this.store.archetipe.push(responseArchetipe.data[i].archetype_name)
                       console.log(responseArchetipe)
                    }
                })
            }
        },
        components:{
            AppHeader,
            AppMain,
            AppFooter
        },
        created(){
            this.getAllCards();
            this.getAllArchetypes();
        }
    }
</script>

<template>
        <AppHeader/>

        <AppMain @searchCardByArchetype="getAllCards()" />

        <AppFooter/>
</template>

<style lang="scss">
    @use "assets/scss/main.scss" as *;
    @use "assets/scss/partials/reset.scss" as *;
</style>
