<template>
<HeaderComponent />
<h1>Hi User, Welcome on Update Page!</h1>
<form class="add">
    <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name" />
    <input type="text" name="adress" placeholder="Enter Adress" v-model="restaurant.address" />
    <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact" />
    <button type="button" v-on:click="addRestaurant">Update new Restaurant</button>
</form>
</template>

<script>
import HeaderComponent from './HeaderComponent.vue';

export default {
    name: "UpdatePage",
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
    mounted() {
        let user = localStorage.getItem("user-info");

        if(!user) {
            this.$router.push({name: "SignUp"});
        }
    }
}
</script>

<style></style>