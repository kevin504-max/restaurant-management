<template>
<HeaderComponent />
<h1>Hi User, Welcome on Add Restaurant Page!</h1>
</template>

<script>
import HeaderComponent from './HeaderComponent.vue';

export default {
    name: "AddPage",
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