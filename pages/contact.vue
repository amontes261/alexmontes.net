<template>
    <div class="contactContainer">
        <div class="text-center d-flex flex-column align-center justify-center contentContainer">
            <div class="mx-5" :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'headerContent-widescreen' : 'headerContent-tallscreen'">
                Let's Connect.
            </div>
            <div class="mx-8 mt-10" :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'subheaderContent-widescreen' : 'subheaderContent-tallscreen'">
                The best ways to get in contact with me are listed here:
            </div>
            <div>
                <v-row class="mt-10 contactIcons">
                    <v-col v-for="(icon, index) in contactIcons" :key="index" class="contactLink" cols="3">
                        <a :href="icon.destination" target="_blank">
                            <img :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'contactIcon-widescreen' : 'contactIcon-tallscreen'" :alt="icon.logo" :src="$vuetify.theme.dark ? icon.darkPath : icon.lightPath" />
                        </a>
                    </v-col>
                </v-row>
            </div>
            <div class="mt-15" :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'noticeProblemText-widescreen' : 'noticeProblemText-tallscreen'">
                Notice a problem with my site? <br v-if="$vuetify.breakpoint.width < mobileViewpointWidthTipover"> <a class="issueInsteadText" href="https://github.com/amontes261/mySite/issues" target="_blank"> Leave me a GitHub Issue instead.</a>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                mobileViewpointWidthTipover: 850,
                contactIcons: [
                    { name: 'LinkedIn', darkPath: '/social_icons/darkMode/linkedin.png', lightPath: '/social_icons/lightMode/linkedin.png', destination: 'https://www.linkedin.com/in/amontes261/'},
                    { name: 'Email', darkPath: '/social_icons/darkMode/email.png', lightPath: '/social_icons/lightMode/email.png', destination: 'mailto:amontes261@gmail.com'},
                    { name: 'Phone', darkPath: '/social_icons/darkMode/phone.png', lightPath: '/social_icons/lightMode/phone.png', destination: 'tel:9172832236'},
                    { name: 'Discord', darkPath: '/social_icons/darkMode/discord.png', lightPath: '/social_icons/lightMode/discord.png', destination: 'https://discordapp.com/users/403355889253220352'}
                ],
            }
        },
        head() {
            return {
                title: "Contact | AM",
                meta: {
                    property: "og:title",
                    name: 'title',
                    content: 'Get in Contact - Alex Montes'
                },
            };
        }
    }
</script>

<style>
    .contactContainer{
        display: flex;
        height: 100vh;
        justify-content: center;
    }

    .contactIcon-widescreen{
        width: 5vw;
        margin: 0 2vw;
        animation: contactIconsFade 2s;
    }

    .contactIcons{
        animation: primaryFade 2s;
    }
    
    @keyframes primaryFade {
        0% { opacity: 0; }
        50% { opacity: 0; }
        75% { opacity: 100; }
    }

    .contentContainer{

    }

    .noticeProblemText-widescreen{
        font-size: 1.2vw;
        animation: noticeProblemTextFade 4.75s;
    }

    @keyframes noticeProblemTextFade {
        0% { opacity: 0;}
        83% { opacity: 0;}
        100% { opacity: 100;}
    }

    .headerContent-widescreen{
        font-size: 6vw;
        font-weight: 700;
        line-height: 0.85;
        font-family: 'Montserrat', Arial;
        text-transform: uppercase;
    }

    .issueInsteadText{
        text-decoration: none;
    }

    .subheaderContent-widescreen{
        font-size: 1.5vw;
        font-family: 'Montserrat', Arial;
        animation: primaryFade 2s
    }

    /* TALL */

    .contactIcon-tallscreen{
        width: 12.5vw;
        margin: 0 2vw;
        animation: contactIconsFade 2s;
    }

    .headerContent-tallscreen{
        font-size: 10vw;
        font-weight: 700;
        line-height: 0.85;
        font-family: 'Montserrat', Arial;
        text-transform: uppercase;
    }

    .noticeProblemText-tallscreen{
        font-size: 3.5vw;
        animation: noticeProblemTextFade 4.75s;
    }

    .subheaderContent-tallscreen{
        font-size: 5vw;
        font-family: 'Montserrat', Arial;
        animation: primaryFade 2s
    }

</style>