<template>
    <v-app dark class="allAppUmbrella" fill-height fluid>
        <!-- BEGIN SIDEBAR IMPLEMENTATION -->
        <!-- If vw exceeds a certain minimum (mobileViewpointWidthTipover), the below renders. -->
        <v-row class="pa-0" v-if="$vuetify.breakpoint.width >= mobileViewpointWidthTipover">
            <v-col class="sideBar" :class="$vuetify.theme.dark ? 'blackFade' : 'whiteFade'" cols="3">
                <div class="align-items-center">
                    <div>
                        <img v-if="$vuetify.theme.dark" class="pb-6" width="150" src="/logo_darkMode.png" />
                        <img v-if="!$vuetify.theme.dark" class="pb-6" width="150" src="/logo_lightMode.png" />
                    </div>
                    <div>
                        <div>
                            <div class="sideBarLinkDiv">
                                <router-link :class="this.$route.name == 'index' ? 'currentRouteSideBarLink' : 'sideBarLink'" to="/">
                                    Home
                                </router-link>
                            </div>
                            <div class="sideBarLinkDiv">
                                <router-link :class="this.$route.name == 'about' ? 'currentRouteSideBarLink' : 'sideBarLink'" to="/about">
                                    About
                                </router-link>
                            </div>
                            <div class="sideBarLinkDiv">
                                <router-link :class="this.$route.name == 'experience' ? 'currentRouteSideBarLink' : 'sideBarLink'" to="/experience">
                                    Experience
                                </router-link>
                            </div>
                            <div class="sideBarLinkDiv">
                                <router-link :class="this.$route.name == 'projects' ? 'currentRouteSideBarLink' : 'sideBarLink'" to="/projects">
                                    Projects
                                </router-link>
                            </div>
                            <div class="sideBarLinkDiv">
                                <router-link :class="this.$route.name == 'contact' ? 'currentRouteSideBarLink' : 'sideBarLink'" to="/contact">
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
                            © 2023 All rights reserved.
                        </div>
                        <div class="py-5">
                            Something look off? <a class="letMeKnowText" href="https://github.com/amontes261/mySite/issues" target="_blank">Let me know.</a>
                        </div>
                    </div>
                </div>
            </v-col>
            <v-col class="nuxtAppSideBarContainer" cols="9">
                <v-main>
                    <Nuxt :class="$vuetify.theme.dark ? 'softBlackFade': 'softWhiteFade'"/>
                </v-main>
            </v-col>
        </v-row>

        <!-- END SIDEBAR IMPLEMENTATION -->
        <!-- BEGIN NAVBAR IMPLEMENTATION -->
        <!-- If vw DOES NOT exceed a certain minimum (mobileViewpointWidthTipover), the below renders. -->
        
        <div v-if="$vuetify.breakpoint.width < mobileViewpointWidthTipover">
            <div class="navBarContainer">
                <div class="navBarContents">
                    <div class="navBarLogoContainer">
                        <img v-if="$vuetify.theme.dark" height="50" src="/logo_darkMode.png" />
                        <img v-if="!$vuetify.theme.dark" height="50" src="/logo_lightMode.png" />
                    </div>
                    <div style="width:100%;" />

                    <!-- BEGIN EXPANDED NAVBAR LINKS IMPLEMENTATION -->
                    <!-- If vw exceeds a certain minimum (navBarWidthTipover), the below renders. -->
                    <div v-if="$vuetify.breakpoint.width >= navBarWidthTipover" class="expandedNavBarLinkContainer">
                        <div class="expandedNavBarLink">
                            <router-link :class="this.$route.name == 'index' ? 'currentRouteNavBarLink' : 'navBarLink'" to="/">
                                Home
                            </router-link>
                        </div>
                        <div class="expandedNavBarLink">
                            <router-link :class="this.$route.name == 'about' ? 'currentRouteNavBarLink' : 'navBarLink'" to="/about">
                                About
                            </router-link>
                        </div>
                        <div class="expandedNavBarLink">
                            <router-link :class="this.$route.name == 'experience' ? 'currentRouteNavBarLink' : 'navBarLink'" to="/experience">
                                Experience
                            </router-link>
                        </div>
                        <div class="expandedNavBarLink">
                            <router-link :class="this.$route.name == 'projects' ? 'currentRouteNavBarLink' : 'navBarLink'" to="/projects">
                                Projects
                            </router-link>
                        </div>
                        <div class="expandedNavBarLink">
                            <router-link :class="this.$route.name == 'contact' ? 'currentRouteNavBarLink' : 'navBarLink'" to="/contact">
                                Contact
                            </router-link>
                        </div>
                    </div>

                    <!-- END EXPANDED NAVBAR LINKS IMPLEMENTATION -->
                    <!-- BEGIN COMPACT NAVBAR LINKS IMPLEMENTATION -->
                    <!-- If vw DOES NOT exceed a certain minimum (navBarWidthTipover), the below renders. -->
                    <div v-if="$vuetify.breakpoint.width < navBarWidthTipover">
                        <v-menu top close-on-click>
                            <template v-slot:activator="{ on, attrs }">
                                <v-btn icon x-large v-bind="attrs" v-on="on" >
                                    <v-icon>mdi-menu</v-icon>
                                </v-btn>
                            </template>
                            <v-list right>
                                <div class="text-right listLinkContainer">
                                    <div v-for="(path, index) in navRoutes" :key="index">
                                        <v-list-item-content>
                                            <router-link :to="path.to" class="menuLink">
                                                {{ path.title }}
                                            </router-link>
                                        </v-list-item-content>
                                        
                                    </div>
                                </div>
                            </v-list>
                        </v-menu>
                    </div>
                </div>
            </div>
            <div class="nuxtAppNavBarContainer">
                <Nuxt class="nuxtBodyNavBar" :class="$vuetify.theme.dark ? 'softBlackFade': 'softWhiteFade'"/>
            </div>
        </div>
    </v-app>
</template>

<style>
    .currentRouteNavBarLink{
        font-size: 140%;
        font-weight: 600;
        padding: 5%;
        text-decoration: none;
        opacity: 1;
        color: #5086d6;
    }

    .currentRouteSideBarLink{
        font-weight: 600;
        padding: 5%;
        text-decoration: none;
        padding-left: 0;
        opacity: 1;
        color: #5086d6;
        font-size: 225%;
    }

    .expandedNavBarLink{
        display: flex;
        margin: 0 5%;
        text-align: center;
        align-items: center;
    }

    .expandedNavBarLinkContainer{
        display: flex;
        justify-content: right;
    }

    .letMeKnowText{
        text-decoration: none;
    }

    .listLinkContainer{
        width: 100%;
    }

    .sideBarLinkDiv{
        width: 100%;
    }

    .menuLink{
        font-size: 150%;
        font-weight: 600;
        text-decoration: none;
        opacity: 0.6;
        transition: 0.4s;
        color: #3874CB;
    }

    .menuLink:hover {
        opacity: 1;
        color: cornflowerblue;

    }

    .menuLink:active {
        color: #2256a3;
    }

    .navBarContainer{
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        top: 0;
        height: 15vh;
        width: 100vw;
        position: sticky;
        z-index: 10;
        top: 0;
        background-color: black;
    }

    .navBarContents{
        display: flex;
        width: 100%;
        align-items: center;
        padding: 20px 40px;
    }

    .navBarLink{
        font-size: 125%;
        font-weight: 600;
        text-decoration: none;
        opacity: 0.5;
        transition: 0.4s;
        color: #3874CB;
    }


    .navBarLink:hover {
        opacity: 1;
        color: cornflowerblue;
        font-size: 140%;
    }

    .navBarLink:active {
        color: #2256a3;
    }

    .navBarLogoContainer{
        
    }

    .sideBarLink{
        font-size: 200%;
        font-weight: 600;
        padding: 5%;
        text-decoration: none;
        padding-left: 0;
        opacity: 0.5;
        transition: 0.4s;
        color: #3874CB;
    }

    .sideBarLink:hover {
        opacity: 1;
        color: cornflowerblue;
        font-size: 225%;
    }

    .sideBarLink:active {
        color: #2256a3;
    }

    .sideBar{
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center; /* also looks nice w/o this... */
        
        height: 100vh;
        position: fixed;
        top: 0;
    }

    .align-items-center{
        align-items: center;
    }

    .blackFade{
        background-color: black;
        transition: 0.4s;
    }

    .whiteFade{
        background-color: white;
        transition: 0.4s;
    }

    .nuxtAppNavBarContainer{
        width: 100vw;
        background-color: black;
    }

    .nuxtAppSideBarContainer{
        margin-left: 25vw;
        padding: 0;
        height: 100vh;
    }


    .nuxtBodyNavBar{
        
    }

    .nuxtBodySidePanel{

    }

    .softBlackFade{
        background-color: #121212;
        transition: 0.4s;
    }

    .softWhiteFade{
        background-color: #F5F5F5;
        transition: 0.4s;
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
        mobileViewpointWidthTipover: 1250,
        navBarWidthTipover: 750,
        navRoutes: [
            { title: 'Home', to: '/' },
            { title: 'About', to: 'about' },
            { title: 'Experience', to: 'experience' },
            { title: 'Projects', to: 'projects' },
            { title: 'Contact', to: 'contact' },
        ],
    }
  }
}
</script>
