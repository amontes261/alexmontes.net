<template>
    <div class="text-center">
        <div class="allContainer">
            <div class="textContainer">
                <div class="headerContainer">
                    <div class="almostThereHeader">
                        Almost There.
                    </div>
                </div>
                <div class= "smallTextContainer">
                    <div>
                        This portfolio is still under development. Check out the
                        <a class="repoLink" href="https://github.com/amontes261/mySite" target="_blank">repository</a>
                        for updates.
                    </div>
                    <div class="pt-4 completionText divSpacer"> Expected completion: Fall 2024 </div>
                </div>
                <img class="pt-7" width="75" src="/logo_darkMode.png" />
            </div>
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
        height: 100vh;
    }

    .almostThereHeader {
        font-weight: 800;
        font-size: calc(60px + 5vmin);
    }

    .completionText{
        font-size: calc(2px + 1.5vmin);
    }

    .divSpacer{
        height: 5vh;
    }

    .headerContainer{
        
    }

    .repoLink{
        color:aqua;
        text-decoration: none;
    }

    .smallTextContainer{
        font-size: calc(15px + 1.5vmin);
        padding-top: 0.25em;
    }

    .textContainer{
        color: white;
        padding-left: 1.5em;
        padding-right: 1.5em;
        padding-top: 1em;
        padding-bottom: 1em;
    }
</style>