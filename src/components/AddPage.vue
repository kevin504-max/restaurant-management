<template>
<HeaderComponent />
<h1>Hi User, Welcome on Add Restaurant Page!</h1>
<form class="add">
    <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name" />
    <input type="text" name="adress" placeholder="Enter Adress" v-model="restaurant.address" />
    <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact" />
    <button type="button" v-on:click="addRestaurant">Add new Restaurant</button>
</form>
</template>

<script>
import HeaderComponent from './HeaderComponent.vue';

export default {
    name: "AddPage",
    components: {
        HeaderComponent
    },
    data() {
        return {
            restaurant: {
                name: "",
                address: "",
                contact: ""
            }
        }
    },
    methods: {
        addRestaurant() {
            console.log(this.restaurant);
        }
    },  
    mounted() {
        let user = localStorage.getItem("user-info");

        if(!user) {
            this.$router.push({name: "SignUp"});
        }
    }
}
</script>

<style></style>