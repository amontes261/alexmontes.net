<template>
  <v-app dark >
    <v-main class="comingSoonContainer">
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<style>

.comingSoonContainer {
    background-color: black;
    background-image: url('/word_backgrounds/opaque/coming_soon.png');
    background-size: cover;
    background-position: center;
    display: grid;
    height: 100vh;
    place-items: center;
  }
  
</style>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
    }
  }
}
</script>
