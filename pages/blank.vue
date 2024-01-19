<template>
    <div class="d-flex align-center justify-center pageContainer">
        <img v-if="$vuetify.theme.dark" width="75" src="/logo_darkMode.png" />
    </div>
</template>

<script>
    export default {
        data () {
        },
        head() {
            return {
                title: "BLANK | AM"
            };
        }
    }
</script>

<style>
    .pageContainer{
        height: 100vh;
    }
</style>