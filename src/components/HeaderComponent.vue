<template>
<div class="nav">
    <a href="#" >Home</a>
    <a href="#" >Add Restaurant</a>
    <a href="#" >Update Restaurant</a>
    <a href="#" >Logout</a>
</div>
</template>

<script>
export default {
    name: "HeaderComponent"
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