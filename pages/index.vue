<template>
    <div v-if="false" :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'homeContainer-widescreen' : ''">
        <div class="homeContent">
            <div>
                <div :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'leftContent-widescreen' : 'topContent-tallscreen'">
                    <div class="portraitInnerContainer">
                        <img :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'portrait-widescreen' : 'portrait-tallscreen'" src="/home_photos/homePicture.jpg" />
                    </div>
                </div>
                <div :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'rightContent-widescreen' : 'bottomContent-tallscreen'">
                    <div :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'rightContentOuterContainer-widescreen' : 'bottomContentOuterContainer-tallscreen'">
                        <div :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'rightContentInnerContainer-widescreen' : 'bottomContentInnerContainer-tallscreen'">
                            <h2 class="nameHeader">
                                Alex Montes
                            </h2>
                            <div class="animatedTextContainer">
                                <div>
                                    <div class="typewrite" href="" data-period="2000" data-type='[ "Graduate Student", "Software Engineer", "Perfectionist" ]'>
                                        <span class="wrap" :class="$vuetify.theme.dark ? 'black' : 'white'"></span>
                                    </div>
                                </div>
                            </div>
                            <h3>
                                <i> Brooklyn, New York </i>
                            </h3>
                            <v-row class="mt-6">
                                <v-col v-if="$vuetify.breakpoint.width < mobileViewpointWidthTipover" cols="1" />
                                <v-col v-for="(icon, index) in homeSocialIcons" :key="index" cols="2">
                                    <a :href="icon.destination" target="_blank">
                                        <img :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'homeIcon-widescreen' : 'homeIcon-tallscreen'" :alt="icon.logo" :src="$vuetify.theme.dark ? icon.darkPath : icon.lightPath" />
                                    </a>
                                </v-col>
                                <v-col v-if="$vuetify.breakpoint.width < mobileViewpointWidthTipover" cols="3" />
                            </v-row>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    var TxtType = function(el, toRotate, period) {
        this.toRotate = toRotate;
        this.el = el;
        this.loopNum = 0;
        this.period = parseInt(period, 10) || 2000;
        this.txt = '';
        this.tick();
        this.isDeleting = false;
    };

    TxtType.prototype.tick = function() {
            setTimeout(() => {
            this.overlay = false;
        }, 1000);
        var i = this.loopNum % this.toRotate.length;
        var fullTxt = this.toRotate[i];

        if (this.isDeleting) {
            this.txt = fullTxt.substring(0, this.txt.length - 1);
        }
        else {
            this.txt = fullTxt.substring(0, this.txt.length + 1);
        }

        this.el.innerHTML = '<span class="wrap">'+this.txt+'</span>';

        var that = this;
        var delta = 130 - Math.random() * 100;

        if (this.isDeleting) {
            delta /= 4;
        }

        if (!this.isDeleting && this.txt === fullTxt) {
            delta = this.period;
            this.isDeleting = true;
        }
        else if (this.isDeleting && this.txt === '') {
            this.isDeleting = false;
            this.loopNum++;
            delta = 50;
        }

        setTimeout(function() {
            that.tick();
        }, delta);
    };

    export default {
        data () {
            this.$router.push('/comingSoon'); // remove when read
            /*return {
                mobileViewpointWidthTipover: 850,
                homeSocialIcons: [
                    { name: 'LinkedIn', darkPath: '/social_icons/darkMode/linkedin.png', lightPath: '/social_icons/lightMode/linkedin.png', destination: 'https://www.linkedin.com/in/amontes261/'},
                    { name: 'Discord', darkPath: '/social_icons/darkMode/discord.png', lightPath: '/social_icons/lightMode/discord.png', destination: 'https://discordapp.com/users/403355889253220352'},
                    { name: 'GitHub', darkPath: '/social_icons/darkMode/github.png', lightPath: '/social_icons/lightMode/github.png', destination: 'https://github.com/amontes261'},
                    { name: 'Instagram', darkPath: '/social_icons/darkMode/instagram.png', lightPath: '/social_icons/lightMode/instagram.png', destination: 'https://www.instagram.com/a.montes28/'},
                    // { name: 'Xbox', darkPath: '/social_icons/darkMode/xbox.png', lightPath: '/social_icons/lightMode/xbox.png', destination: 'https://account.xbox.com/en-us/profile?gamertag=TheMixxRemixx' },
                ]
            }*/
        },
        head() {
            return {
                title: "Home | AM",
                meta: [{
                    property: "og:title",
                    name: 'title',
                    content: 'Alex Montes\' Portfolio'
                }],
            };
        },
        mounted:function() {
            var elements = document.getElementsByClassName('typewrite');
            for (var i = 0; i < elements.length; i++) {
                var toRotate = elements[i].getAttribute('data-type');
                var period = elements[i].getAttribute('data-period');
                if (toRotate && toRotate.includes("]") ) {
                    new TxtType(elements[i], JSON.parse(toRotate), period);
                }
            }
            // INJECT CSS
            var css = document.createElement("style");
            css.type = "text/css";
            css.innerHTML = ".typewrite > .wrap { border-right: 0.17em solid cornflowerblue}";
            document.body.appendChild(css);
        }
    }
</script>

<style>
    /*  =====================
        GENERALIZED CSS BELOW 
        ===================== */
    .animatedTextContainer{
        width: 100%;
    }

    .black{
        color: black;
    }

    .centerTypewriterText{
        margin: 0 auto;
    }

    .homeContent{
        padding: auto;
        width: 100%;
        position: absolute;
        top: 52%;
        transform: translateY(-50%)
    }

    .nameHeader{
        font-size: 3.5em;
        font-weight: 700;
        text-transform: uppercase;
        line-height: 1.0;
        font-family: "Montserrat", Arial, Helvetica, sans-serif;
    }

    .portraitInnerContainer{
        text-align: center;
    }

    .white{
        color: white;
    }

    .wrap {
        white-space: nowrap; /* Keeps the content on a single line */
        text-decoration: none;
        font-family: 'Courier New', Courier, monospace;
        font-size: 2em;
        animation:
            cursorBlink 1s step-end infinite;
    }
    @keyframes cursorBlink {
        from, to { border-color: cornflowerblue }
        50% { border-color: transparent }
    }

    /*  ====================
        WIDESCREEN CSS BELOW 
        ==================== */

    .homeContainer-widescreen{
        display: flex;
        height: 100vh;
        justify-content: center;
    }

    .homeIcon-widescreen{
        width: 2.5vw;
    }

    .leftContent-widescreen{
        display: flex;
        width: 50%;
        float: left;
        padding: 20px;
        justify-content: center;
        align-items: center;
        height: 50vh;
    }

    .rightContentOuterContainer-widescreen{
        display: flex;
        align-items: center;
        width: 100%;
        vertical-align: middle;
        text-align: center;
    }

    .portrait-widescreen{
        width: 75%;
        border-radius: 30px;
    }

    .rightContent-widescreen{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 50%;
        float: right;
        padding: 20px;
        height: 50vh;
    }

    .rightContentInnerContainer-widescreen{
        text-align: left; /* Optional: Center the content horizontally within the inner div */
    }

    /*  ====================
        TALLSCREEN CSS BELOW 
        ==================== */

    .bottomContentOuterContainer-tallscreen{
        justify-content: center;
    }

    .bottomContent-tallscreen{
        width: 100%;
        text-align: center;
        padding: 20px;
    }

    .homeIcon-tallscreen{
        width: 5vw;
    }

    .portrait-tallscreen{
        margin-top: calc(10vh + 5vw);
        width: 50%;
        border-radius: 30px;
    }

    .bottomContentInnerContainer-tallscreen{
        text-align: center;
    }

    .topContent-tallscreen{
        text-align: center;
        width: 100%;
    }
</style>