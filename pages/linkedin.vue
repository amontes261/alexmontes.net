<template>
    <div class="d-flex align-center justify-center pageContainer">
        <img v-if="$vuetify.theme.dark" width="50" src="/logo_darkMode.png" />
    </div>
</template>

<script>
    

    export default {
        data () {
            window.location.replace("https://www.linkedin.com/in/amontes261/"); 
        },
        head() {
            return {
                title: "LinkedIn | AM"
            };
        }
    }
</script>

<style>
    .pageContainer{
        height: 100vh;
    }
</style>
