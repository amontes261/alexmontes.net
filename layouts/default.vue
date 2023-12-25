<template>
    <v-app dark fill-height fluid>
        <div class="allAppUmbrella" :class="$vuetify.theme.dark ? 'blackFade' : 'whiteFade'">
            <!-- BEGIN SIDEBAR IMPLEMENTATION -->
            <!-- If vw exceeds a certain minimum (mobileViewpointWidthTipover), the below renders. -->
            <v-row class="pa-0" v-if="$route.name != 'blank' && $vuetify.breakpoint.width >= mobileViewpointWidthTipover">
                <v-col class="sideBar" :class="$vuetify.theme.dark ? 'blackFade' : 'whiteFade'" cols="3">
                    <div class="align-items-center">
                        <div>
                            <router-link to="/">
                                <img v-if="$vuetify.theme.dark" class="pb-6" width="125" src="/logo_darkMode.png" />
                                <img v-if="!$vuetify.theme.dark" class="pb-6" width="125" src="/logo_lightMode.png" />
                            </router-link>
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
                            <button @click="$vuetify.theme.dark = !$vuetify.theme.dark" class="themebutton mt-5" :class="$vuetify.theme.dark ? 'themebutton-darkMode' : 'themebutton-lightMode'" role="button"> <strong> {{ $vuetify.theme.dark ? "Light Mode" : "Dark Mode" }} </strong> </button>
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
            <div v-else-if="$route.name == 'blank' && $vuetify.breakpoint.width >= mobileViewpointWidthTipover" class="nuxtAppNoSideBarContainer">
                <v-main>
                    <Nuxt :class="$vuetify.theme.dark ? 'softBlackFade': 'softWhiteFade'"/>
                </v-main>
            </div>

            <!-- END SIDEBAR IMPLEMENTATION -->
            <!-- BEGIN NAVBAR IMPLEMENTATION -->
            <!-- If vw DOES NOT exceed a certain minimum (mobileViewpointWidthTipover), the below renders. -->
            
            <div v-else-if="$vuetify.breakpoint.width < mobileViewpointWidthTipover && !overlay">
                <div v-if="$route.name != 'blank'" class="navBarContainer" :class="$vuetify.theme.dark ? 'blackFade' : 'whiteFade'">
                    <div class="navBarContents">
                        <div class="navBarLogoContainer">
                            <router-link to="/">
                                <img v-if="$vuetify.theme.dark" height="75" src="/logo_darkMode.png" />
                                <img v-if="!$vuetify.theme.dark" height="75" src="/logo_lightMode.png" />
                            </router-link>
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
                        <div>
                            <v-btn plain :ripple=false @click="$vuetify.theme.dark = !$vuetify.theme.dark" icon x-large>
                                <div class="navBarThemeButton" />
                            </v-btn>
                        </div>
                        <div v-if="$vuetify.breakpoint.width < navBarWidthTipover">
                            <v-menu rounded transition="slide-x-reverse-transition" top open-on-hover close-on-click open-delay="100">
                                <template v-slot:activator="{ on, attrs }">
                                    <v-btn icon x-large v-bind="attrs" v-on="on" >
                                        <v-icon>mdi-menu</v-icon>
                                    </v-btn>
                                </template>

                                <v-card class="pa-5 listLinkContainer">
                                    <v-list class="navList">
                                        <v-list-item v-for="(path, index) in navRoutes" :key="index">
                                            <router-link :to="path.to" class="menuLink">
                                                <v-list-item-content>
                                                    <v-list-item-title style="font-size: 150%;"> {{ path.title }} </v-list-item-title>
                                                </v-list-item-content>
                                            </router-link>
                                            <v-list-item-icon>
                                                <v-icon v-text="path.icon" />
                                            </v-list-item-icon>
                                        </v-list-item>
                                    </v-list>
                                </v-card>
                            </v-menu>
                        </div>
                    </div>
                </div>
                <div class="nuxtAppNavBarContainer">
                    <Nuxt :class="$vuetify.theme.dark ? 'softBlackFade': 'softWhiteFade'"/>
                </div>
            </div>
        </div>
        <v-overlay v-if="$route.name != 'blank'" :opacity="1" :value="overlay">
            <div class="loadBar" />
        </v-overlay>
    </v-app>
</template>

<style>
    .test{
        background-color: #121212;
    }
    /*  =====================
        GENERALIZED CSS BELOW
        ===================== */
        
    /*  ====================
        WIDESCREEN CSS BELOW
        ==================== */

    .currentRouteSideBarLink{
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

    /*  ====================
        TALLSCREEN CSS BELOW
        ==================== */
    
    .currentRouteNavBarLink{
        font-size: 140%;
        font-weight: 600;
        padding: 5%;
        text-decoration: none;
        opacity: 1;
        color: #5086d6;
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

    

    .listLinkContainer{
        width: 100%;
        align-items: right;
        align-content: right;
        justify-content: right;
    }

    .sideBarLinkDiv{
        width: 100%;
    }

    .menuLink{
        font-size: 150%;
        font-weight: 600;
        text-decoration: none;
        margin-left: auto; 
        margin-right: 0;
        opacity: 0.6;
        transition: 0.4s;
        color: white;
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

    .navBarThemeButton {
        box-sizing: border-box;
        position: relative;
        display: block;
        transform: scale(var(--ggs,1));
        border:2px solid;
        border-radius:100px;
        width:20px;
        height:20px;
    }

    .navBarThemeButton::after, .navBarThemeButton::before {
        content: "";
        box-sizing: border-box;
        position: absolute;
        display: block
    }

    .navBarThemeButton::before {
        border:5px solid;
        border-top-left-radius:100px;
        border-bottom-left-radius:100px;
        border-right: 0;
        width:9px;
        height:18px;
        top:-1px;
        left:-1px
    }

    .navBarThemeButton::after {
        border:4px solid;
        border-top-right-radius:100px;
        border-bottom-right-radius:100px;
        border-left: 0;
        width:4px;
        height:8px;
        right:4px;
        top:4px
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
        min-height: 100vh;
        position: fixed;
        top: 0;
    }

    .themebutton {
        appearance: none;
        border-radius: 15px;
        box-sizing: border-box;
        cursor: pointer;
        display: inline-block;
        font-family: Roobert,-apple-system,BlinkMacSystemFont,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol";
        font-size: 16px;
        font-weight: 600;
        line-height: normal;
        margin: 0;
        min-height: 60px;
        min-width: 0;
        outline: none;
        padding: 16px 24px;
        text-align: center;
        text-decoration: none;
        transition: all 300ms cubic-bezier(.23, 1, 0.32, 1);
        user-select: none;
        -webkit-user-select: none;
        touch-action: manipulation;
        width: 100%;
        will-change: transform;
    }

    .themebutton:disabled {
        pointer-events: none;
    }

    .themebutton:hover {
        transform: translateY(-5px);
    }

    .themebutton:active {
        box-shadow: none;
        transform: translateY(0);
    }

    .themebutton-darkMode {
        background-color: black;
        border: 2px solid #1A1A1A;
        color: #FFFFFF;
        transition: 0.4s;
    }

    .themebutton-darkMode:hover {
        box-shadow: rgba(255, 255, 255, 0.25) 0 8px 15px;
    }

    .themebutton-lightMode {
        background-color: white;
        border: 2px solid #e9e9e9;
        color: black;
        transition: 0.4s;
    }

    .themebutton-lightMode:hover {
        box-shadow: rgba(0, 0, 0, 0.25) 0 8px 15px;
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

    .nuxtAppNoSideBarContainer{
        padding: 0;
        min-height: 100vh;
    }

    .nuxtAppSideBarContainer{
        margin-left: 25vw;
        padding: 0;
        min-height: 100vh;
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
        font-size: 1vw;
        font-weight: 900;
        font-family: Arial, Helvetica, sans-serif;
    }

    .allAppUmbrella{
        font-family: "Mulish", Arial, Helvetica, sans-serif;
        min-width: 100vw;
        min-height: 100vh;
    }

    /* loading contents */

    @keyframes loadbar {
        0%,to { left: 0;  right: 80% }
        25%,75% { left: 0; right: 0 }
        50% { left: 80%; right: 0 }
    }
    .loadBar,
    .loadBar::before {
        display: block;
        box-sizing: border-box;
        height: 8px
    }
    .loadBar {
        position: relative;
        transform: scale(var(--ggs,1));
        width: 50px
    }
    .loadBar::before {
        content: "";
        position: absolute;
        border-radius: 8px;
        background: cornflowerblue;
        animation: loadbar 2s cubic-bezier(0,0,.58,1) infinite
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
        data () {
            return {
                mobileViewpointWidthTipover: 850,
                navBarWidthTipover: 750,
                navRoutes: [
                    { title: 'Home', to: '/', icon: 'mdi-home' },
                    { title: 'About', to: 'about', icon: 'mdi-information' },
                    { title: 'Experience', to: 'experience', icon: 'mdi-account-school' },
                    { title: 'Projects', to: 'projects', icon: 'mdi-hammer-wrench' },
                    { title: 'Contact', to: 'contact', icon: 'mdi-email' },
                ],
                overlay: true
            }
        },
        head() {
            return {
                title: "Welcome | AM"
            };
        },
        mounted() {
            setTimeout(() => {
                this.overlay = false;
            }, 750);
        }
    }
</script>
