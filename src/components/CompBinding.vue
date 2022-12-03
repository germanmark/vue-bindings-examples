<template>
    <div>
        <button @click="toggleDarkMode">Toggle dark mode</button>
        <PropComponent :counter="counter" customString="This is my custom message"/>
        <p ref="counterContainer">
            <!-- {{counter}} -->
            {{counter > 5 ? "large" : "small"}}
        </p>
        <button @click="increment">Increment</button>
        <button @click="toggleImage">Show/hide image</button>
        <button @click="changeColor">Change color</button>
        <img v-if="isImageVisible" :src="imageSrc" alt=""/>
        <h3 v-else>No dino nuggies for you :(</h3>
        <!-- <p v-for="(item,index) in foods" :key="index">
            {{index}}{{item}}
        </p> -->
        <FoodCard  
            v-for="(food, index) in inventory" 
            :key="index" 
            :foodName="food.name"
            :stock="food.count"
            :foodImage="food.img"
            @buyItem="shoppingCart"
        />
    </div>
</template>

<script>
import PropComponent from '@/components/PropComponent.vue';
import FoodCard from './FoodCard.vue';
    export default {
        components: { 
                PropComponent,
                FoodCard
        },
        name : "CompBinding",
        data() {
            return {
                counter: 0,
                isImageVisible : false,
                imageSrc : "https://yummydinobuddies.com/app/uploads/2021/09/22693_3D_21oz_DinoTheOriginal_M37_P1929004_Horiz-610x555.jpg",
                foods : [   
                            "Fettuccine",
                            "Watermelon", 
                            "Lasagna", 
                            "Taco",
                            "Donair Poutine", 
                            "Buddha Bowl",
                            "Pizza",
                            "Dates"
                ],
                inventory :[
                    {
                        name : "Fettuccine",
                        count : 5,
                        img : "https://www.modernhoney.com/wp-content/uploads/2018/08/Fettuccine-Alfredo-Recipe-1.jpg"
                    },
                    {
                        name : "Watermelon",
                        count : 20,
                        img : "https://images.saymedia-content.com/.image/t_share/MTc0NDI4Mjc4MDUwNzkyODA4/national-watermelon-day.png"
                    },
                    {
                        name : "Lasagna",
                        count : 12,
                        img : "https://p.kindpng.com/picc/s/148-1483651_transparent-lasagna-png-bitch-lasagna-png-download.png"
                    },
                    {
                        name : "Taco",
                        count : 50,
                        img : "https://www.thewholesomedish.com/wp-content/uploads/2019/06/The-Best-Classic-Tacos-1.jpg"
                    },
                    {
                        name : "Donair Poutine",
                        count : 47,
                        img : "https://primetimedonair.com/wp-content/uploads/2021/09/Beef-Donair-Poutine-scaled.jpg"
                    },
                    {
                        name : "Buddha Bowl",
                        count : 6,
                        img : "https://forkfulofplants.com/wp-content/uploads/2021/02/Vegan-Mexican-Bowl-24-768x1024.jpg"
                    },
                    {
                        name : "Pizza",
                        count : 100,
                        img : "https://img.zoo.media/cache/mod_bt_contentslider/acc437797968b7475dce84d0bf838ae8-220c08548cac211cc7db219bb52f46cf_XL.jpg"
                    },
                    {
                        name : "Dates",
                        count : 5,
                        img : "https://imgs.search.brave.com/osD52onoq357Nu1Fyp4BxbvlWWg5Rv80hd6kXVWyZX8/rs:fit:832:225:1/g:ce/aHR0cHM6Ly90c2Ux/Lm1tLmJpbmcubmV0/L3RoP2lkPU9JUC5E/UkRHeFZLMFZseE1s/VWRiWXNpSWJ3SGFF/TyZwaWQ9QXBp"
                    },
                    {
                        name : "Bibimbap",
                        count : 2,
                        img : "https://recipetineats.com/wp-content/uploads/2019/05/Bibimbap_3.jpg"
                    }
                ],
                cart : []

            }
        },
        methods: {
            increment() {
                this.counter++;
                this.imageSrc = "https://recipetineats.com/wp-content/uploads/2019/05/Bibimbap_3.jpg";
            },
            toggleImage(){
                this.isImageVisible = !this.isImageVisible;
            },
            changeColor(){
                this.$refs.counterContainer.style.color = "pink";
            },
            shoppingCart(item){
                this.cart.push(item);
                // Backing it up in a cookie
            },
            toggleDarkMode(){
                this.$root.$emit(`toggleDarkMode`);
            }
        }
    }
</script>

<style scoped>

</style>