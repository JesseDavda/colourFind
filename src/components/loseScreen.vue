<style scoped>

    .screenContainer {
        width: 50%;
        height: 600px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;

        position: absolute;
        z-index: 10;

        background-color: #fff;
        border-radius: 5px;
        border: 2px solid #000;
        box-shadow: 1px 2px 15px #444;
    }

    .screenContainer > h1 {
        font-weight: 300;
        font-size: 60px;
    }

    #winIcon {
        font-size: 150px;
        color: #c23616;
        margin-bottom: 40px;
    }

    #winningColour {
        width: 30%;
        height: 100px;

        display: flex;
        align-items: center;
        justify-content: center;

        border-radius: 10px;
        box-shadow: 1px 2px 15px #444;
    }

</style>

<template>
    <div class="screenContainer">
        <h1>WRONG!</h1>
        <span class="fas fa-window-close" id="winIcon"></span>
        <div id="winningColour" v-bind:style="{ backgroundColor: winningColour }"><p>{{winningColour.toUpperCase()}}</p></div>
    </div>
</template>

<script>
    export default {
        name: 'winScreen',
        props: {
            winningColour: String
        }
    }
</script>
