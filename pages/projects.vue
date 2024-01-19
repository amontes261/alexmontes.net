<template>
    <div :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'pageOnTheWayContainer-widescreen' : 'pageOnTheWayContainer-tallscreen'" class="d-flex align-center justify-center">
        <v-card elevation="15" outlined class="d-flex align-center justify-center text-center"  min-height="250" width="85%">
            <v-card-text class>
                <v-icon class="pageOnTheWayIcon py-6" color="red" x-large> mdi-wrench-clock </v-icon>
                <div :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'pageOnTheWayHeader-widescreen' : 'pageOnTheWayHeader-tallscreen'" class="pa-5">
                    Page on the way...
                </div>
                <div :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'pageOnTheWaySubheader-widescreen' : 'pageOnTheWaySubheader-tallscreen'" class="pa-5 mx-10">
                    You've made it to the right place, but this place doesn't exist just yet. <br v-if="$vuetify.breakpoint.width >= mobileViewpointWidthTipover">
                    Check back soon to see if this page's been completed.
                </div>
                <div class="d-flex justify-center">
                    <button @click="$router.go(-1)" class="backButton mt-5" :class="$vuetify.theme.dark ? 'backButton-darkMode' : 'backButton-lightMode'" role="button"> <strong> Back </strong> </button>
                </div>
            </v-card-text>
        </v-card>
    </div>
</template>

<script>
    export default {
        data () {
            return{
                mobileViewpointWidthTipover: 850,
            }
        },
        head() {
            return {
                title: "Projects | AM"
            };
        }
    }
</script>

<style>
    .pageOnTheWayIcon{
        font-size: 20vh;
    }

    .backButton {
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
        width: 40%;
        will-change: transform;
    }

    .backButton:disabled {
        pointer-events: none;
    }

    .backButton:hover {
        transform: translateY(-3px);
    }

    .backButton:active {
        box-shadow: none;
        transform: translateY(0);
    }

    .backButton-darkMode {
        background-color: black;
        border: 2px solid #1A1A1A;
        color: #FFFFFF;
        transition: 0.4s;
    }

    .backButton-darkMode:hover {
        box-shadow: rgba(255, 255, 255, 0.25) 0 8px 15px;
    }

    .backButton-lightMode {
        background-color: white;
        border: 2px solid #e9e9e9;
        color: black;
        transition: 0.4s;
    }

    .backButton-lightMode:hover {
        box-shadow: rgba(0, 0, 0, 0.25) 0 8px 15px;
    }


    /* WIDE */

    .pageOnTheWayContainer-widescreen{
        height: 100vh;
    }

    .pageOnTheWayHeader-widescreen{
        color: red;
        font-size: 4vw;
        text-transform: uppercase;
        font-family: 'Montserrat', Arial, Helvetica, sans-serif;
        font-weight: 600;
        text-align: center;
    }

    .pageOnTheWaySubheader-widescreen{
        font-size: 1.25vw;
        text-align: center;
        line-height: 1.2;
    }

    /* TALL */

    .pageOnTheWayContainer-tallscreen{
        height: 85vh;
    }

    .pageOnTheWayHeader-tallscreen{
        color: red;
        font-size: 6vw;
        text-transform: uppercase;
        font-family: 'Montserrat', Arial, Helvetica, sans-serif;
        font-weight: 600;
        text-align: center;
    }

    .pageOnTheWaySubheader-tallscreen{
        font-size: 3.5vw;
        text-align: center;
    }
</style>