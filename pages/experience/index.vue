<template>
    <div class="experienceContainer">
        <div class="experienceContents">
            <div :class="$vuetify.breakpoint.width >= mobileViewpointWidthTipover ? 'pt-15 pb-5 bigHeader-widescreen' : 'pt-15 pb-10 bigHeader-tallscreen'">
                {{ experienceShown == 'W' ? 'Workplace' : 'School' }} Experience
            </div>
            <div v-if="$vuetify.breakpoint.width >= mobileViewpointWidthTipover" class="shownExperienceToggleContainer-widescreen align-center justify-center pb-5">
                <div @click="experienceShown = 'W'; experienceToggle = false;" class="pr-2 experienceToggleOption-widescreen align-right" :class="experienceShown == 'W' ? 'switchOptionTarget-widescreen' : 'switchOptionSecondary-widescreen'">
                    Work
                </div>
                <div class="align-center justify-center" min-width="100">
                    <v-switch v-model="experienceToggle" @click="toggleExperienceShown()" color="#5086d6" :ripple=false inset />
                </div>
                <div @click="experienceShown = 'S'; experienceToggle = true;" class="experienceToggleOption-widescreen" :class="experienceShown == 'S' ? 'switchOptionTarget-widescreen' : 'switchOptionSecondary-widescreen'">
                    School
                </div>
            </div>
            <div v-else class="align-center justify-center shownExperienceToggleContainer-tallscreen">
                <div @click="experienceShown = 'W';" class="experienceToggleOption-tallscreen" :class="experienceShown == 'W' ? 'switchOptionTarget-tallscreen' : 'switchOptionSecondary-tallscreen'">
                    Work
                </div>
                <div @click="experienceShown = 'S';" class="experienceToggleOption-tallscreen" :class="experienceShown == 'S' ? 'switchOptionTarget-tallscreen' : 'switchOptionSecondary-tallscreen'">
                    School
                </div>
            </div>

            <v-timeline v-if="$vuetify.breakpoint.width >= mobileViewpointWidthTipover" align="start" class="py-15">
                <v-timeline-item v-for="(exp, i) in (experienceShown == 'W' ? workExperiences : schoolExperiences)" :key="i" size="small">
                    <template v-slot:icon>
                        <router-link :to="exp.pageRoute" class="experienceCardRoute">
                            <img class="timelineIconImage" :src=exp.iconPath />
                        </router-link>
                    </template>
                    <template v-slot:opposite>
                        <div class="timelineText-widescreen pt-1 headline font-weight-bold">
                            {{ exp.timeline }}
                        </div>
                    </template>
                    <div class="timelineCards-widescreen">
                        <router-link :to="exp.pageRoute" class="experienceCardRoute">
                            <v-card elevation="15" outlined shaped>
                                <v-card-text>
                                    <div>
                                        {{ exp.company }}
                                    </div>
                                    <div class="text-h5 text--primary">
                                        <strong> {{ exp.title }} </strong>
                                    </div>
                                    <div>
                                        {{ exp.location }}
                                    </div>
                                    <div class="text--primary" style="white-space: pre-line;">
                                        {{ exp.description }}
                                    </div>
                                </v-card-text>
                            </v-card>
                        </router-link>
                        <v-card v-if="experienceShown == 'W' && (exp.company == 'Rensslear Polytechnic Institute')" elevation="15" outlined shaped class="mt-5">
                            <v-card-text>
                                <div>
                                    {{ exp.company }}
                                </div>
                                <div class="text-h5 text--primary">
                                    <strong> Resident Assistant </strong>
                                </div>
                                <p>
                                    {{ exp.location }}
                                </p>
                                <div class="text--primary">
                                    - Fostered the development of relationships among hundreds of residents <br>
                                    - Planned and implemented programs to assist international and transfer students in transitioning to campus <br>
                                    - Counseled and advised students on academic and personal questions and concerns <br>
                                    - Developed and conducted programs on diversity, chemical abuse, personal development, relationships, and academic performance <br>
                                    - Managed administrative duties: budgeting, maintenance requests, incident reports, and room transfers <br>
                                </div>
                            </v-card-text>
                        </v-card>
                    </div>
                </v-timeline-item>
            </v-timeline>

            <!-- TALL IMPLEMENTATION BELOW -->
            <v-timeline v-else side="end" dense align="start" class="py-15">
                <v-timeline-item v-for="(exp, i) in (experienceShown == 'W' ? workExperiences : schoolExperiences)" :key="i" size="small">
                    <template v-slot:icon>
                        <router-link :to="exp.pageRoute" class="experienceCardRoute">
                            <img class="timelineIconImage" :src=exp.iconPath />
                        </router-link>
                    </template>
                    <div class="timelineCards-widescreen">
                        <router-link :to="exp.pageRoute" class="experienceCardRoute">
                            <v-card elevation="15" outlined shaped>
                                <v-card-text>
                                    <div>
                                        {{ exp.company }}
                                    </div>
                                    <div class="text-h5 text--primary">
                                        <strong> {{ exp.title }} </strong>
                                    </div>
                                    <div>
                                        {{ exp.timeline }}
                                    </div>
                                    <div class="text--primary" style="white-space: pre-line;">
                                        {{ exp.description }}
                                    </div>
                                </v-card-text>
                            </v-card>
                        </router-link>
                        <v-card v-if="experienceShown == 'W' && (exp.company == 'Rensslear Polytechnic Institute')" elevation="15" outlined shaped class="mt-5">
                            <v-card-text>
                                <div>
                                    {{ exp.company }}
                                </div>
                                <div class="text-h5 text--primary">
                                    <strong> Resident Assistant </strong>
                                </div>
                                <p>
                                    {{ exp.timeline }}
                                </p>
                                <div class="text--primary">
                                    - Fostered the development of relationships among hundreds of residents <br>
                                    - Planned and implemented programs to assist international and transfer students in transitioning to campus <br>
                                    - Counseled and advised students on academic and personal questions and concerns <br>
                                    - Developed and conducted programs on diversity, chemical abuse, personal development, relationships, and academic performance <br>
                                    - Managed administrative duties: budgeting, maintenance requests, incident reports, and room transfers <br>
                                </div>
                            </v-card-text>
                        </v-card>
                    </div>
                </v-timeline-item>
            </v-timeline>

        </div>
    </div>
</template>

<!-- https://codesandbox.io/s/stack-70157850-3cblq?file=/src/components/CustomExample.vue -->

<script>
    export default {
        data () {
            return{
                mobileViewpointWidthTipover: 850,
                experienceShown: 'W', // W for work, S for school
                experienceToggle: (this.experienceShown == 'S'),
                workExperiences: [
                    {
                        timeline: 'June - August 2023',
                        title: 'Software Development Engineer Intern',
                        company: 'Amazon Web Services',
                        location: 'Bellevue, WA',
                        description: 'Experiences will be added after internship ends...',
                        iconPath: '/experience_timeline_icons/AWS.png',
                        pageRoute: '/experience/AWS',
                    },
                    {
                        timeline: 'August 2022 - May 2023',
                        title: 'Help Desk Consultant',
                        company: 'Rensslear Polytechnic Institute',
                        location: 'Troy, NY',
                        description: '- Provided hardware and software support for both faculty, staff, and students \n - Coordinated computer repairs with Rensselaer\'s computer repair shop through Zendesk\'s support module \n - Managed user accounts, printers, and workstations through Microsoft Active Directory',
                        iconPath: '/experience_timeline_icons/RPI.png',
                        pageRoute: '/experience/HelpDesk',
                    },
                    {
                        timeline: 'January - August 2022',
                        title: 'Software Engineer Co-Op',
                        company: 'Huntington Ingalls Industries',
                        location: 'Syracuse, NY',
                        description: '- Engineered a comprehensive algorithm incorporating color, proximity, and Time of Flight LIDAR sensors and utilized embedded microcontrollers to integrate autonomous driving functionality for off-roading vehicles \n - Designed, deployed, and documented a full-stack application utilizing Microsoft Power Apps, Power Automate, Power Fx and SharePoint to streamline the shipping and tracking processes for the Product Management Team \n - Implemented and fully documented EZ Office’s Lab-Asset Tracking Software to monitor product calibration and expiration dates, increasing office productivity by 35% and improving overall office and lab organization \n - Deployed an NGINX Web Server to visualize and control Radio Frequency Chamber equipment remotely \n - Developed C++ and Python scripts to automate Vertical Launch System sequences and dissect UCEU log files',
                        iconPath: '/experience_timeline_icons/HII.png',
                        pageRoute: 'experience/HII',
                    },
                    {
                        timeline: 'May 2021 - January 2022',
                        title: 'Help Desk Consultant',
                        company: 'Rensslear Polytechnic Institute',
                        location: 'Troy, NY',
                        description: '- Provided hardware and software support for both faculty, staff, and students \n - Coordinated computer repairs with Rensselaer\'s computer repair shop through Zendesk\'s support module \n - Managed user accounts, printers, and workstations through Microsoft Active Directory',
                        iconPath: '/experience_timeline_icons/RPI.png',
                        pageRoute: 'experience/HelpDesk',
                    },
                ],
                schoolExperiences: [
                    {
                        timeline: 'January 2023 - Present',
                        title: 'Rensselaer Polytechnic Institute',
                        company: 'M.S, Artificial Intelligence & Machine Learning',
                        location: 'Troy, NY',
                        description: `4.0 GPA \n Participated in the Algorand Foundation\'s MEGA-ACE Hackathon \n Graduate Research Project`,
                        iconPath: '/experience_timeline_icons/RPI.png',
                        pageRoute: 'experience/RPI',
                    },
                    {
                        timeline: 'August 2019 - May 2023',
                        title: 'Rensselaer Polytechnic Institute',
                        company: 'B.S, Computer Science',
                        location: 'Troy, NY',
                        description: '3.6 GPA \n Dean\'s Honor List (x4) \n 4 Undergraduate Research Projects \n 1 Independent Research Project',
                        iconPath: '/experience_timeline_icons/RPI.png',
                        pageRoute: 'experience/RPI',
                    },
                    {
                        timeline: 'September 2015 - June 2019',
                        title: 'Poly Prep Country Day School',
                        company: '',
                        location: 'Brooklyn, NY',
                        description: '3.8 GPA Unweighted, 4.4 Weighted \n Dean\'s List \n Varsity Baseball \n Varsity Swimming \n Concert Choir \n Blue Notes \n A Capella \n AP Scholar Award',
                        iconPath: '/experience_timeline_icons/POLY.png',
                        pageRoute: 'experience/POLY',
                    },
                    {
                        timeline: 'September 2012 - June 2015',
                        title: 'St. Ephrem\'s School',
                        company: '',
                        location: 'Brooklyn, NY',
                        description: 'I\'ll figure out what to put here eventually...',
                        iconPath: '/experience_timeline_icons/EPHREM.png',
                        pageRoute: '',
                    },
                ],
            }
        },
        methods: {
            toggleExperienceShown(){
                if (this.experienceShown == 'W')
                    this.experienceShown = 'S';
                else
                    this.experienceShown = 'W';
            }
        },
        head() {
            return {
                title: "Experience | AM"
            };
        }
    }
</script>

<style>
    .v-input--switch:not(.v-input--switch--flat):not(.v-input--switch--inset) .v-input--switch__thumb {
        color: cornflowerblue
    }
    .theme--dark.v-input--switch .v-input--switch__track {
        color: cornflowerblue
    }
    .theme--light.v-input--switch .v-input--switch__track {
        color: cornflowerblue
    }

    .theme--dark.v-timeline:before {
        background: cornflowerblue;
    }
    .theme--light.v-timeline:before {
        background: cornflowerblue;
    }

    .experienceCardRoute{
        text-decoration: none;
    }

    .experienceContainer{
        text-align: center;
        justify-content: center;
        align-items: center;
    }

    .experienceContents{
        margin-left: 5vw;
        margin-right: 5vw;
    }

    .experienceSwitchButtons{

    }
    
    .timelineIconImage{
        max-width: 4.25vw;
        min-width: 50px;
        padding-top: 0.5vw;
    }

    /* WIDE */

    .bigHeader-widescreen{
        font-size: 4.5vw;
        font-weight: 700;
        text-transform: uppercase;
        font-family: 'Montserrat', Arial, Helvetica, sans-serif;
    }

    .experienceToggleOption-widescreen{
        margin: 1vh 1vw;
        font-size: 2vw;
        font-weight: 700;
        font-family: 'Montserrat', Arial, Helvetica, sans-serif;
        transition: 0.3s;
        cursor: pointer;
    }

    .shownExperienceToggleContainer-widescreen{
        display: flex;
        text-transform: uppercase;
        border-bottom: 2px solid cornflowerblue;
        height: 5vw;
    }

    .switchOptionSecondary-widescreen{
        font-size: 1.25vw;
        color: gray;
    }

    .switchOptionTarget-widescreen{
        font-size: 2.75vw;
        color: #5086d6;
    }

    .timelineCards-widescreen{
        padding: 0 1.25vw;
    }

    .timelineText-widescreen{
        padding: 0 1.25vw;
    }

    /* TALL */

    .bigHeader-tallscreen{
        font-size: 6vw;
        font-weight: 700;
        text-transform: uppercase;
        font-family: 'Montserrat', Arial, Helvetica, sans-serif;
    }

    .experienceToggleOption-tallscreen{
        width: 50vw;
        font-size: 6vw;
        text-transform: uppercase;
        font-family: 'Montserrat', Arial, Helvetica, sans-serif;
        font-weight: 700;
        transition: 0.3s;
        cursor: pointer;
    }
    
    .shownExperienceToggleContainer-tallscreen{
        display: flex;
        height: 9vh;
        border-bottom: 3px solid cornflowerblue;
    }

    .switchOptionSecondary-tallscreen{
        font-size: 5vw;
        color: gray;
    }

    .switchOptionTarget-tallscreen{
        font-size: 9vw;
    }

</style>