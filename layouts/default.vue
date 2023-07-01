<template>
    <v-app dark class="allAppUmbrella" fill-height fluid>
        <v-row>
            <v-col class="navPanel" :class="$vuetify.theme.dark ? 'navPanelDark' : 'navPanelLight'" cols="3">
                <div class="navPanelContainer"> <!-- centered -->
                    <div class="logoContainer">
                        <img v-if="$vuetify.theme.dark" class="pb-6" width="150" src="/logo_darkMode.png" />
                        <img v-if="!$vuetify.theme.dark" class="pb-6" width="150" src="/logo_lightMode.png" />
                    </div>
                    <div class="navContainer">
                        <div class="linkContainer">
                            <div class="linkParentDiv">
                                <router-link :class="this.$route.name == 'index' ? 'activeNavLink' : 'navLink'" to="/">
                                    Home
                                </router-link>
                            </div>
                            <div class="linkParentDiv">
                                <router-link :class="this.$route.name == 'about' ? 'activeNavLink' : 'navLink'" to="/about">
                                    About
                                </router-link>
                            </div>
                            <div class="linkParentDiv">
                                <router-link :class="this.$route.name == 'experience' ? 'activeNavLink' : 'navLink'" to="/experience">
                                    Experience
                                </router-link>
                            </div>
                            <div class="linkParentDiv">
                                <router-link :class="this.$route.name == 'projects' ? 'activeNavLink' : 'navLink'" to="/projects">
                                    Projects
                                </router-link>
                            </div>
                            <div class="linkParentDiv">
                                <router-link :class="this.$route.name == 'contact' ? 'activeNavLink' : 'navLink'" to="/contact">
                                    Contact
                                </router-link>
                            </div>
                        </div>
                    </div>
                    <div class="themeButtonContainer">
                        <v-btn :ripple="false" @click="$vuetify.theme.dark = !$vuetify.theme.dark" class="mt-9" v-bind:light="$vuetify.theme.dark" v-bind:dark="!$vuetify.theme.dark" small v-model="$vuetify.theme.dark" :color="$vuetify.theme.dark ? '#64B5F6' : 'black'"> {{ $vuetify.theme.dark ? "Light Mode" : "Dark Mode" }} </v-btn>
                    </div>
                    <div class="smallLinksContainer">
                        <div class="mt-6">
                            © 2023 Alex Montes
                        </div>
                        <div>
                            All rights reserved.
                        </div>
                        <div class="py-5">
                            Something look off? <a class="letMeKnowText" href="https://github.com/amontes261/mySite/issues" target="_blank">Let me know.</a>
                        </div>
                    </div>
                </div>
            </v-col>
            <v-col class="nuxtApp" cols="9">
                <v-main>
                    <Nuxt :class="$vuetify.theme.dark ? 'nuxtBodyDark': 'nuxtBodyLight'"/>
                </v-main>
            </v-col>
        </v-row>
    </v-app>
</template>

<style>
.activeNavLink{
    font-size: 200%;
    font-weight: 600;
    padding: 5%;
    text-decoration: none;
    padding-left: 0;
    opacity: 1;
    color: #5086d6;
    font-size: 225%;
}

.letMeKnowText{
    text-decoration: none;
}

.linkParentDiv{
    width: 100%;
}

.navLink{
    font-size: 200%;
    font-weight: 600;
    padding: 5%;
    text-decoration: none;
    padding-left: 0;
    opacity: 0.5;
    transition: 0.4s;
    color: #3874CB;
}

.navLink:hover {
    opacity: 1;
    color: cornflowerblue;
    font-size: 225%;
}

.navLink:active {
    color: #2256a3;
}

.navPanel{
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    top: 0;
    width: 450px;
    height: 100vh;
    position: fixed;
    top: 0;
}

.navPanelContainer{
    align-items: center;
}

.navPanelDark{
    background-color: black;
    transition: 0.4s;
}

.navPanelLight{
    background-color: white;
}

.nuxtApp{
    margin-left: 450px;
    height: 100vh;
}

.nuxtBodyDark{
    background-color: #121212;
    transition: 0.4s;
}

.nuxtBodyLight{
    background-color: #F5F5F5;
}

.smallLinksContainer{
    font-size: small;
}

.allAppUmbrella{
    font-family: "Mulish", Arial, Helvetica, sans-serif;
    background-color: cyan; /* for testing */
}

/* dw about below*/

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
