<template>
<div class="nav">
    <a href="#" >Home</a>
    <a href="#" >Add Restaurant</a>
    <a href="#" >Update Restaurant</a>
    <a v-on:click="logout">Logout</a>
</div>
</template>

<script>
export default {
    name: "HeaderComponent",
    methods: {
        logout() {
            localStorage.clear();
            this.$router.push({name: "LoginPage"});
        }
    }
}
</script>

<style>
.nav {
    background-color: #333;
    overflow: hidden;
}
.nav a {
    float: left;
    color: #F2F2F2;
    padding: 16px 14px;
    text-align: center;
    font-size: 17px;
    text-decoration: none;
    transition: 0.5s;
}
.nav a:hover {
    background: #DDD;
    color: #333;
}
</style>