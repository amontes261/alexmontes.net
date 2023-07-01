<template>
    <div class="text-center">
        <div class="allContainer">
            <v-card color="black" class="comingSoonCard">
                <div class="textContainer">
                    <div class="comingSoonHeader">
                        Coming Soon
                    </div>
                    <div class= "smallTextContainer">
                        <div> This webpage is still under development. </div>
                        <div class= "completionAndCreatedByText divSpacer"> Expected completion: Fall 2023 </div>
                        <div>
                            In the meantime, you can check out the&nbsp;
                            <a class= "repoLink" href="https://github.com/amontes261/mySite">repository</a>
                            &nbsp;for updates.
                        </div>
                        <div> Thanks for coming & see you soon!</div>
                        <div class= "completionAndCreatedByText divSpacer"> Created by Alex Montes </div>
                        </div>
                </div>
            </v-card>
        </div>
    </div>
</template>

<style>
    .allContainer {
        flex-direction: column;
        font-size: calc(10px + 1.75vmin);
        background-attachment: fixed;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .comingSoonCard {
        color: black;
    }

    .completionAndCreatedByText{
        font-size: calc(2px + 2vmin);
    }

    .comingSoonHeader {
        font-weight: 800;
        font-size: calc(60px + 5vmin);
    }

    .divSpacer{
        height: 5vh;
    }

    .repoLink{
        color:aqua;
        text-decoration: none;
    }

    .smallTextContainer{
        padding-top: 1em;
    }

    .textContainer{
        color: white;
        background-color: black;
        padding-left: 1.5em;
        padding-right: 1.5em;
        padding-top: 1em;
        padding-bottom: 1em;
    }
</style>