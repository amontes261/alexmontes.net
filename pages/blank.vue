<template>
    <div class="d-flex align-center justify-center pageOnTheWayContainer">
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
    .pageOnTheWayContainer{
        height: 100vh;
    }
</style>