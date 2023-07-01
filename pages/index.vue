<template>
    <div class="allContainer">
        <div class="cardContainer">
            <div class="homeItems">
                <!-- <img class="avatar" width="150" src="/portrait.png" />


                    TEST
                -->
            </div>
        </div>






    </div>
</template>

<script>
  export default {
    head() {
        return {
            title: "Home"
        };
    }
  }
</script>

<style>
    .allContainer{
        height: 100vh;
    }

    .cardContainer{
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
    }

    .homeItems{
        display: flex;
        align-items: center;
    }

    .temp{
        /* for testing... */
        height: 110vh;
        color: red;
    }

    /* Coming Soon CSS Below */
    /*
    .allContainer {
        flex-direction: column;
        font-size: calc(10px + 1.75vmin);
        background-attachment: fixed;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    */

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