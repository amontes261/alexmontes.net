<template>
    <div class="d-flex align-center justify-center pageContainer">
        <img v-if="$vuetify.theme.dark" width="50" src="/logo_darkMode.png" />
    </div>
</template>

<script>
    

    export default {
        data () {
            window.location.replace("https://alexmontes.net/resume.pdf"); 
        },
        head() {
            return {
                title: "Resume | AM"
            };
        }
    }
</script>

<style>
    .pageContainer{
        height: 100vh;
    }
</style>
