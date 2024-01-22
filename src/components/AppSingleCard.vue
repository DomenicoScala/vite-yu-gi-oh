<script>
    import { store } from '../store.js'
    export default{
        data(){
            return{
                store
            };
        },
        methods:{

        },
        props:{
           card : Object
        }
    }
</script>

<template>

                                
    
        
            <div class="single-card col-3">
                <div class="image-card">
                    <img :src="card.card_images[0].image_url" alt="">
                </div>

                <div class="text-card bg-warning">
                    <h4>{{ card.name }}</h4>
                    <p>{{ card.archetype }}</p>
                </div>
            </div>


  


           

</template>

<style lang="scss" scoped>
    @use "../assets/scss/partials/reset.scss" as *;
    
    .text-card{
        text-align: center;
        padding: 10px;
        margin-bottom: 20px;
        height: 120px;
        
        >h4{
            font-size: 20px;
            color: white;
            text-align: center;
            margin-top: 10px;
            font-weight: bold;
        }
    }

    

</style>
