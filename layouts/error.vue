<template>
  <v-app dark>
    <div>
        <template>
            <div :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'errorPageContainer-widescreen' : 'errorPageContainer-tallscreen'">
                <div v-if="error.statusCode === 404" :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'largeNumberBackgroundContainer-widescreen' : 'largeNumberBackgroundContainer-tallscreen'">
                    404
                </div>
                <div v-else :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'largeNumberBackgroundContainer-widescreen' : 'largeNumberBackgroundContainer-tallscreen'">
                    500
                </div>
                <div class="error404Container">
                    <div class="text-center d-flex flex-column align-center justify-center contentContainer">
                        <div v-if="error.statusCode === 404" class="mx-5" :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'headerContent404-widescreen' : 'headerContent404-tallscreen'">
                            Page not found...
                        </div>
                        <div v-else class="mx-5" :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'headerContent500-widescreen' : 'headerContent500-tallscreen'">
                            Something Went Wrong
                        </div>
                        <div class="mx-5" :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'subheaderContent-widescreen' : 'subheaderContent-tallscreen'">
                            <div v-if="error.statusCode === 404" class="my-8">
                                We looked long & hard for the page you're trying to visit, but couldn't find it.
                            </div>
                            <div v-else class="mt-8">
                                Sorry, seems something went wrong. Please <a class="letMeKnowText" href="https://github.com/amontes261/mySite/issues" target="_blank"> let me know</a> how you got here so it won't happen again.
                            </div>
                        </div>
                        <div v-if="error.statusCode === 404" class="mx-5" :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'ifErrorText-widescreen' : 'ifErrorText-tallscreen'">
                            <i> If you believe this' an error, please <a class="letMeKnowText" href="https://github.com/amontes261/mySite/issues" target="_blank"> let me know</a>. </i>
                        </div>
                        <div class="mt-10 themeButtonContainer">
                            <router-link to="/">
                                <button class="goHomeButton mt-5" :class="$vuetify.theme.dark ? 'goHomeButton-darkMode' : 'goHomeButton-lightMode'" role="button"> <strong> Go Home </strong> </button>
                            </router-link>
                        </div>
                    </div>
                </div>
            </div>
        </template>
    </div>    
  </v-app>
</template>

<script>
    export default {
        name: 'EmptyLayout',
        layout: 'empty',
        props: {
            error: {
                type: Object,
                default: null
            }
        },
        data () {
            return {
                mobileViewpointWidthTipover: 850,
            }
        },
        head() {
            return {
                title: this.error.statusCode === 404 ? 'Page Not Found | AM': 'Unexpected Error | AM'
            };
        }
    }
</script>

<style>
    .errorPageContainer-widescreen{
        height: 100vh;
    }

    .error404Container{
        display: flex;
        height: 100vh;
        justify-content: center;
        position: relative;
    }


    .goHomeButton {
        appearance: none;
        border-radius: 15px;
        box-sizing: border-box;
        cursor: pointer;
        display: inline-block;
        font-family: Roobert,-apple-system,BlinkMacSystemFont,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol";
        font-size: 26px;
        font-weight: 600;
        line-height: normal;
        margin: 0;
        min-height: 70px;
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

    .goHomeButton:disabled {
        pointer-events: none;
    }

    .goHomeButton:hover {
        transform: translateY(-5px);
    }

    .goHomeButton:active {
        box-shadow: none;
        transform: translateY(0);
    }

    .goHomeButton-darkMode {
        background-color: black;
        border: 2px solid #1A1A1A;
        color: #FFFFFF;
        transition: 0.4s;
    }

    .goHomeButton-darkMode:hover {
        box-shadow: rgba(255, 255, 255, 0.25) 0 8px 15px;
    }

    .goHomeButton-lightMode {
        background-color: white;
        border: 2px solid #e9e9e9;
        color: black;
        transition: 0.4s;
    }

    .goHomeButton-lightMode:hover {
        box-shadow: rgba(0, 0, 0, 0.25) 0 8px 15px;
    }

    .headerContent404-widescreen{
        font-size: 5.5vw;
        font-weight: 700;
        line-height: 0.85;
        font-family: 'Montserrat', Arial;
        text-transform: uppercase;
    }

    .headerContent500-widescreen{
        color: red;
        font-size: 4.25vw;
        font-weight: 700;
        line-height: 0.85;
        font-family: 'Montserrat', Arial;
        text-transform: uppercase;
    }

    .ifErrorText-widescreen{
        font-size: 1.25vw;
    }

    .largeNumberBackgroundContainer-widescreen{
        position: absolute;
        opacity: 0.02;
        font-size: 28vw;
        line-height: 1;
        animation: breathingEffect 6s infinite;
    }
    
    @keyframes breathingEffect {
        0% { opacity: 0.02; }
        55% { opacity: 0.02; }
        77.5% { opacity: 0.12; }
        80% { opacity: 0.12; }
        100% { opacity: 0.02; }
    }

    .subheaderContent-widescreen{
        font-size: 1.5vw;
    }




    /* TALL  */

    .errorPageContainer-tallscreen{
        height: 85vh;
    }

    .headerContent404-tallscreen{
        font-size: 8vw;
        font-weight: 700;
        line-height: 0.85;
        font-family: 'Montserrat', Arial;
        text-transform: uppercase;    
    }

    .headerContent500-tallscreen{
        color: red;
        font-size: 10vw;
        font-weight: 700;
        line-height: 0.85;
        font-family: 'Montserrat', Arial;
        text-transform: uppercase;    
    }

    .ifErrorText-tallscreen{
        font-size: 3.5vw;
    }

    .largeNumberBackgroundContainer-tallscreen{
        position: absolute;
        opacity: 0.02;
        font-size: 45vw;
        line-height: 1;
        animation: breathingEffect 6s infinite;
    }

    .subheaderContent-tallscreen{
        font-size: 4.5vw;
    }
</style>
