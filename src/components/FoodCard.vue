<template>
    <div>
        <h1>{{foodName}}</h1>
        <p>In stock: {{stock}}</p>
        <img :src="foodImage">
        <button @click="addToCart">Add to cart</button>
    </div>
</template>

<script>
    export default {
        name : "FoodCard",
        props: {
            foodName: String,
            foodImage : {
                type : String,
                default : "https://yummydinobuddies.com/app/uploads/2021/09/22693_3D_21oz_DinoTheOriginal_M37_P1929004_Horiz-610x555.jpg"
            },
            stock: Number
        },
        methods: {
            addToCart() {
                this.$emit(`buyItem`, this.foodName);
            },
            toggleDarkMode(){
                console.log("Dark mode toggled in food card for: "+this.foodName);
            }
        },
        mounted () {
            this.$root.$on(`toggleDarkMode`, this.toggleDarkMode);
        },
    }
</script>

<style scoped>
    img{
        height: 15vh;
    }
    div{
        border: navy 3px solid;
        width: 50vw;
        position: relative;
        left: 50%;
        transform: translateX(-50%);
    }
</style>