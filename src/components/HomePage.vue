<template>
<HeaderComponent />
<h1>Hi {{ name }}, Welcome on Home Page!</h1>
<table border="1">
    <tr>
        <td>ID</td>
        <td>Name</td>
        <td>Contact</td>
        <td>Address</td>
        <td>Actions</td>
    </tr>
    <tr v-for="item in restaurant" :key="item.id">
        <td>{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.contact }}</td>
        <td>{{ item.address }}</td>
        <td>
            <router-link :to="'/update/' + item.id">Update</router-link>
            <button v-on:click="deleteRestaurant(item.id)">Delete</button>
        </td>
    </tr>
</table>
</template>

<script>
import HeaderComponent from './HeaderComponent.vue';
import axios from 'axios';

export default {
    name: "HomePage",
    data () {
        return {
            name: "",
            restaurant: []
        }
    },      
    components: {
        HeaderComponent
    },
    methods: {
        async deleteRestaurant(id) {
            let result = await axios.delete(`http://localhost:3000/restaurant/${id}`);

            if(result.status == 200) {
                this.loadData();
            }
        },
        async loadData() {
            let user = localStorage.getItem("user-info");
            this.name = JSON.parse(user).name;
            
            if(!user) {
                this.$router.push({name: "SignUp"});
            }

            let result = await axios.get("http://localhost:3000/restaurant");
            this.restaurant = result.data;
        },
    },
    async mounted() {
        this.loadData();
    }
}
</script>

<style>
    td {
        width: 160px;
        height: 40px;
        text-align: center;
    }
</style>