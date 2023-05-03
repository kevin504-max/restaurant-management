<template>
<HeaderComponent />
<h1>Hi User, Welcome on Home Page!</h1>
</template>

<script>
import HeaderComponent from './HeaderComponent.vue';

export default {
    name: "HomePage",
    components: {
        HeaderComponent
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