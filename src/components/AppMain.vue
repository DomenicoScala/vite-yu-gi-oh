<script>
    import AppSingleCard from './AppSingleCard.vue';
    import { store } from '../store.js'
    export default{
        data(){
            return{ 
                store
            };
        },
        methods:{

        },
        components:{
            AppSingleCard
        }
    }
</script>

<template>

        <main>
            <section class="bg-warning">
                    <div class="container">
                        <div class="main-bg">
                            <select name="Alien" id="">
                                <option value="" v-for="(archetipe,i) in store.archetipe">{{ archetipe.archetype_name }}</option>
                            </select>
                        </div>

                        <section>
                            <div class="container bg-white px-5 py-5">
                                <div class="number-cards bg-black text-light">
                                    <p>Found {{ store.cards.meta.current_rows }} Cards</p>
                                </div>
                                
                                <div class="card-container">
                                    <div class="row">
                                        <AppSingleCard
                                        v-for="(cart,i) in store.cards.data"
                                        :card="cart"/>
                                    </div>
                                </div>


                            </div>
                        </section>
                    </div>
            </section>
        </main>

</template>

<style lang="scss" scoped>
    @use "../assets/scss/partials/reset.scss" as *;
    .main-bg{
        padding: 50px;

        > select{
            padding:10px 10px;
            text-align: left;
            width: 200px;
            border-radius: 5px;
            border: none;
        }

    }

    .number-cards{
        height: 50px;
        padding: 10px;

        >p{
            vertical-align: middle;
            font-weight: bold;

        }
    }

    .text-card{
        text-align: center;
        padding: 10px;
        
        >h4{
            font-size: 20px;
            color: white;
            text-align: center;
            margin-top: 10px;
            font-weight: bold;
        }
    }

    

</style>
