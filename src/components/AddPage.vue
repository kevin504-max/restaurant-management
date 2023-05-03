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
import axios from 'axios';

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
        async addRestaurant() {
            const result = await axios.post("http://localhost:3000/restaurant", {
                name: this.restaurant.name,
                address: this.restaurant.address,
                contact: this.restaurant.contact 
            });

            if(result.status == 201) {
                localStorage.setItem("restaurant-info", JSON.stringify(result.data));
                this.$router.push({name: "HomePage"});
            }
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